---
title: "Fuji FinePix A825 (A820) on Gutsy"
date: 2007-08-25
forum: Multimedia &amp; Video
---

### Post by Thumper723 on 2007-08-25
I am runnig Gutsy 64 bit, current running kernel 2.22.6-10

Compaq Presario V6310
1GB Ram

I try loading pics off of my camera using gThumb, and it does not see the camera. My camera sees the computer. 

lsusb is taking over a minute to execute, but is not returning anything.

master@master-laptop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 1199:0120 Sierra Wireless, Inc. 
Bus 001 Device 001: ID 0000:0000  
master@master-laptop:~$ 
master@master-laptop:~$ 

The sierra wireless is my Sprint Aircard. 

When I try to load it in gThumb, it takes almost a minute when I double click on the "no camera found" icon for the list of cameras to come up, and the "port" shows nothing. 

I think something is going on but it is bogging the computer down. 

I hate having to reboot into windows just to load pics off the camera. 

When I run lsusb without the camera attached, lsusb gives the same result, but instantly. 

I tried booting into the -8 & -9 kernels, no luck. Tried every USB port, including the one the aircard usually sits on. The aircard will work on all ports as long as I "killall pppd" and lsusb before running the connect script.

---

### Post by Thumper723 on 2007-08-26
Anybody got any ideas?

---

### Post by Thumper723 on 2007-08-27
I've tried getting the laptop to see it as a media drive. No luck there either.

---

### Post by MonctonJohn on 2007-12-26
This might be a little late but I'll reply anyway. The Fuji A820 does not operate as a USB Mass Storage device, it only operates in PTP mode. I actually contacted Fuji support over this  and that's what they told me. In order to see the camera you have to install libptp. I don't have enough experience with ubuntu and gnome since I use Slackware and KDE. I compiled and installed digiKam which supports ptp. Also I could not use the ptp commands as a regular user until I played with the udev rules so that the device node was created with rights for my user account. So that's pretty much it. If this post is still alive let me know if it works for you. :)

---

