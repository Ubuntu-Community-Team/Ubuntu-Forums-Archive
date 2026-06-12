---
title: "pulseaudio crash (not flash)"
date: 2009-01-13
forum: Multimedia Software
---

### Post by orbit on 2009-01-13
Pulseaudio crashes randomly.  It usually takes days or weeks, but eventually it fails.  I use audacious for my music player.  When pulseaudio goes down, audacious locks up.  I've seen a few discussions related to flash, but this is not caused by flash.

Killing puslseaudio with `pulseaudio -k' does not work.  It doesn't die.  After killing it in System Monitor I can restart it using the command `pulseaudio -D'.


Thanks

---

### Post by wolfen69 on 2009-01-13
remove it and use alsa. i had some minor hitches with pulse, and once i removed it, all is better.

---

### Post by Caseyjp on 2009-01-23
> **wolfen69 said:**
> remove it and use alsa. i had some minor hitches with pulse, and once i removed it, all is better.

That is NOT a solution, as the official distribution USES pulse audio as its default.  Also, telling a noob (not accusing the OP of this) to remove pulse audio without detail information can lead to a brick and bad feelings toward a distribution.  Think before you type. :idea:


I too am experiencing random pulse lockups which require restarting the daemon as well as the audio player (in this case VLC).

Using the "perfect pulse audio" setup information from here and pulse's site have not resolved these random crashes.

---

### Post by halovivek on 2009-01-23
> **Caseyjp said:**
> That is NOT a solution, as the official distribution USES pulse audio as its default.  Also, telling a noob (not accusing the OP of this) to remove pulse audio without detail information can lead to a brick and bad feelings toward a distribution.  Think before you type. :idea:



I had the same problem with pulse audio and i went to help thread and tried to solve but i could not. so i have removed the pulse audio and I have installed the ALSA from [this thread]("http://ubuntuforums.org/showthread.php?t=994256"). now i can able to do good.

---

### Post by Melcar on 2009-01-23
I have noticed pulseaudio crashes when watching several small videos or switching video/music players rapidly.  The way I fix it is simply by switching all my players and gstreamer properties to use ALSA.  There is no need to remove pulseaudio or kill the process.

---

### Post by markbuntu on 2009-01-23
I was having this problem when I first installed Hardy but have not had pulse crash on me in normal use in the last 6 months or so nor have I seen it in Intrepid.

If you are having this problem there are a few things you can do to help the devs figure out how to fix it. One thing is to start puseaudio from a terminal with pulseaudio -vvv and see what messages you get when it crashes. 

Another thing you can do is look in the pulse audio manager and keep an eye on the stream numbers in the Devices section. When that number reaches about 1100 pulse will crash. If an application is rapidly opening and closing streams then there is a problem with the application's alsa or pulseaudio plugin. This was the problem with flash 9. 

Other applications may have this problem but less severely. There is also the possibility of a memory leak or something in an alsa driver or in pulseaudio itself. 

Since this is not happening to everyone it is important that those who do experience it report it so your help in this would be appreciated. 

You can report your findings by filing a bug report at launchpad or at pulseaudio.org or to the application devs directly depending on what you find.

---

### Post by obzidian on 2009-03-17
Any update on this?

Having Exaile crash often when streaming music.

:(

---

