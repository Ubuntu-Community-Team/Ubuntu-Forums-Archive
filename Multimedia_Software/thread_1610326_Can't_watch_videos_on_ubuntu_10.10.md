---
title: "Can't watch videos on ubuntu 10.10"
date: 2010-10-31
forum: Multimedia Software
---

### Post by xarkitu on 2010-10-31
Hello!

I've got an eeepc 1101ha and have installed the latest ubuntu, 10.10, but i can't watch any videos!
Besides the original player, i have installed and tried to watch videos in VLC, SMPlayer and GNOME MPlayer but it has always some kind of error. In VLC I can hear the sound. On all others the file simply doesn't work.
I don't know what to do, help me please!

---

### Post by ajgreeny on 2010-10-31
What video file type or types will not play?

Have you installed the **ubuntu-restricted-extras** package?

---

### Post by xarkitu on 2010-10-31
Hi!

I've installed the package you wrote but it didn't work. The players say:

- Totem: The following packages are necessary and not found: XVID MPGEG-4 decoder.
- VLC: No suitable decoder module:VLC does not support the audio or video "mp4v". Unfortunately, there is nothing you can do.  
- SMplayer: MPlayer has finished unexpectedly. Exit code: 127 

All my files are .avi

---

### Post by ajgreeny on 2010-11-01
I am not sure if it will help, but try enabling the medibuntu repos and install w32codecs (or w64codecs, depending on your OS).

That packaqe may have some codecs missing from your system.

---

### Post by chrisito on 2011-02-01
Hi friends I have something intersting I have the same problem in UBUNTU 10.10 can hear the sound but CAN NOT see the video .. so I start loading all the extra restricted and vlc sugestions but the problem was not there.  If you can hear the video but cant see it; the answer is in the video card configuration or xserver if you have nvidia videocard the solution is simple move the contrast control to 50%, for some reason when ubuntu installs nvidia cards like mine( NVIDIA Gforce9500) it puts the VIDEO CONTRAST to 0% so no image can be seen when a video is played so for me the solution was to move in the xserver ( video settings CONTRAST to 50%) an also in TOTEM - edition - preferences move the contrast to 50%, the same in VLC - tools - preferences - show all- video- image properties color more than ONE 
this how I resolve the problem of no Video Image in UBUNTU 10.10 
HOPE IT WILL BE USE FULL

---

### Post by Christofferh on 2011-02-06
> **chrisito said:**
> Hi friends I have something intersting I have the same problem in UBUNTU 10.10 can hear the sound but CAN NOT see the video .. so I start loading all the extra restricted and vlc sugestions but the problem was not there.  If you can hear the video but cant see it; the answer is in the video card configuration or xserver if you have nvidia videocard the solution is simple move the contrast control to 50%, for some reason when ubuntu installs nvidia cards like mine( NVIDIA Gforce9500) it puts the VIDEO CONTRAST to 0% so no image can be seen when a video is played so for me the solution was to move in the xserver ( video settings CONTRAST to 50%) an also in TOTEM - edition - preferences move the contrast to 50%, the same in VLC - tools - preferences - show all- video- image properties color more than ONE 
this how I resolve the problem of no Video Image in UBUNTU 10.10 
HOPE IT WILL BE USE FULL

How did you find out about that? ...impressive. The contrast was good in nvidia-settings for me running with packages from[ppa:ubuntu-x-swat]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates") ([Launchpad team page]("https://launchpad.net/~ubuntu-x-swat")) and a GTX460 with dual monitors.

Though it was at 0% in Totem, after changing that back to 50% I can watch movies again. I didn't even have to change anything in VLC, it worked after changing the settings in Totem.

I haven't had time to dig into this but my guess is that the contrast setting is somekind of global setting for the graphic card that get some bad value from Totem first time you start Totem in 10.10. Just a wild guess.

---

### Post by malecka on 2012-03-30
Hello guys...
I'm having some problems with watching videos, not in browse, but in players. I wanted to watch movie, and the audio is going well but the video is not going smooth. And, before starting i have 1 second black screen, and it is going on the application...
Any help about this issue?

---

