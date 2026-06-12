---
title: "I just want to watch a DVD..."
date: 2006-02-18
forum: Multimedia &amp; Video
---

### Post by makoto149 on 2006-02-18
I've been running Ubuntu Breezy for about 3 weeks, and I LOVE it! But I can't figure out how to watch a DVD. I installed libdvdcss-whatever, and w32codecs, and every media player I could find in a google search, but to no avail.

I just want to watch a DVD. Can someone help me?

I am running an HP Pavilion dv4000 series notebook. Thanks!!

---

### Post by alfonz on 2006-02-18
do you have VLC installed?

if not do:

```
sudo apt-get install vlc libdvdcss2
```

this is what I use to watch DVD's and video files in general, but others might sugest mplayer. It wont hurt to install it anyways ;)

---

### Post by makoto149 on 2006-02-18
That got me further. Now when I open Totem, instead of saying "Can't read title information from DVD" it says "There were no decoders found to handle the stream, you might need to install the corresponding plugins"

Any ideas?

Please, somebody help me!!!

Thanks!!!!

---

### Post by Randomskk on 2006-02-18
Installing Ogle and then ogle-gui worked for me...
Try VLC and mplayer, too...

You definitely need libdvdcss2, I think there is a script on your computer someplace that installs all the needed files for you.

---

### Post by makoto149 on 2006-02-18
I appreciate the replies, but I have installed ALL of the stuff mentioned. libdvdcss2 (to which I alluded in my original post, well, sort of).

I have installed ogle, and when I run it from the menu, it just sort of "goes away." When I run it from the command line, I get:

WARNING[dvd_gui]: add_keybinding(): No such action: 'SaveScreenshot'
WARNING[dvd_gui]: add_keybinding(): No such action: 'SaveScreenshotWithSPU'
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Using libdvdcss version 1.2.9 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000377
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000044b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000004cf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000004e3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x0000128b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000012fc
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x000022a5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00002316
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00002e1d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00002e8e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00029fd9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00043fa8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x0032ae1e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0032ae8f
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_1.VOB (0x0032ae8f)!!
libdvdread: Elapsed time 4
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0034a877
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0034a8e8
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 4
WARNING[ogle_mpeg_ps]: dvdreadblocks only got 1, wanted 7
FATAL[ogle_mpeg_ps]: dvdreadblocks failed

I was hoping there was a DVD player for Ubuntu that just worked out of the box, but I haven't had any luck so far...

Thanks again for any help!

---

### Post by Lord Illidan on 2006-02-18
Xine also works for dvds.

---

### Post by niviche on 2006-02-18
I guess you have tried this already, but what about Totem-xine, or, on KDE, Kaffeine (with xine)?

---

### Post by makoto149 on 2006-02-18
I installed Kaffeine and that didn't help.

I just want to play a DVD.

---

### Post by yootje on 2006-02-18
Yeah, but did you try VLC?

---

### Post by makoto149 on 2006-02-18
Yes, I tried that. To no avail. I don't know how to communicate to you guys that I' stuck, but I'm stuck. I've tried everything in the doc.

I need help from an expert.

---

### Post by Dhar on 2006-04-07
I just tried  [this]("http://ubuntuforums.org/showpost.php?p=338836&postcount=2") (with symptoms like yours), and got it to work.  Give it a try!

-g.

---

