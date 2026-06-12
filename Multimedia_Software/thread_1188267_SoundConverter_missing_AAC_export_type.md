---
title: "SoundConverter missing AAC export type"
date: 2009-06-15
forum: Multimedia Software
---

### Post by mabtifro2 on 2009-06-15
Im using the most recent version of SoundConverter (1.4.3) which says it exports the following file formats: WAV, FLAC, MP3, AAC, and Ogg Vorbis files.

However, only four of those options are available when I enter the options (WAV, MP3, Ogg and FLAC).

I need the AAC format to convert music to play in a Nintendo thing which only reads those files.

What should I do - why is it missing?

---

### Post by SuperSonic4 on 2009-06-15
Have you installed faac?

---

### Post by Bachstelze on 2009-06-15
[http://packages.ubuntu.com/jaunty/soundconverter](http://packages.ubuntu.com/jaunty/soundconverter)

I don't see anything about AAC here. Most likely, the version of SoundConverter that is in the Ubuntu repositories was compiled without AAC support, since it is not a free format.

---

### Post by mabtifro2 on 2009-06-15
supersonic: faac was not installed when i asked the question. i just installed it however through synaptic and still no dice.

hymn to life: i installed soundconverter through a deb package on their website, not through synaptic.

---

### Post by mc4man on 2009-06-15
the more current versions from the website do support aac. It's a gstreamer app so in addition to libfaac0 you'd probably need one of the various gstreamer plugins.
I don't use gstreamer apps much so can't say which one in particular, figure one or more of these
bad and bad multiverse
ugly and ugly multiverse
gstreamer- ffmpeg

Noting that for bad and  ugly the multiverse plugin doesn't replace the bad and ugly (install all 4

Or use soundkonverter which uses faac/faad directly for the backend

Edit:
a quick test is not that impressive, for a gui I'd use soundkonverter instead or better yet set up to use neroAacEnc

---

