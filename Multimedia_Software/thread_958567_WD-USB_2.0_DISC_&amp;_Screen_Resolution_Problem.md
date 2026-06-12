---
title: "WD-USB 2.0 DISC &amp; Screen Resolution Problem"
date: 2008-10-25
forum: Multimedia Software
---

### Post by w860124 on 2008-10-25
hi, are a newb at this so I kinda need some help..

Just installed Ubuntu a cuople of days ago and there is still a few things that are bothering me... 

#1) My portable USB 2.0 WD-MY BOOK 300GB hard drive with fat32 on isn't realy working as it should, everytime I boot up I have to run:
$ sudo rmmod ehci_hcd

and that makes the drive slow...
From what I've learned by searching the net, this is somekind of a  common problem... doeas anybody have a solution to this problem..?

#2) My computer is running on a integreated Intel i830M chipset video driver and a basic hercules screen with a screen resolution limit at 1024x768@60Hz
Somehow my computer has set the screen up to run un 1280x768@50Hz
this resolves in problems everytime I run a video or anykind of site containing a flash file.

When I try to change the screen resolution down to 1024x768, it goes crazy and starts to scramble across the screen... then I have to reboot the computer and when it boots back up it returns to the origionaly 1280x768 and the problem is still there... 

thankfull for any help I can get.. And remember that I'm still a beginner

\$ w860124

---

### Post by xc3RnbFO8P on 2008-10-25
In Terminal try: 
> gksu displayconfig-gtk
and choose Generic
and resolution that your monitor supports

---

### Post by w860124 on 2008-10-28
thanks that realy helped... still have problem with my disc though...

---

