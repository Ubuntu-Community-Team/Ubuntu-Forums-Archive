---
title: "firewire 1394 not working in jaunty 9.04"
date: 2009-08-20
forum: Multimedia Software
---

### Post by charonred on 2009-08-20
I recently installed 9.04 jaunty on friends PC; they're slowly getting used to it (lots of HELP phone calls). 

I was over there the other day and the system wouldn't capture anything via firewire because apparently it wasn't installed or not running or something - sorry can't remember exactly what it said, but I've just had a reminder phone call to fix it ... ?#-o

It all worked fine in Win XP, so what are the things I should be looking at on my next 'house call' to get it working in Ubuntu 9.04

---

### Post by ahickey on 2009-08-21
A couple of things to try.

Set the permission for raw1394 - see the following link: [http://ubuntuforums.org/showthread.php?t=966472]("http://ubuntuforums.org/showthread.php?t=966472")
This specifically mentions Kino as the capture app.

Or/and -  My external hard drive only works over firewire when the drive is plugged in and on at boot up. I haven't found a fix for this in Linux, I just accept it.
Try having the camera plugged in on boot up.



I hope this helps.

---

### Post by ianmillington on 2009-08-21
This is an issue that bugged me for some time. I understand that the author of the kernel firewire module has an issue about non-administrator access. Just to check it is the same thing, get your friend to run the video capture program (probably kino?) as root. I bet it's detected then.

You will find this link really, really helpful as a fix. Worked for me.

[https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)

Ian

---

### Post by bigtom2 on 2009-09-02
Quote:
sudo apt-get install kino  

Quote:
sudo apt-get install dvgrab  

Quote:
sudo apt-get install libraw1394-8  

Quote:
sudo apt-get install libraw1394-dev  

C) Start kino in terminal 
Quote:
sudo kino  

this sudo kino pulls up the gui 
make suer ths camera is running when you type sudo kino in
termianal mode.













> **ianmillington said:**
> This is an issue that bugged me for some time. I understand that the author of the kernel firewire module has an issue about non-administrator access. Just to check it is the same thing, get your friend to run the video capture program (probably kino?) as root. I bet it's detected then.


You will find this link really, really helpful as a fix. Worked for me.

[https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)

Ian

---

### Post by ianmillington on 2009-09-02
The problem with that approach is that Kino is running as root which has the potential to undermine the security of the system.

The link I posted provides a method for kino/kdenlive etc to access the firewire subsystem as an ordinary user.

---

