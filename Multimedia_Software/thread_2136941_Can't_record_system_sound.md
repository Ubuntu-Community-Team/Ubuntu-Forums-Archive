---
title: "Can't record system sound"
date: 2013-04-19
forum: Multimedia Software
---

### Post by Stonecold1995 on 2013-04-19
I've never been able to record system sound...  For the life of me, I can't figure it out!  Nothing works, recordmydesktop, qx11grab, plain ffmpeg, nothing, not matter what settings I try to change.

Currently I'm trying to use just ffmpeg, so this is the command line:
```
/usr/bin/ffmpeg -xerror -loglevel info -f x11grab -framerate 60 -video_size 640x480 -i :0.0+2,23 -dcodec copy -f alsa -i default -sample_fmt s16 -audio_service_type ma -vol 256 -vcodec libx264 -tune touhou -acodec libvorbis -y /tmp/out.mkv
```

What am I doing wrong??  I've tried different "-audio_service_type"s (through qx11grab) but nothing works...  Some tutorial online told me to set alsamixer's settings so it looks like [this]("http://www.pictureshack.us/images/10122_alsamixer.png"), but that didn't seem to work either.

---

### Post by Stonecold1995 on 2013-04-25
bump

---

### Post by monkeybrain2012 on 2013-04-25
Install pulse audio volume control (sudo apt-get install pauvcontrol)  While recording open the pulse audio volume control to look  at the "recording" tab and see if it is recording, if not go to "configuration" tab and see if changing the devices makes a difference. There are other tabs and settings, you may need to experiment a bit, but make sure that you remember the original settings so you don't get lost.

Hope this helps.

---

### Post by Stonecold1995 on 2013-04-26
> **monkeybrain2012 said:**
> Install pulse audio volume control (sudo apt-get install pauvcontrol)  While recording open the pulse audio volume control to look  at the "recording" tab and see if it is recording, if not go to "configuration" tab and see if changing the devices makes a difference. There are other tabs and settings, you may need to experiment a bit, but make sure that you remember the original settings so you don't get lost.

Hope this helps.
```
alex@kubuntu:~$ sudo -k apt-get install pauvcontrol
[sudo] password for alex: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package pauvcontrol
```

---

### Post by monkeybrain2012 on 2013-04-26
Sorry, misspell. It should be pavucontrol

---

### Post by Stonecold1995 on 2013-04-29
The configuration tab didn't help, and the recording tab says the microphone is being recorded.  I want the *system sounds* to be recorded, not my microphone!

[IMG]http://i43.tinypic.com/35240zp.jpg[/IMG]

EDIT:
Even when I use Audio Stereo Duplex and set the mode to "Monitor of built-in audo analog stereo", it still won't record.
[img]http://i39.tinypic.com/346nz15.png[/img]

---

### Post by Stonecold1995 on 2013-04-29
Not sure if it matters but *none* of the sound bars in pavucontrol moved at all, not even in the "Playback" section when I had audio playing.

Could there be something wrong with my sound card?  I have followed several Youtube and written tutorials, all are very simple and mostly say the exact same thing, but when I try to record I get nothing.


Would it work if I were to plug an AUX cable into my AUX in and headphone slots so the computer records itself that way?

---

### Post by Stonecold1995 on 2013-05-02
bump

---

### Post by Stonecold1995 on 2013-05-28
bump

---

### Post by Stonecold1995 on 2013-06-09
bump

---

### Post by Stonecold1995 on 2013-06-09
Well, I got it to work.  The last post of [http://ubuntuforums.org/showthread.php?t=1619431](http://ubuntuforums.org/showthread.php?t=1619431) helped me.

---

### Post by Baldrick_NZ on 2013-06-10
In your pic above showing 'monitor of built in audio...' to the right there is a speaker with an 'x' through it. Clicking on it should unmute and give you the system sounds you're after.

Cheers.

---

