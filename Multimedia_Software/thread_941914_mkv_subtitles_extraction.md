---
title: "mkv subtitles extraction"
date: 2008-10-08
forum: Multimedia Software
---

### Post by oknos on 2008-10-08
Hi there, does anyone know a way to extract the subtitles from a mkv file?     
                      thanks :)

---

### Post by lovinglinux on 2008-10-08
mkvtoolnix has extraction options but I don't know the commands. I used mkvextractgui on Windows, but I'm not sure if there is a gui for linux.

---

### Post by oknos on 2008-10-09
I have the same problem with mkvtoolnix, i just hoped there was another way.

thanks a lot though.

---

### Post by oknos on 2008-10-09
Basically i want to encode from mkv to dvd with the subtitles of my choice, so if there is another way to do that without having to extract the mkv subtitles, i 'd be ok with that too.

i hope someone will come up with a way... :-|

---

### Post by shirilover on 2008-10-09
The method of extracting a track from a matroska container is:
```

mkvextract tracks "yourfile.mkv" tracknum:"yourfile.ext"

```
where, tracknum is the track number you wish to extract. This can be found using mkvinfo -g "yourfile.mkv".
the extension .ext should match the CODEC_ID of the track (avi for divx and xvid; 264 for avc; mp3,aac,ogg for audio; and ssa,***,srt for subtitles).
Example -- extracting a subtitle stream which is track 3:
```

mkvextract tracks "[SS-Eclipse] Hayate no Gotoku! - 06 (1280x720 h264) [3F717C30].mkv" 3:"Hayate - 06.***"

```

---

### Post by oknos on 2008-10-11
Thanks a lot! that works just fine :)

---

### Post by MrsUser on 2012-08-24
I know, this thread is old. But I had the same question. However, the extraction via terminal is a bit inconvenient. Then I was hoping that MKV extract gui exists for Linux as well, but no luck -- until lately I found an article about 'MKV Extractor GUI' for Linux:

[http://www.iloveubuntu.net/mkv-extractor-gui-471-extracts-edits-and-re-encapsulates-mkv-files](http://www.iloveubuntu.net/mkv-extractor-gui-471-extracts-edits-and-re-encapsulates-mkv-files)


Forum topic from the author (in French):
[http://forum.ubuntu-fr.org/viewtopic.php?id=293216](http://forum.ubuntu-fr.org/viewtopic.php?id=293216)


Documentation for the current version (in French):
[http://doc.ubuntu-fr.org/mkv_extractor_gui_v4](http://doc.ubuntu-fr.org/mkv_extractor_gui_v4)

If you can't read French, doesn't matter. The software's GUI is very intuitive, no French involved.

And you can simply install it via terminal:

> sudo add-apt-repository ppa:hizo/mkv-extractor-gui
sudo apt-get update
sudo apt-get install mkv-extractor-guiHope this is useful for other people, too.

---

### Post by sandyd on 2012-08-24
[B]Necromancing - thread closed

Please do not post in threads more than one year old.
[/B]

---

