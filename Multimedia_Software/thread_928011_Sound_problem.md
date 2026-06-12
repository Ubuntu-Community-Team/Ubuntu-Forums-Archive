---
title: "Sound problem"
date: 2008-09-23
forum: Multimedia Software
---

### Post by yelserpdog on 2008-09-23
Hi all,

I've got a problem with my sound. If I play a music file (any type), watch a flash video online or a video file from my hard drive, the sound keeps locking up. It'll play fine then suddenly stop, buzz (the sound locked and repeated) then continue ok till the next time it does the same thing. 
During video playback the same thing happens but when it does the picture also freezes.
I've spent a long time searching for fixes and tried several guides on here to no avail.
I've done what was said on this thread

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

When I do as instructed in appendix B I get result A and according to that Pulse is configured fine. I've followed the instructions in appendix C and i'm still having the same problem. I use my laptop for 95% of what I do so this is ery frustrating. Can anyone help??
I've got a Dell Inspiron 1501 running 8.04 64bit
cheers
Yd

---

### Post by yelserpdog on 2008-09-23
Can anyone help?

---

### Post by markbuntu on 2008-09-23
Do you have libflashsupport installed. That will fix the problem with flash 9. If you are using flash 10, it will give you problems so you should remove it.

I have written an extensive sound troubleshooting guide you can try here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by yelserpdog on 2008-09-23
Would Flash 10 affect the playback on normal audio files though played through a media player?

---

### Post by markbuntu on 2008-09-23
No it should not. Since you are in 64 bit, you could be having problems with the 32bit libs that some applications use. There are some stickys at the top of the 64 bit forum here that you should look at.

---

### Post by yelserpdog on 2008-09-24
I've tried everything I can find now including what you've mentioned and I'm no further on. All video and audio files (in any player) offline and online get so far through then freeze, the sound gets locked for about 2 seconds then the file continues playing. There's nothing wrong with the hardware as I've had no problems in Windows. What can I do????

---

### Post by yelserpdog on 2008-09-24
if it helps in diagnosing, the files always freeze at 54 seconds!

---

### Post by markbuntu on 2008-09-24
Are you checking your email every minute or something?
Your resources could be getting squeezed. The fact that the applicaton continues to play after stalling points to it being suspended while something else is using the system. 

You can check this with the system monitor. It is in System/Administration. You can probably figure it out yourself.

---

### Post by yelserpdog on 2008-09-24
my mail's always on :)

I think you may be onto something. When idle, the cpu usage is around 17%. When I play an mp3 it goes up to about 25%. If I move the mouse around or open and close a few windows it jumps to around 70%. When the sound locks it jumps to around 95%.

---

### Post by yelserpdog on 2008-09-24
After pouring through posts about high cpu usage I found a suggestion about using the top command in the terminal. I did this and played an mp3 at the moment it locked the top item in the cpu% column had the command "b43". When i've done a search on this all I can find is references to the broadcom wirless (which I'm using).

---

### Post by yelserpdog on 2008-09-25
After faffing around all night with this i've found that if I turn off Wifi the my video and audio files play ok with no problems. Does anyone know why this is happening??

---

### Post by markbuntu on 2008-09-25
Is the wifi connected or is it always searching?

---

### Post by yelserpdog on 2008-09-25
Yeah, wifi is connected and working fine. I've found now that if I turn off the wifi and connect to the router using a cable I don't get the problem so I presume it must be something with the wireless card causing it. It's a  Broadcom Corporation BCM4311 802.11b/g WLAN. As I said before though I never used to get this problem in Windows so it can't be the card that's faulty. It's all very wierd.

---

### Post by markbuntu on 2008-09-25
It is probably the wifi driver taking cpu priority. There is a way to change the "nice" setting of programs but I am not familiar with how to do that.

---

