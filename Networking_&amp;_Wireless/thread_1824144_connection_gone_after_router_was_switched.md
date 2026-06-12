---
title: "connection gone after router was switched"
date: 2011-08-13
forum: Networking &amp; Wireless
---

### Post by ChaosTage on 2011-08-13
hey guys 

after a while of silent reading i now have a little problem of my own

i recently had to switch routers because my old one didnt work anymore. i have a dual boot machine with win7 for games and natty narwhal (64-bit) for everything else. i'm quite new to ubuntu, i know how to navigate the menu, change settings, install things, just the basic stuff. i dont know how to use the terminal yet except some basic commands for installing and updating software.

after my router swap, my connection for windows was back, although i had to pull out the network cable and plug it back in for this to happen. unfortunately my connection in ubuntu is still gone. i see the connection in network manager, but i cant access the internet through it. i tried setting up a new one with the same settings, to no avail. 

i connect to the internet directly through my router. i tried finding some documentation for it but havent had luck with that. 

is there some way to reset the connection? or let ubuntu set up a new one like when i'm doing a fresh install? i think that ubnuntu still thinks i'm using the old router and that this is the cause for the connection fail.

i hope someone can help me with this meddling problem

thanks a bunch in advance!

---

### Post by ChaosTage on 2011-08-13
nobody's got an answer?:icon_frown:

---

### Post by thefasterblueone on 2011-08-13
Is this a wireless connection? You say you can 'see it', then click on 'edit in Network Manager and adjust the settings for that connection.

Post the results of:

```
ifconfig
```

---

### Post by ChaosTage on 2011-08-13
```
  eth0      Link encap:Ethernet  HWaddr 20:cf:30:77:3c:64  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
            Interrupt:45 
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:24 errors:0 dropped:0 overruns:0 frame:0
            TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
            RX bytes:1440 (1.4 KB)  TX bytes:1440 (1.4 KB)
  
```that's my ifconfig. my pc is connected with my router through a wire. i already considered playing around with the settings as i said i think it's because ubuntu thinks i still use my old router. but i dont know what i would have to change. i'm still quite new at this so bear with me:D

anyway i see the connection eth0 when i open the network manager, however when i click on the taskbar applet (i prefer the classic gnome look over unity) it says that i'm not connected to any wired connections and i cant see the eth0 connection either so i cant connect to it.

---

### Post by ChaosTage on 2011-08-16
ok after my connection went awol on both windows and ubuntu again, i  switched off my pc, plugged out the power cable for a few minutes,  plugged it back in, all while resetting my router. and voila it worked.  until now it hasnt failed for both ubuntu and windows yet. although as a  precaution im getting a used network card from a friend of mine  tomorrow. hope it holds out until then.

anyway thanks for all the help and views:popcorn:

---

