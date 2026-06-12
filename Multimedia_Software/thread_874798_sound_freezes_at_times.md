---
title: "sound freezes at times"
date: 2008-07-30
forum: Multimedia Software
---

### Post by jeenuv on 2008-07-30
Hi,

I use Ubuntu 8.04 LTS on a DELL Inspiron 6400. Ubuntu has detected my sound hardware and works fine most of the time. But at times, my lappy simply goes mute -- no sound comes out it. For example, Pidgin just stops producing sounds for incoming messages and media players like mplayer and Amarok refuse to playback any media -- not that it gives out error messages, but just freezes. For example, mplayer will give me the window, but no real-time playback. I'm able to seek but no continuous playback. Similarly Amarok just hangs, and I've to kill it.

The problem disappears if I log and out and log back in. Same is the case if I restart X (CTRL-ALT-BACKSPACE).

I don't know how to reproduce the problem. I suspect the sound driver. Is there any way by which I can re-initialize the sound driver, without restarting/logging out? Have anyone experiences this sort of problem before?

Please help.

Thanks
Jeenu

---

### Post by jeenuv on 2008-07-30
Oops! I just discovered that I had a flash movie being buffered when this problem occurred. I confirmed this by loading a page with a flash movie, and I could reproduce the problem. No other media worked until I closed the webpage.

Any idea whether this is a known problem, and how to work this around?

Thanks
Jeenu

---

### Post by GurktheBurp on 2008-07-30
I have exactly the same problem! Its really annoying, I can listen to music and aMSN plays sounds. Until I want to go on youtube, then i get no more sound from amarok and aMSN. I learn a lot of music from my computer on guitar, keyboard ect. It's honestly making me think of switching back to Windows. Anyone know how to fix this?

Thanks,
James.

---

### Post by jeenuv on 2008-08-02
Most of the times I'm not able to use get sound in my Ubuntu sytem, after I watch a Flash video. When I sat finished watching, I mean I closed the Firefox web page with the video. When I start Amarok, it complains that it couldn't initialize any sound drivers. And when I run mplayer, I get only the video.

When I searched the net on how to restart the sound driver, I learned that doing

sudo /etc/init.d/alsa-utils restart

will help. However, it didn't solve the problem.

Please can somebody tell me how to re-initialize the sound driver?

Thanks
Jeenu

---

### Post by garuhhh on 2008-08-02
same problem here!
running on Ubuntu 8.04, sound also stops responding when opening flash videos, gets back sound by restarting X (ctr+alt+backspace).

same problem after hibernate/suspend.. (resuming from hibernate or suspend).

using these won't work, since, afaik ubuntu 8.04 doesn't use ALSA as sound server, it uses PULSEAUDIO now.
```
sudo /etc/init.d/alsa-utils restart
```

don't have any idea how to restart sound server (pulseaudio).:(

---

### Post by garuhhh on 2008-08-08
i experienced the same with ubuntu8.04.. it's a problem with the default setup of pulseaudio...the new sound server of ubuntu. it doesn't use alsa, or atleast alsa runs via pulseaudio.. anyway, look at this howto in setting up pulseaudio.

[http://ubuntuforums.org/showthread.php?t=776739&highlight=ekiga+pulseaudio](http://ubuntuforums.org/showthread.php?t=776739&highlight=ekiga+pulseaudio)

in my case, my problems with missing sound after resume from hibernate/suspend was solved, as well as lost sound while playing flash video..

---

### Post by Efrain Valles on 2008-08-09
a workaround fr this issue is to close all apps that work with audio... specially firefox and then kill the processes of pulseaudio.

killall pulseaudio.

this will restart it. The issue has to do with the non free flash plugin. It still does not play nice with the new sound server (pulseaudio). 
this reminds me of the times when it didn't play nice with alsa...

Hope this helps

---

