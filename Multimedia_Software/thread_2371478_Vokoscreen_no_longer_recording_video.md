---
title: "Vokoscreen no longer recording video"
date: 2017-09-14
forum: Multimedia Software
---

### Post by ihayes on 2017-09-14
I have ubuntu 16.04 installed on three computers and Vokoscreen screen recorder on each one. Vokoscreen suddenly started recording 0 byte text files starting around Sept 12, 2017 instead of video files. Vokoscreen has been working fine for last six months and no recent changes to the systems that i know of. It's actually intermittent, sometimes correctly recording video, and sometimes 0 byte files. Vokoscreen version is 2.4.0 and I have it set to output .avi files.

The fact that this started happening on three different computers at the same time makes me thing this has to do with some type of update, but I don't know of any that occurred recently. Let me know if anyone has experienced this issue or know of the cause.

---

### Post by mc4man on 2017-09-15
Vokoscreen should have a couple of logs in ~/.config/vokoscreen. When you get a bad recording maybe go take a look, particularly in the ffmpeg log

---

### Post by ihayes on 2017-09-15
There are 3 files in ~/.confg/vokoscreen , they are:

ffmpeg-20170915-200020.log     -> partial contents at: [https://pastebin.com/twVMTex7](https://pastebin.com/twVMTex7)
vokoscreen.conf                       ->  only interesting thing here is:  Recorder=/usr/bin/ffmpeg
vokoscreen.log                         -> contents at: [https://pastebin.com/RmXFecC9](https://pastebin.com/RmXFecC9)

I tried below commands from another post:

sudo mv /usr/bin/ffmpeg /usr/bin/ffmpeg_backup
sudo ln -s /usr/bin/avconv /usr/bin/ffmpeg
-- this causes vokoscreen to crash, reboot computer
sudo mv /usr/bin/ffmpeg_backup /usr/bin/ffmpeg

This seems to guarantee vokoscreen will record correctly on first run, but on subsequent runs it goes back to recording 0 byte files.

I have an old computer with ubuntu 15.10 and it's unnaffected, the log looks like,

vokoscreen.log                 _> contents at: [https://pastebin.com/a9XaRfFG](https://pastebin.com/a9XaRfFG)

Based on this info, I think there was an automated update to either QT or ffmpeg around Sept 12 that is causing the issue. If I can't resolve it, I may try upgrading to 17.04.

---

### Post by mc4man on 2017-09-15
For starters open a terminal & run same command voko is using, see what happens. If it runs then make sure to use q in terminal to quit ffmpeg & save the file.
```
ffmpeg -f x11grab -framerate 25 -video_size 622x484 -i :0+47,339+nomouse -f alsa -i pulse  -pix_fmt yuv420p -c:v libx264 -preset veryfast -c:a libmp3lame  -q:v 1  /home/blade/Videos/whatever.avi
```

---

### Post by ihayes on 2017-09-17
Thanks for this advice mc4man. The command line command works every time on all computers. I tried forcing software updates on all my computers but that didn't help with the gui version. It works intermittently with the gui. Sometimes it will record, and sometimes it won't. However, it's easy to tell if it's recording as the counter will be moving in the gui. The times it doesn't record, the timer stays at 0. So it seems it's just an issue with the gui. I'm using gnome classic desktop on all computers, which might be part of the issue. 

I tried installing ubuntu 17.04 on a computer with gnome classic desktop, but vokoscreen is unstable in this configuration, so that's not an option.

---

### Post by mc4man on 2017-09-17
> **ihayes said:**
> Thanks for this advice mc4man. The command line command works every time on all computers. I tried forcing software updates on all my computers but that didn't help with the gui version. It works intermittently with the gui. Sometimes it will record, and sometimes it won't. However, it's easy to tell if it's recording as the counter will be moving in the gui. The times it doesn't record, the timer stays at 0. So it seems it's just an issue with the gui. I'm using gnome classic desktop on all computers, which might be part of the issue. 

I tried installing ubuntu 17.04 on a computer with gnome classic desktop, but vokoscreen is unstable in this configuration, so that's not an option.
For 16.04 if inclined I've included latest voko here, read page first.
[https://launchpad.net/~mc3man/+archive/ubuntu/xerus-media](https://launchpad.net/~mc3man/+archive/ubuntu/xerus-media)
If using & there is an old voko .config folder then delete it first..

---

### Post by ihayes on 2017-09-21
I tried the latest voko version which installs 2.5.5 Beta. However it suffers from the same intermittent recording issue in the gui. It also crashes on stop record. Tried installing ubuntu 17.10 but voko has the same issue. Running in Unity or Gnome classic doesn't change anything. Also trying going back to ubuntu 15.10, general update from old repositories works, but installing vokoscreen fails. 

Voko will usually record after a reboot for a few times, but then goes back to not recording. This intermittent behavior is tough to troubleshoot.

---

### Post by ihayes on 2017-09-29
Thought I would try vokoscreen on 17.10 Beta. The intermittent recording issue doesn't appear in this version. However, when I record some video, the recording is just a black screen. Audio recording works fine. Hopefully they will get this resolved before the official release as I don't know of a viable replacement for this software.

---

### Post by mc4man on 2017-09-29
Can't say I've been able to dupe your issues in any Ubuntu release inc. 17.10 but in regards to 17.10 try when logging into an xorg session if you've been using the ubuntu default of Wayless

---

### Post by ihayes on 2017-09-29
Works fine when choosing xorg on login, looks like wayland is default. Thanks for the tip.  Vokoscreen allows for mkv and mp4 format, and lib264 and mpeg codecs.Avi format is not an option. I think mp4 with mpeg codec will work for me. The other options also record successfully. The computer I'm testing on has a pretty weak video card and that's a possible reason wayland doesn't work. Will be upgrading to 17.10 when it comes out in October.

---

### Post by mc4man on 2017-09-29
Voko uses ffmpeg which doesn't support screen recording in wayland protocol. There is  a gnome recorder that does though probably lightly featured.

---

### Post by ihayes on 2017-10-04
Ok, good to know. Xorg will be fine for me.

---

