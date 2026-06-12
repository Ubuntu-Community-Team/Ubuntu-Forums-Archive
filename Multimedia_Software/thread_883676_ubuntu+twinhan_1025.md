---
title: "ubuntu+twinhan 1025"
date: 2008-08-08
forum: Multimedia Software
---

### Post by bhavinpshah on 2008-08-08
Hi,

I want to have my TwinHan 1025 working on my ubuntu 8.04 box with VLC media player. Like the way TwinHan 1025 card works with windows - one can give Mac address and there is a virtual network adaptor created for the card.  Can someone please help me with this?

After reading ubuntu forum, there was a thread on how to have twinhan 1025 working with BTTV drivers. I followed that and installed it successfully. I am not able to view channels because I guess my service provider needs the virtual adaptor and MAC information of TwinHan Card. Can someone help understand me following queries or help me achieve above functionality? I am totally new to DVB and LinuxTV world.

What is the difference between the BTTV driver and the one provided on TwinHan website - AZLinux_v1.4.2_CI_FC6? I know it is for FC 6 but it does not work on FC 6 either. What is CI? There is a driver available for without CI also.


Thanks,
Bhavin

---

### Post by mocha on 2008-08-08
I use a Twinhan 1022a which is like an updated 1020.  I'm not too familar with the 1025, is that just a regular DVB-S card?  Anyway, all I needed to get it to work was add dvb-bt8xx, dst, and bttv to the /etc/modules file.  Actually to test it first just do a "sudo modprobe dst" and the same with the other 2 modules and see what output you get.  Then you should end up with an adapter in /dev/dvb/adapter0.  Inside of there (on my system) I have a demux0, dvr0, frontend0, and net0.  

If you get all that accomplished then it's just a matter of installing dvb utilities for tuning and zapping (search synaptic) and then setup a player (mplayer, me-tv, kaffeine, vdr-xine, mythtv, etc).  There are a number of how-to's for the players if you look on google.

I think "CI" has something to do with pay tv module??  I'm not sure about the mac address and virtual network adapter stuff, I only use my Twinhan to watch DVB-S television.

---

