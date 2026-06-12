---
title: "System Freeze While Playing Video"
date: 2011-01-06
forum: Multimedia Software
---

### Post by JCM_Pico on 2011-01-06
Hi there,

When I play some video file, like some series (.avi), my system often freezes, the image become static and the sound starts looping. Ctr+Alt+Del does nothing and the only way to shut the computer down and restart the system is by holding the power button down for a long time.
I've already searched the web for this problem but I find nothing.
I have a Asus UX-30 with an Intel  GMA X4500MHD

is there any way to solve this problem?

cheers

---

### Post by rinswind on 2011-01-09
I have almost the same problem. When video is playing after a while the system freezes. No sound no any response, nothing. It seems the problem is with the video drivers. In other thread the recommendation is to switch off the accelerated video rendering. For the default video player you can do that by running "gstreamer-properties" from the console and delecting the "X windowing system (no Xv)" video plugin. This however causes terrible video performance on my Nvidia 8800 GTS.

I run Ubintu 11.04 and the problems started after an update I did 2 days ago. Looking at the APT history there are no updates that seem to have caused the problem:

evolution-common:i386 (2.30.3-1ubuntu7.1, 2.30.3-1ubuntu7.2), 
libapparmor1:i386 (2.5.1-0ubuntu0.10.10.2, 2.5.1-0ubuntu0.10.10.3), 
libcupscgi1:i386 (1.4.4-6ubuntu2.2, 1.4.4-6ubuntu2.3), 
git-doc:i386 (1.7.1-1.1, 1.7.1-1.1ubuntu0.1), 
evolution:i386 (2.30.3-1ubuntu7.1, 2.30.3-1ubuntu7.2), 
python-aptdaemon-gtk:i386 (0.31+bzr506-0ubuntu4, 0.31+bzr506-0ubuntu5), 
python-aptdaemon:i386 (0.31+bzr506-0ubuntu4, 0.31+bzr506-0ubuntu5), 
git-gui:i386 (1.7.1-1.1, 1.7.1-1.1ubuntu0.1), 
libapparmor-perl:i386 (2.5.1-0ubuntu0.10.10.2, 2.5.1-0ubuntu0.10.10.3), 
ubuntu-sso-client:i386 (1.0.7-0ubuntu1, 1.0.8-0ubuntu1), 
libevview3:i386 (2.32.0-0ubuntu1, 2.32.0-0ubuntu1.1), 
cups-client:i386 (1.4.4-6ubuntu2.2, 1.4.4-6ubuntu2.3), 
evince-common:i386 (2.32.0-0ubuntu1, 2.32.0-0ubuntu1.1), 
libcupsmime1:i386 (1.4.4-6ubuntu2.2, 1.4.4-6ubuntu2.3), 
libsqlite3-0:i386 (3.7.2-1, 3.7.2-1ubuntu0.1), 
cups-ppdc:i386 (1.4.4-6ubuntu2.2, 1.4.4-6ubuntu2.3), 
libevolution:i386 (2.30.3-1ubuntu7.1, 2.30.3-1ubuntu7.2), 
libcupsppdc1:i386 (1.4.4-6ubuntu2.2, 1.4.4-6ubuntu2.3), 
cups-common:i386 (1.4.4-6ubuntu2.2, 1.4.4-6ubuntu2.3), 
libcups2:i386 (1.4.4-6ubuntu2.2, 1.4.4-6ubuntu2.3), 
git:i386 (1.7.1-1.1, 1.7.1-1.1ubuntu0.1), 
ifupdown:i386 (0.6.10ubuntu3, 0.6.10ubuntu3.1), 
dpkg:i386 (1.15.8.4ubuntu3, 1.15.8.4ubuntu3.1), 
aptdaemon:i386 (0.31+bzr506-0ubuntu4, 0.31+bzr506-0ubuntu5), 
cups:i386 (1.4.4-6ubuntu2.2, 1.4.4-6ubuntu2.3), 
evince:i386 (2.32.0-0ubuntu1, 2.32.0-0ubuntu1.1), 
libevdocument3:i386 (2.32.0-0ubuntu1, 2.32.0-0ubuntu1.1), 
libcupsdriver1:i386 (1.4.4-6ubuntu2.2, 1.4.4-6ubuntu2.3), 
evolution-plugins:i386 (2.30.3-1ubuntu7.1, 2.30.3-1ubuntu7.2), 
cups-bsd:i386 (1.4.4-6ubuntu2.2, 1.4.4-6ubuntu2.3), 
gitk:i386 (1.7.1-1.1, 1.7.1-1.1ubuntu0.1), 
apparmor:i386 (2.5.1-0ubuntu0.10.10.2, 2.5.1-0ubuntu0.10.10.3), 
libcupsimage2:i386 (1.4.4-6ubuntu2.2, 1.4.4-6ubuntu2.3), 
libpq5:i386 (8.4.5-0ubuntu10.10, 8.4.6-0ubuntu10.10), 
git-core:i386 (1.7.1-1.1, 1.7.1-1.1ubuntu0.1), 
gnome-system-tools:i386 (2.32.0-0ubuntu1, 2.32.0-0ubuntu1.1),
apparmor-utils:i386 (2.5.1-0ubuntu0.10.10.2, 2.5.1-0ubuntu0.10.10.3)

Anyway does anyone know if it is possible to revert this entire update?

---

### Post by rinswind on 2011-01-09
Okay I booted from an older kernel and this seems to have fixed the problem. The only minor issue I have is that the screensaver turns on during video playback but I can live with that. Here is the content of my /proc/version

Linux version 2.6.32-26-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #48-Ubuntu SMP Wed Nov 24 09:00:03 UTC 2010

---

### Post by wiggie on 2011-02-17
So you´re running kernel 2.6.32-26? That's the one I'm running and I'm getting the same problem.

I can move my mouse but clicking does nothing. Very strange.

It worked fine before, except for one problem: when I played a film, once in a while I would get full CPU usage for about 5 secs, at which time the video would freeze, I couldn't even get out of full screen mode, then it came back.

So I followed these instructions: [http://ubuntuforums.org/showpost.php?p=10342739&postcount=3](http://ubuntuforums.org/showpost.php?p=10342739&postcount=3)
where you edit the gstreamer properties to set the video to X Windows (No Xv). Ever since my system keeps freezing when video is displayed. It is really annyoing!

I changed it back, but it still does it.

---

### Post by no2498 on 2011-02-17
type htop in a terminal it tells you how to install it
after installed type ftop click enter
look for what ever is running and what its using memory or cpu
as you play a video


ftop also comes up in system tools
click q to stop it

---

### Post by rinswind on 2011-03-07
Hi,
In the end I discovered my machine freezes because the radiator on my chipset has detached and the machine overheated when I does intense computations like decoding video for example. Once I reattached the bloody thing everything went back to normal. 

Cheers,
Todor

---

