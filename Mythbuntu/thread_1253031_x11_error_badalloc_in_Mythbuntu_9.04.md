---
title: "x11 error badalloc in Mythbuntu 9.04"
date: 2009-08-29
forum: Mythbuntu
---

### Post by [Yatta] on 2009-08-29
In 8.10 I have no problem with playing video.... When i upgrade to 9.04 all my video players give me basically the same error

**X11 error: BadAlloc (insufficient resources for operation)**

Mind you this only happens when i use xv video mode in 9.04... if I switch to x11 it works fine but there is no video scaling (can't full screen video :-( )
I've been reading and it's been said that the above error is some driver of video card issue.

82865g integrated graphics device

In 8.10 I have installed 
xserver-xorg-video-intel 2.2.4.1
Kernel 2.6.27-14

In 9.04
xserver-xorg-video-intel 2:2.6.3
Kernel 2.6.28-11

Can someone advise me what I should do to get my video card working properly in 9.04 ???
x11 error badalloc insufficient resources

---

### Post by movieman on 2009-08-29
I'm guessing you're using integrated graphics and the graphics chip doesn't have enough RAM assigned to it. Is there a BIOS option to change that?

---

### Post by [Yatta] on 2009-08-29
Yea it is a intergrated card... but it worked fine in 8.04?!?!?!  I'll try it an see though.

---

### Post by [Yatta] on 2009-09-30
SOLVED!!
It seems like I needed to rollback to xserver-xorg-video-intel-2.4. I used the drivers from PPA... just in case I found this online 

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
Here is the gist of it though


Add the following lines to your /etc/apt/sources.list:

 deb [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main
 deb-src [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main

Import the GPG key:

 sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xce90d8983e731f79

Install the driver:

 $ sudo apt-get update
 $ sudo apt-get install xserver-xorg-video-intel-2.4

I may try the optimal setting from this [[COLOR="Red"][SIZE="4"]post[/SIZE][/COLOR]]("http://ubuntuforums.org/showthread.php?t=1130582")...

---

### Post by mlnease on 2009-10-25
> **'[Yatta] said:**
> SOLVED!!
It seems like I needed to rollback to xserver-xorg-video-intel-2.4. I used the drivers from PPA... just in case I found this online 

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
Here is the gist of it though


Add the following lines to your /etc/apt/sources.list:

 deb [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main
 deb-src [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main

Import the GPG key:

 sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xce90d8983e731f79

Install the driver:

 $ sudo apt-get update
 $ sudo apt-get install xserver-xorg-video-intel-2.4

I may try the optimal setting from this [[COLOR=Red][SIZE=4]post[/SIZE][/COLOR]]("http://ubuntuforums.org/showthread.php?t=1130582")...
Yatta,

THANK you.  I've tried half a dozen fixes today, this is the one that SOLVED my problem.

mike

---

### Post by [Yatta] on 2009-10-25
I'm glad it was able to help someone.... caused i looked ALL over the place for a solution.

---

### Post by mlnease on 2009-10-25
> **'[Yatta] said:**
> I'm glad it was able to help someone.... caused i looked ALL over the place for a solution.
So am I and so *did* I, Man--thanks a million again.  Just thought I should mention that I don't know from Mythbuntu--I'm just using plain old Jaunty, if any other Jaunty users are looking for a solution.

Cheers,

mike

---

