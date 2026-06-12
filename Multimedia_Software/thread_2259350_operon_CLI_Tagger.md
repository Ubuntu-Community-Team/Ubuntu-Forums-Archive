---
title: "operon CLI Tagger"
date: 2015-01-03
forum: Multimedia Software
---

### Post by Yellow Pasque on 2015-01-03
operon is the command-line counterpart to the exfalso tagger GUI. I can't believe I just discovered it now, since it made life a lot easier. I don't see any threads about it either

I was transcoding some .flac files to musepack SV8 for use on an mp3 player. (Supposedly, musepack gives similar quality/filesize to vorbis and takes less battery power to decode.) The 'mpcenc' encoder is easy and flexible, but not smart enough to create an APEv2 tag from the flac metadata without manually using the metaflac command.  However, operon made it easy:

```
#!/bin/sh

mpcenc --quality 6.00 "$1"
outputfilename=`echo $1 | sed -e 's/^\(.*\)\.flac$/\1\.mpc/g'`
operon copy "$1" "$outputfilename"
```


I'll probably use operon to get rid of genre tags (I don't find them useful) and find .flac's in my collection that may still have unwanted ID3 tags on them and garbage metadata. Is anyone else using this utliity to do some neat things in scripts?

---

