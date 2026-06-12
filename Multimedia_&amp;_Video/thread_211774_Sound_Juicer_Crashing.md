---
title: "Sound Juicer Crashing"
date: 2006-07-08
forum: Multimedia &amp; Video
---

### Post by dahli.llama on 2006-07-08
I have been tried to rip some CDs using Sound Juicer, but the program shuts down the instant I click the extract button.  It plays the CDs just fine, but will not extract them in any format.

I tried running it from the command line to see if I got any errors, and all I got was this:
```
Segmentation fault

```

I've tried uninstalling it and reinstalling, but it hasn't helped.

Any help would be appreciated.

---

### Post by stoneman on 2006-08-06
I had exactly the same problem with Sound Juicer 2.14.4.
Normally extracting works, but if I use old CDs that are not well readable, Sound Juicer crashes immediately with "Segmentation fault" after clicking "extract".

My settings:
- Eject when finished checked
- Folder: Custom folder under user-home
- Track Names:
  -- Fodler hirarchy: Album Title
  -- File name: Track Artist (sortable) - Track Title
- Strip special characters checked
- Output Format mp3

Profile "mp3":
- GStreamer Pipeline: audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 quality=0 bitrate=192

I installed the mp3-extension with the following hint:
[http://wiki.bsdforen.de/index.php/MP3_mit_Sound_Juicer_rippen%3F](http://wiki.bsdforen.de/index.php/MP3_mit_Sound_Juicer_rippen%3F)

Does anyone have a clue regarding this problem?

Thanks for help.

---

