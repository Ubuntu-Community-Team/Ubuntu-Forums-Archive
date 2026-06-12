---
title: "The pain of the HD2600...."
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by hiddendragon715 on 2007-11-07
I have read/ tried every different option for getting this card to work and I am either doing something wrong or this card just will not work in Linux. I have used the driver from ATI/AMD's website for my card and installed from the terminal and everything shows up (catalyst control center etc..)  I run aticonfig --initial  and aticonfig --overlay-type=Xv
I use sudo dpkg-reconfigure xserver-xorg I restart the system and everything says that the driver is installed and working fine but no 3D effects are usable and any time I scroll through a web page or document the screen "Scrolls" like when you have no driver installed in Windoz.

I have tried to use Envy since I figured I am a linux noob and I am likely performing the install wrong and I get the same results. I have tried to use the "restricted driver" that comes by default in the install of the OS through the restricted driver manager and I either get the same result or X crashes. 

I am wondering if any of you can tell me if I am missing a step that you can see from my explanation? I would like to hear from anyone who actually has this card installed "Radeon HD2600 pro" I have had success with X series of cards from ATI and linux but I have yet to get this card to work on any distro. If I cannot get this figured out soon I am considering buying a new card (likely one from Nvidia..) PLEASE HELP and THANK YOU for taking the time to read this. 

I forgot to mention I am currently running gutsy x86

---

### Post by hazelnutz18 on 2008-04-08
I've had the same issue in the past - its always because I don't enable the device in "Restricted Drivers Manager" BEFORE installing the drivers.

---

