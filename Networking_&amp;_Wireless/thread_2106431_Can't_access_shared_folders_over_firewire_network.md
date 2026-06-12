---
title: "Can't access shared folders over firewire network"
date: 2013-01-19
forum: Networking &amp; Wireless
---

### Post by N00b-un-2 on 2013-01-19
I just had to wipe my laptop's hard drive because I messed up the MBR pretty bad.  So before I wiped it I was looking for a fast way to transfer a couple hundred gigabytes of data from the laptop to the desktop.  Both the desktop and the laptop are attached to the same Wifi network but using Wireless G which was promising to take over a day, and that's if the connection didn't drop in the middle of transferring.  So instead, I fired up a live CD and then tried two methods, 1) share a network connection between the two using Firewire and 2) the same thing over ethernet.

The weird thing is, I was able to bring up the firewire connection by 

```
sudo modprobe firewire_net
sudo ifconfig firewire0 x.x.x.x up # had to give it a static address
ifconfig -a # to check the connection was indeed up
```

I plugged it into my other computer (a Mac).  I had also set up both AFP (netatalk) as well as Samba shares to move the files to and from.

With the firewire cable plugged in, I could see the shares but could not log on to use them.  With the ethernet cable connected, I would click on the share, it would ask for user name and password and then connect normally. 


So what is the problem with IP over Firewire?  I'm tempted to guess that it has something to do with DHCP, since the eth0 interface is managed dynamically by network manager while firewire is not.

Which brings me to my next question.  Is it possible to add Firewire to the gnome network manager?

---

### Post by N00b-un-2 on 2013-01-19
I figured it out.  The issue is with the subnet mask.  The Ubuntu laptop was set to 255.255**.255.0 **but the Mac was grabbing 255.255**.0.0**.  After that I was able to access file shares.  Fixed it by manually configuring the Firewire interface on the Mac.  Now I can see the shares, but I lost the ability to access the internet over firewire because of the lack of DHCP.

There has to be a way to accomplish this with DHCP on both machines, some way to manage firewire0 using gnome-network-manager.

---

