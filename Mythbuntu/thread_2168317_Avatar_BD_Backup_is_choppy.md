---
title: "Avatar BD Backup is choppy"
date: 2013-08-17
forum: Mythbuntu
---

### Post by diesel48 on 2013-08-17
I recently backed up my BD's using MakeMKV to play through my mythbox. I am able to play all of backups flawlessly except Avatar. It stutters. I should have more than enough power to play it. The machine is an i3, 4gb ram, SSD drive and the video card is a Nvidia GT610.  Any ideas? I have tried SMB and NFS off my NAS just to make sure it was not a bandwidth problem. When looking at TOP during playback the CPU percentages do not seem to high. The load average is 1.1 .80 and .44 . Individual process are low, less than 10%. Any ideas?

---

### Post by diesel48 on 2013-08-17
Forgot to say I am using 12.0.4.1 myth.25

---

### Post by diesel48 on 2013-08-19
Nothing? Is my hardware to slow? When playing from a small media player it plays fine.

---

### Post by papibe on 2013-08-19
Hi diesel48.

I'm not very familiar with Myth, but in order to reproduce 1080p video you need to:
[LIST]
[*]Have the proper driver installed. In this case the Nvidia proprietary driver.
[*]Have the proper libraries installed: libvdpau1.
[*]Make sure the video is encoded in one of the supported formats (basically h264, x264 or MPEG).
[*]Make sure that the player is both able to use VDPAU and is set to use it as an output (instead of XVideo and X11).
[/LIST]
In order to see if the library is install, you can run this:
```
apt-cache policy libvdpau1
```
Check the proper Myth documentation for the output setting.

Hope it helps.
Regards.

---

### Post by diesel48 on 2013-08-19
I do not think that is it. All of my other 1080p content plays without a hitch. I was assuming this had something to do with the high-bit rate. The Nvidia drivers are installed and working. The player is using VDPAU.

---

### Post by krisbee2000 on 2013-08-19
I know I had an issue playing an mp4 in mythtvfrontend - no issue in VLC... problem was the theme painter was set to auto - when I set to qt or opengl, the mp4 issue went away.

---

### Post by diesel48 on 2013-08-19
I will double check on that but I believe my machine is set to Open GL. It is an MKV file.

---

### Post by diesel48 on 2013-08-20
updated to mythtv .25 and the stuttering went away.

---

