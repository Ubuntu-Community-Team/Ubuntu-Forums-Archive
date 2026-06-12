---
title: "Jaunty Freezes after fresh install with ATI Radeon HD2600xt"
date: 2009-05-03
forum: Multimedia Software
---

### Post by aksival on 2009-05-03
Howdy,

I've got two Dell computers that are running 9.04.  Both of these system have two 22" Dell LCD flat panels (all the same model) attached via dual DVI ATI video cards.

One of the systems is a few years old, and thus the video card is a few years old as well (it's an ATI Radeon X600).  This system was upgraded to 9.04 from 8.10 and works perfectly out of the box (including dual monitors via System > Preferences > Display).  No problems whatsoever here.

The other system is only about a year old and it has a much newer video card -- an ATI Radeon HD 2600xt. After a fresh 9.04 install, just about everything works fine (including dual monitors via System > Preferences > Display).  There are, however, a couple of problems:

1. I cannot enable Desktop Effects (I read somewhere that this model graphics card has been blacklisted because it's currently unstable, so I can wait for an update to fix this -- no worries).

2. After a short period of use (anywhere from 5 to 45 minutes) the entire system hangs.  The mouse cursor stops, music stops, everything freezes.  The system has to be cold-booted.

After a lot of research online, I've come up with a couple of theories:

1. There may be a memory leak in the new version of the X server

2. There is an issue with the new version of the open-source ATI graphics card drivers

Considering this, I tried to use the restricted ATI drivers by selecting System > Administration > Hardware Drivers.  This appeared to work fine, except that I couldn't enable the second monitor (System > Preferences > Display turned up a blank dialog and hung for a few minutes).

So here's where I am now:

I've done another fresh install of 9.04 and got the dual monitors working again using the open drivers, but the freezing continues to happen.  Is this a known bug in either the X server or the open ATI drivers?  If so, is there any indication of when fixes generally get pushed?

Thanks in advance :)

---

### Post by aksival on 2009-05-04
After reviewing more posts in the forum this morning, it looks like there is definitely an issue with ATI Radeon cards.

Since this makes the system completely unusable due to freezing (at least for a handful of users), I would imagine that this bug would be somewhat critical.

Can anyone verify that this bug has been reported and confirmed?  I can't seem to find the relevant report online.

Thanks :)

---

### Post by csab on 2009-05-04
Interestingly, with my system (Radeon HD 2600 Pro), the open soirce driver works perfectly, but I don't have good hardware graphics support, which makes programs like Google Earth almost unusable.

If I enable the restricted hardware driver (from the repository), the I get a very unstable system.

