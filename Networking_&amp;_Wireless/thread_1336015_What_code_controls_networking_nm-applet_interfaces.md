---
title: "What code controls networking? nm-applet? interfaces?"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by konradpiskorz on 2009-11-24
My network needs are simple.  Network-manager makes them cumbersome.  I have two networks, my lab and home.  The lab is a static ip wired.  Home is DHCP wired or wireless.

Right now I have nm-applet set up with two profiles, home and lab.  Every day my laptop travels from my home to the lab and back.  Two times a day I have to go into 'manual configuration' from the icon. Unlock.  Choose the other profile.  Click load profile.  Wait.

Whenever I do this in the lab after doing this the network does not work period.  To make it work I have to type

sudo ifdown -a
sudo ifup -a
sudo ifdown -a
sudo ifup -a

Yes, I have to do it twice or else it wont work.  It also takes over 30 seconds for each command to run as it seems to search for my NFS drives which are at home, not in the lab, and waits for a timeout... theres three NFS drives and three timeouts!

Nothing like getting in ready to work and having to spend over two minutes at the terminal for internet access.  Not very convenient and very frustrating to do five-six days a week.



My question is, is nm-applet necessary?  That is, is nm-applet controlled by whatever the configuration in /etc/network/interfaces is?  Or does nm-applet run on top of whatever runs /etc/network/interfaces as a controller?

What I want to do is remove nm-applet as its a pain in the beehive and just change my config with a sh script or even by just commenting/uncommenting things in interfaces.  This would be significantly more convenient.  Is this possible?  Or are they one package?  Where can I learn how Ubuntu or Debian manage networking?  

I may be wrong but by changing profiles aka 'Locations' nm-applet seems to simply edit /etc/network/interfaces and for some reason doesn't set up wired networks properly making life more painful than it has to be.

Any insight into the problem in general or answers to my questions will be greatly appreciated.

Thank You
Konrad

Ubuntu Hardy Heron 8.04 on a Toshiba Tecra A6

---

