---
title: "lame and ffmpeg remove writing library metadata"
date: 2011-07-28
forum: Multimedia Software
---

### Post by adismsc on 2011-07-28
Hi,
how can I remove metadata (writing library) from mp3 file? When I use lame I can remove encoding settings by switch, but I can't remove encoder information. Encoding with ffmpeg save additional metadata like encoding settings... I want to remove all of them. It is possible?

--EDIT--
Main problem is writing library information. Sometimes information is saved normally (LAME3.98.4), sometimes not (LAME3.98÷&#259;R&#262;umôL, LAME&#350;&#350;&#8217;...) and sometimes information is not saved. Is there any standard for it ?! :|. If this metadata is required - no problem but I want to save it in this form -> "LAME3.98.4"... Not this  "LAME3.98÷&#259;R&#262;umôL" and not this "LAME&#350;&#350;&#8217;" and no other... Only encoder/encoder version and nothing else. Please help.

---

### Post by andrew.46 on 2011-07-28
You should be able to delete most mp3 metadata from mp3 files (id3v1 and id3v2 tags) with id3v2 from the commandline. Something like following should work:

```
id3v2 --delete-all *[COLOR="Red"]my_file.mp3[/COLOR]*
```

Of course you will need to replace *[COLOR="Red"]my_file.mp3[/COLOR]* with the name of your own file. Hope this does the trick for you :).

---

### Post by adismsc on 2011-07-28
It doesn't work :( I think it's not id3 tag.

after your command:

```
General
Complete name                    : test.MP3
Format                           : MPEG Audio
File size                        : 469 KiB
Duration                         : 30s 40ms
Overall bit rate                 : 128 Kbps
Writing library                  : LAME3.98.4

Audio
Format                           : MPEG Audio
Format version                   : Version 1
Format profile                   : Layer 3
Mode                             : Joint stereo
Mode extension                   : MS Stereo
Duration                         : 30s 119ms
Bit rate mode                    : Constant
Bit rate                         : 128 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 44.1 KHz
Compression mode                 : Lossy
Stream size                      : 469 KiB (100%)
Writing library                  : LAME3.98.4

```

---

### Post by andrew.46 on 2011-07-28
Sorry that did not remove the 'Writing Library' section for you. Perhaps somebody cleverer than me can open an mp3 produced by Lame with a hexeditor and see where that tag actually sits?

---

### Post by adismsc on 2011-07-28
Ok, anyway thanks for the reply :)

---

