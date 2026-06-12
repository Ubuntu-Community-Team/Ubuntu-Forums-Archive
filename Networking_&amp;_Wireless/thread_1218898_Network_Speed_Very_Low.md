---
title: "Network Speed Very Low"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by zombi4sk8 on 2009-07-21
Hi ,
 
this is my first post and i'm really sick of this problem cause i don't know how to fix :confused::confused: and i'm start to get crazy form that
 
MY PROBLEM IS :
 
i have dsl at home and my speed is 4MB and that mean i can have 512kb download speed , but after using ubuntu 9.04 my download speed max 60kb i tried everythinfg to fix it and nothin worked till now .
 
i made a test speed from internet and it show me that my speed is 4mb 
i used xp in the same comptures and i get full 512 download speed
even in firefox is slower
 
i have this problem with my LAPTOP (HP TX2500) and my PC with (ALF USB Wireless) and i tried also (Linksys pci card)
even the lan card have the same slow speed
 
 
please help me i don't wanaa back to use windwos
 
Thanks

---

### Post by martinbaselier on 2009-07-21
If I understand you correctly, you should have a download speed of 512 kbyte/s, but you only get 60 kbps. And you have the problem on two pc's, tested it with 3 different wireless cards and one ethernet card. 

You say, you tried everything. Could you explain what you mean with that?

Did you have the wireless turned off when you tested the lan? 

Could you open a terminal, and copy the output of **iwconfig** (you can copy/paste from/to the terminal with the right mouse button menu)

---

### Post by zombi4sk8 on 2009-07-21
what i meant by trying everything is that i turned off ipv6 and installing broadcom driver again 

and yah the wireless card was off when i tried the lan cable

[php]lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:218  Noise level:165
          Rx invalid nwid:0  invalid crypt:1  invalid misc:0

pan0      no wireless extensions.
[/php]

---

### Post by martinbaselier on 2009-07-21
Ok, you want to try the lan first. (iwconfig is only for wireless). 
What does the following command show?
**sudo ethtool eth0**

You might want to test a bit with the speed setting: 
**sudo ethtool -s speed 10/100/1000**
and
**man ethtool** 
for more info.

---

### Post by zombi4sk8 on 2009-07-21
this is from 

[PHP] sudo ethtool eth0[/PHP]

[PHP]Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
    Link detected: yes
[/PHP]

and it's the same :confused::confused::confused::confused::confused:

thanks for your help first
second i reallly want this to work

---

### Post by martinbaselier on 2009-07-21
Have you also tried setting the speed to 10mbps ?

It would be helpful if you also tell what you tried. 
It would help me prevent asking unnecessary questions. 

to help your search the following commands are also useful:
**lspci**
when you run it, you see each device has a number in front of it.
**sudo lspci -v -s** followed by that number will give you details for one of the devices. 
**man lspci** for more info
**sudo lshw -c network** 
**sudo lshw -c network -html > hardware.html** will create a nice html document with info on your network devices. 

It can help to see the manufacturer (I have a sitecom usb wireless device for example; which is actually a realtek 8187B and it will show the kernel module in use (you could say it's the driver for the device)
**dmesg | grep eth0**
will show you the kernel messages about your nic

---

