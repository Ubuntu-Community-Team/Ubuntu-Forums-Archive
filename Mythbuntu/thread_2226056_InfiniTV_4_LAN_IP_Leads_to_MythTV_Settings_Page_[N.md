---
title: "InfiniTV 4 LAN IP Leads to MythTV Settings Page [NETWORK DRIVER]"
date: 2014-05-25
forum: Mythbuntu
---

### Post by Golono on 2014-05-25
I've been going through the process of setting up an HTPC at home using the Ceton InfiniTv 4. Because of the lack of clarity on the wiki pages online, I thought that I could run OpenELEC or xbmcbuntu and I wasted a few hours trying to setup the infinitv 4 on those before I moved on to Mythbuntu. 

Once I went through the hassles of installing the drivers, I tried accessing the Infinitv's information page with the default IP. As it turns out, that ip leads me to MythTv's settings page. I've tried editing the interfaces text as the [wiki suggests]("http://www.mythtv.org/wiki/Ceton_InfiniTV_4#Setting_up_the_Network_Driver") and after six hours of trying everything that I can think of, I've gotten nowhere. 

Needless to say I'm feeling frustrated and I would appreciate some help. The MythTV forum is not very active so I'm hoping that I can get more help here.

---

### Post by blm-ubunet on 2014-05-26
I do not have this h/w.

AFAIK the Ceton card appears as a network adaptor.
It will have its own IP address ; not the same as the host computer's network adaptor.
You must be using the localhost IP in the browser URl..

The wiki is a little confusing (or I am) when it talks about Ceton card running a DHCP server.
But an IP address must be allocated from somewhere & the Ceton adaptor is its own private network.
Most people's computer's are not running DHCP servers (their routers are DHCP server &/or using static IP).
The router does not see the private network adaptor unless it is bridged.

After it has been reset (by python script) it should be
[http://192.168.200.1](http://192.168.200.1)

I would guess your home router was 192.168.1.1 & computer (host box) is 192.168.1.2 or similar.

---

