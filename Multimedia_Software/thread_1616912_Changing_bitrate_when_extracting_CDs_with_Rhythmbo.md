---
title: "Changing bitrate when extracting CDs with Rhythmbox"
date: 2010-11-08
forum: Multimedia Software
---

### Post by Jonahtan on 2010-11-08
Hello,

does anyone know how to change the bitrate when extracting CDs with Rhythmbox?

I am able to extract to MP3 files with a bitrate of 128 kbps but would like to extract with VBR.

Edit>Preferences>Music>Preferred format>Edit>Profiles>CD Quality, MP3>Edit>GStreamer pipeline:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux

Does not "vbr-quality=6" mean that I am extracting with VBR? Nothing happens when I change the 6 to a lower number. The file properties still show a 128 kbps bitrate.

---

