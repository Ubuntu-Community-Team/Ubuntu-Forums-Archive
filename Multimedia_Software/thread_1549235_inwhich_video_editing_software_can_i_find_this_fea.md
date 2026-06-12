---
title: "inwhich video editing software can i find this feature?"
date: 2010-08-09
forum: Multimedia Software
---

### Post by Amgad elsaiegh on 2010-08-09
i have a couple of .avi clips in which the sound plays 2 seconds before the video ,so i need a software that can re-sync the sound correctly with the video with affecting the video/audio quality, what program can i use ? /what is the name of this feature in video editing programs ?

* i`m using Ubuntu 10.04
** i noted that the Multimedia & video forum have only threads about problems in playing videos & cards drivers problems , but i did not find anywhere else suitable to ask this question on the forums!

---

### Post by bryanl on 2010-08-09
I use avidemux for this. There is a checkbox and a value box on the main screen that you can use to enable audio shifting in a specified +/- number of milliseconds.

---

### Post by FakeOutdoorsman on 2010-08-09
Avidemux can re-sync your audio.  I'm not sure if it will re-encode though.

[list=1][*] Import your video.
[*] On the left, you'll see a checkbox titles "Shift".  You want the audio to start two-seconds later.  Start with a value of 2000 (2000 ms = 2 seconds).  Make sure Video and Audio are both set to "Copy".
[*] If it looks right export your video.[/list]

You can also use the command line (untested by me):
```
ffmpeg -i input.foo -vcodec copy -acodec copy -itsoffset 00:00:02.00 output.foo
```

You can use MPlayer to test how much you need to change the audio delay with the - and + keys. It will print out a display on the video showing you how much delay you've applied.

---

### Post by Amgad elsaiegh on 2010-08-09
thanks alot guys :)
that worked perfectly :D

---