1. Switch user always freezes the computer. (I heard this is bug, and ATI won't fix it, but I can live without this feature.)

2. When I attempt to start a video playback in Totem, it freezes the computer about 50% of the time.

3. Occasionally the computer fails to wake up after sleep. I have to unplug it to restart.

I heard that the fglrx driver in the repository is beta, so I may try the one from the website.

---

### Post by aksival on 2009-05-04
> Interestingly, with my system (Radeon HD 2600 Pro), the open soirce driver works perfectly, but I don't have good hardware graphics support, which makes programs like Google Earth almost unusable.


Forgot to mention, with the open drivers 3d apps run like you said -- practically unusable.

---

### Post by BramWillemsen on 2009-05-21
I'm not sure if this is considered to be thread necromancy but this hit turned up nr 1 at google when i searched for freezing in jaunty with ati's

I have an ati x1950 PRO. I cannot use the flgrx drivers so im using the open source ones. In ubuntu 8.10 i had no freezes or anything while using the flgrx drivers. I reinstalled to ubuntu 9.04 and now they occasionally happen. 

3d games are especially terrible. I could run Nexuiz on 8.10 with no problem at all with the flgrx drivers. With the open source drivers in 9.04 it freezes within 10 seconds. Only rebooting helps then. There is a critical bug somewhere.

---

### Post by AugustinZ on 2009-05-21
Yes, I've this bug affects me as well - the system stops responding, the only thing I can do is to move the cursor. Reboot (hardware button) is the only way to "fix it".

---

### Post by Taila on 2009-05-21
My PC is a P4 2.4 GHz with 640Mb Ram and ATI Radeon 9200SE. I had been using Intrepid previously with no problems but when Jaunty came out I did fresh install of it. I realized the window effects were not working too well (no cube) also could not change virtual desktops.

The biggest problem though was the freezing desktop, nothing works until a hard boot. So now I have gone back to Intrepid and rolled a Ubuntu/Kubuntu system that works wonderfully.

---

### Post by BramWillemsen on 2009-05-21
it seems like only ati users experience this behaviour. I prefer to use jaunty because of its new features but the random lockups with the open source driver are driving me crazy.

---

### Post by Taila on 2009-05-25
I have been running Jaunty on the side as minor desktop and last Friday have noticed that it no longer freezes on my P4 2.4 GHz, ATI Radeon 9200SE with 640 MB Ram. So have retunred it to major operations. There has been no freezes now, the only thing still not working is the virtual desktops (cube) but then I do not use those much. Other desktop effects work such as wobbly windows work well and the system is fast in response. So I do not know whether some update has fixed something to do with my hardware.

I hope this is the same for others with similar and or better hardware now.

---

### Post by krychek on 2009-05-25
I'm also experiencing freezes when playing 3D games. (Urban Terror) I had no freezes with 8.10 and fglrx. I have Ati Mobility FireGL V5200. Sometimes I can play for 1 hour without freeze, sometimes it freezes after 5 minutes. I don't use compiz. Also the performance is poorer than it was in 8.10.

Is this reported on launchpad?

---

### Post by krychek on 2009-05-25
I just found this page:
[http://ossnotebook.blogspot.com/2009/05/ubuntu-jaunty-unstable-with-video-ati.html](http://ossnotebook.blogspot.com/2009/05/ubuntu-jaunty-unstable-with-video-ati.html)

It link to this bug:
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/368049](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/368049)

So this bug is supposed to be fixed in Karmic and Jaunty-proposed.

---

### Post by Taila on 2009-05-27
> **krychek said:**
> I just found this page:
[http://ossnotebook.blogspot.com/2009/05/ubuntu-jaunty-unstable-with-video-ati.html](http://ossnotebook.blogspot.com/2009/05/ubuntu-jaunty-unstable-with-video-ati.html)

It link to this bug:
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/368049](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/368049)

So this bug is supposed to be fixed in Karmic and Jaunty-proposed.

Well thanks krychek, I followed the link and did as advised there. My desktop has working virtual desktop now the only thing still not working is if I do cube but otherwise the mouse scrolling between desktops works smoothly. I am now at a happy state of being.

---

### Post by csab on 2009-06-03
My problem was fundamentally different, and I have a newr card so I don't think it would solve it for me. Anyone knows a solution to the "hard freeze on user switch" problem?

---

### Post by Primefalcon on 2009-06-12
I get the same issue freezing up, but I am unable to even move the mouse, for referenace I am using an x1300 so the proprietary drive is not an option.

it happens mostly when I seem to be installing software however which forces me to ma manually clear the dpkg cache, so I can reinstall the software properly

---

### Post by Gurqn on 2009-08-12
Guys problem fixied with ati's own driver package from website also follow to guide on wiki from here 

Jump the here 
**[SIZE=3]Installing the drivers manually[/SIZE]**

```
http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide
```

now 2600xt working perfect and smooth.

Tested.:popcorn:

---

### Post by ropsu on 2009-08-15
> **Gurqn said:**
> Guys problem fixied with ati's own driver package from website also follow to guide on wiki from here 

Unfortunately ATI's own drivers did not solve my problems with HD4870. Nor did [OSS Notebook -blog]("http://ossnotebook.blogspot.com/2009/05/ubuntu-jaunty-unstable-with-video-ati.html"), even after doing ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
``` (which updated *libgl1-mesa-dri* and *libgl1-mesa-glx* from 3.0 to 3.1).

My system is still freezing somewhere between xorg starting (login screen) and useing system some 25 minutes. Freezing includes  mouse and I'm just having two leds blinking in middle of keyboard showing system error or so. After login there are usually also a few short hangs, when I can move mouse but nothing else is workin (clock or system monitor is not beeing updated).

---

### Post by ropsu on 2009-08-15
> **ropsu said:**
> Unfortunately ATI's own drivers did not solve my problems with HD4870.

Tried this also, no luck: [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

Still freezing anywhere between graphical login showing up and using computer for a while. Usually it hangs totally at login or right after it.

---

