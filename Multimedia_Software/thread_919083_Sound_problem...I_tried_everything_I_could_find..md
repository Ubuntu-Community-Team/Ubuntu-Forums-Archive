---
title: "Sound problem...I tried everything I could find."
date: 2008-09-13
forum: Multimedia Software
---

### Post by TriggerIsHappy on 2008-09-13
I have tried all the previous posts that I can find on this sound problem.

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

 lspci -v
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Aspire 5920G
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

I have reinstalled Ubuntu 3 times trying to fix this and I think it is going to be a bug. I converted yesterday to linux and haven't had sound since the install. Like most of the others I have sound through the headphones but nothing else. In the 24 hours of working with Ubuntu I have grown very fond of it, I just need my sound back and my printer but I will post elsewhere for that. Someone please give me some advice or tell me how I report these bugs.

Thanks in advance,
Trigger

---

### Post by Bucky Ball on 2008-09-13
Not sure if it was you in a previous post but ...

Have you double clicked on your speaker icon to check nothing is muted in there? Know it sounds dumb but ...

---

### Post by Bucky Ball on 2008-09-13
That last post should have been:

Double click on speaker, go to edit in the window that opens then preferences. Make sure you have ticks in the appropriate places.

---

### Post by rrrlc on 2008-09-13
I'm glad you made this post. Same exact problem. Do you have problems playing youtube videos as well? I have all the pertinent firefox plugins to watch videos (flash, java, totem...), yet when I play a video, it stops at 2 seconds and there is no audio. Maybe these two problems are linked?

---

### Post by nightmarestreet on 2008-09-13
I've got the same problem. My flash is working though (but not with sound, obviously).

biff@laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0

---

### Post by TriggerIsHappy on 2008-09-13
No I have no problems playing videos from anywhere. Just the sound won't play. Bucky Ball... I checked the preferences and everything necessary is ticked. I've tried alsa drivers, new kernels, alsamixer is good. I can't find the problem. I thought I could have messed something up with the install but I've installed 3 times and nothing is different. From the other post seems like it may be an HDA Intel problem.

---

### Post by Bucky Ball on 2008-09-13
No, not install problem ... thinking ... :-k

You have ubuntu-restricted-extras loaded? 

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Aspire 5920G
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <**access denied**>
```I checked and mine shows what I have in bold here but is working fine. This is an onboard sound device, right?  It seems perhaps you don't have permissions to access this device, apparently a known glitch. Copy and paste this in a terminal and post the result here.

**ls -la /dev/snd**

If this returns an error 'No such file or directory' you will need to download the missing bits for the driver. Is the a red mark on your speaker icon also indicating you can't access?

---

### Post by TaskmasterC on 2008-09-13
[FONT="Century Gothic"][SIZE="2"][/SIZE][/FONT]I have the same problem trying to play videos off youtube. No sound. I have tried everything I can think of to no avail. However I can get system sound and my audio files play fine. I am wondering if it has something to do with firefox 3. If you have no sound at all, try changing you mixer. I had to mess with it for a couple of hours when I first installed ubuntu. Hope that helps a little.

---

### Post by TriggerIsHappy on 2008-09-14
eric@eric:~$ ls -la /dev/snd
total 0
drwxr-xr-x   2 root root      200 2008-09-14 12:23 .
drwxr-xr-x  14 root root    14160 2008-09-14 12:23 ..
crw-rw----+  1 root audio 116,  0 2008-09-14 12:23 controlC0
crw-rw----+  1 root audio 116,  4 2008-09-14 12:23 hwC0D0
crw-rw----+  1 root audio 116,  5 2008-09-14 12:23 hwC0D1
crw-rw----+  1 root audio 116, 24 2008-09-14 12:24 pcmC0D0c
crw-rw----+  1 root audio 116, 16 2008-09-14 14:50 pcmC0D0p
crw-rw----+  1 root audio 116, 28 2008-09-14 12:23 pcmC0D4c
crw-rw----+  1 root audio 116,  1 2008-09-14 12:23 seq
crw-rw----+  1 root audio 116, 33 2008-09-14 12:23 timer


I played with the mixer and nothing works.

---

### Post by Bucky Ball on 2008-09-14
[quote=TriggerIsHappy]drwxr-xr-x   2 root root      180 2008-09-15 02:48 .
drwxr-xr-x  13 root root    13800 2008-09-15 02:49 ..
crw-rw----+  1 root audio 116,  0 2008-09-15 02:48 controlC0
crw-rw----+  1 root audio 116,  4 2008-09-15 02:48 hwC0D0
crw-rw----+  1 root audio 116, 24 2008-09-15 02:48 pcmC0D0c
crw-rw----+  1 root audio 116, 16 2008-09-15 04:00 pcmC0D0p
crw-rw----+  1 root audio 116, 17 2008-09-15 02:48 pcmC0D1p
crw-rw----+  1 root audio 116,  1 2008-09-15 02:48 seq
crw-rw----+  1 root audio 116, 33 2008-09-15 02:48 timer[/quote]

There's mine and it looks identical to yours. But my machine is working fine! The only thing I can suggest, and the end of my knowledge for now on this one, is this page which might give you a few clues. Although dated, seems like the same 

[http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/](http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/)

Not the exact prob, but like I say, might give you a few ideas ...

---

### Post by TriggerIsHappy on 2008-09-14
Where's the page?

---

### Post by markbuntu on 2008-09-14
You can try my extensive troubleshooting and setup guide here:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by TriggerIsHappy on 2008-09-14
Thank you markbuntu. I am an idiot (again). THe option for  "Surround" on the alsamixer (when I first tried it) gave me a horrible wailing sound almost like a system beep. I didn't have any music playing when I was fooling with the mixer the first time and got the sound. I just now was following your guide and in the first paragragh figured out that me muting the "Surround" option killed my sound. So I adjusted the mic to get rid of the wail and am not listening to some wonderful music.


Thank you EVERYONE who posted...you all helped in some way or another.

Trigger

---

### Post by TriggerIsHappy on 2008-09-14
I've got one last question. Sound in everything but firefox. How can I fix this?

---

### Post by markbuntu on 2008-09-14
Read a little further down in my guide.

---

### Post by arch.stanton on 2008-09-14
my problem is that i cant run 2 programs using audio simultaneously

I'll be using amarok, and then a ill try to go on youtube but no audio will be playing. But if i shutdown amarok, then restart firefox, that same page works. but then ill start up amarok again and amarok wont be playing any sound.

Same goes for VLC and anything that has audio output.

---

### Post by markbuntu on 2008-09-14
You can also fix that with my guide.

---

### Post by Yellow Pasque on 2008-09-14
Ditch ALSA. Use OSS4 :)
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by TriggerIsHappy on 2008-09-14
Thanks again markbuntu. Everything works perfectly now.

---

