# fstunes

Hackathon project!

Extremely minimal command-line music library manager and media player
in the spirit of Git and UNIX. Uses a background process only for
playing media files, and does not index or cache. Uses abstractions
well-suited to the POSIX filesystem. Name origin: "filesystem" +
"tunes" = "fstunes".

## Command-line usage

This package provides one binary, `fstunes`. It has several available
subcommands:

* import: add media files to the database
* playlist: create or delete playlist
* insert: select song references using various filters, dereference,
  sort the results, and insert sequentially into a playlist;
  optionally also remove original references from playlists.
* remove: select song references using various filters and remove from
  playlists.
* edit: select song references using various filters, dereference,
  sort the results, write selected metadata to text file, open editor,
  write changes back and update pointers
* list: select song references using various filters, dereference,
  sort the results, and display selected metadata, optionally in
  summary format
* delete: remove media files from the database
* seek: jump to index in up-next playlist and optionally toggle
  play/pause

### import

    $ fstunes import <path>...

### playlist

    $ fstunes playlist (create | delete [-y, --yes]) NAME...

### insert

    $ fstunes insert
        [-m, --match FIELD=VALUE]              # literal match
        [-m, --match FIELD=VALUE1,VALUE2,...]  # set match
        [-m, --match FIELD=LOW-HIGH]           # range match
        [-m, --match FIELD=all]                # no filter
        [-s, --sort FIELD]
        [-r, --reverse FIELD]
        [-x, --shuffle FIELD]
        [-t, --transfer]
        [-y, --yes]
        [--before | --after]
        PLAYLIST INDEX

`FIELD` may be `artist`, `album`, `disk`, `track`, `song`, or `from`.
Special values for `from` are `library` and `queue`.

### remove

    $ fstunes remove
        [-m, --match FIELD=VALUE]              # literal match
        [-m, --match FIELD=VALUE1,VALUE2,...]  # set match
        [-m, --match FIELD=LOW-HIGH]           # range match
        [-m, --match FIELD=all]                # no filter
        [-y, --yes]

### edit

    $ fstunes edit
        [-m, --match FIELD=VALUE]              # literal match
        [-m, --match FIELD=VALUE1,VALUE2,...]  # set match
        [-m, --match FIELD=LOW-HIGH]           # range match
        [-m, --match FIELD=all]                # no filter
        [-s, --sort FIELD]
        [-r, --reverse FIELD]
        [-x, --shuffle FIELD]
        [-f, --fields FIELD1,FIELD2,...]
        [-e, --editor EDITOR]
        [-y, --yes]

### list

    $ fstunes list
        [-m, --match FIELD=VALUE]              # literal match
        [-m, --match FIELD=VALUE1,VALUE2,...]  # set match
        [-m, --match FIELD=LOW-HIGH]           # range match
        [-m, --match FIELD=all]                # no filter
        [-s, --sort FIELD]
        [-r, --reverse FIELD]
        [-x, --shuffle FIELD]
        [-f, --fields FIELD1,FIELD2,...]
        [-o, --overview]

### delete

    $ fstunes delete
        [-m, --match FIELD=VALUE]              # literal match
        [-m, --match FIELD=VALUE1,VALUE2,...]  # set match
        [-m, --match FIELD=LOW-HIGH]           # range match
        [-m, --match FIELD=all]                # no filter
        [-y, --yes]

### seek

    $ fstunes seek
        [-p, --play]
        [-P, --pause]
        [-a, --absolute]
        INDEX