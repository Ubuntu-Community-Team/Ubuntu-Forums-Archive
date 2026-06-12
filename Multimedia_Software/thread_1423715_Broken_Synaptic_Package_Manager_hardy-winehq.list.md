---
title: "Broken Synaptic Package Manager: hardy-winehq.list"
date: 2010-03-07
forum: Multimedia Software
---

### Post by Enzis on 2010-03-07
Hi guys! I'm a newby of Linux as of about a week ago. Been trying vigorously to make things work, especially wine, for windows games I don't want to give up. Here's my issue:

I was trying to install NVIDIA proprietary drivers and it gave me an error for lack of permission. A forum led me to the attempt of using Synaptic Package Manager, which I can't open because it loads with an error (error message below.)

E: Type '--2010-03-06' is not known on line 1 in source list /etc/apt/sources.list.d/hardy-winehq.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I've messed with wine quite thoroughly with the mass troubleshooting the past week or so and assume it's got something to do with that (though it does seem to be installed right and working right.) Here's my system specs if it helps (I admit to not understanding what most of it means):

Unbunto 9.10 (karmic)
GNOME 2.28.1
Kernel Lnux 2.6.31-19-generic
(I'm using Zorin OS, but that should only effect the GUI and not any installations, so I assume.)

2G RAM, AMD Athlon 64 X2
Not sure how to check my specific video card, but will find out if necessary. Hardware drivers tells me to install either of:
NVIDIA accelerated graphics driver 173
NVIDIA accelerated graphics driver 185 (recommended)

Thx bunches in advance for any support.

---

### Post by hansdown on 2010-03-07
Welcome to the forum Enzis.

Have you considered doing a dual boot?

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Enzis on 2010-03-07
I've heard of doing a duel boot. Have only used linux for a week tho and don't want to give up so soon. I rly want to ge this thing figured out, and synaptic package looks like something I may need in the future.

Otherwise, thx for taking the time to respond, especially as quickly as u did

---

### Post by hansdown on 2010-03-07
> **Enzis said:**
> I've heard of doing a duel boot. Have only used linux for a week tho and don't want to give up so soon. I rly want to ge this thing figured out, and synaptic package looks like something I may need in the future.

Otherwise, thx for taking the time to respond, especially as quickly as u did

It's just, that Wine does have it's own problems, that a dual install doesn't.

---

### Post by karthick ayyapillai on 2010-03-07
> **Enzis said:**
> Hi guys! I'm a newby of Linux as of about a week ago. Been trying vigorously to make things work, especially wine, for windows games I don't want to give up. Here's my issue:

I was trying to install NVIDIA proprietary drivers and it gave me an error for lack of permission. A forum led me to the attempt of using Synaptic Package Manager, which I can't open because it loads with an error (error message below.)

E: Type '--2010-03-06' is not known on line 1 in source list /etc/apt/sources.list.d/hardy-winehq.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I've messed with wine quite thoroughly with the mass troubleshooting the past week or so and assume it's got something to do with that (though it does seem to be installed right and working right.) Here's my system specs if it helps (I admit to not understanding what most of it means):

Unbunto 9.10 (karmic)
GNOME 2.28.1
Kernel Lnux 2.6.31-19-generic
(I'm using Zorin OS, but that should only effect the GUI and not any installations, so I assume.)

2G RAM, AMD Athlon 64 X2
Not sure how to check my specific video card, but will find out if necessary. Hardware drivers tells me to install either of:
NVIDIA accelerated graphics driver 173
NVIDIA accelerated graphics driver 185 (recommended)

Thx bunches in advance for any support.

Hi 
type in the terminal 
lspci you will get to know the drivers and one more thing  go to the software repository and in the third party software add nvidia graphics card to the list.
one more thing just un install all the things you have done for getting wine working and restart the computer first then add the graphics card to the third party software list get updates again restart and finally install your wine using the terminal
sudo apt-get update && sudo apt-get install wine
this might help you

---

