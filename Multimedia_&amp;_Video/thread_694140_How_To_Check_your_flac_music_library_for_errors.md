---
title: "How To: Check your flac music library for errors"
date: 2008-02-11
forum: Multimedia &amp; Video
---

### Post by owennewo on 2008-02-11
Whilst it is rare for flac files to become corrupt, there are situations where this might happen.  e.g. dodgy hard drive, or copying files over a dodgy wifi network (the latter happened to me).

Fortunately as flac has an in built checksum it is straightforward to check whether a flac file is corrupt:

flac -t <flac file>

So to check a directory structure of flac files, something like this might work

cd ~/Music/
find ./ -name "*.flac" -type f -print0 | xargs -0 flac -st 2>output.log

This finds all flac files in the users Music directory (and all sub directories) and runs a verify on each file it finds.  Errors are put into the output.log file in the current directory.

If you prefer a more verbose output then change "flac -st" to "flac -t"

The script can take a while (~30 seconds per flac) as md5 checks take a while.

On a related note you can also perform a check when the file is encoded "flac -V" to ensure encoding is correct.  This takes the encoded flac and decodes back to the original file and checks whether the files are the same.

---

