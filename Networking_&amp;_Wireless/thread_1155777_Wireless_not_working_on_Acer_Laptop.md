---
title: "Wireless not working on Acer Laptop"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by superkop007 on 2009-05-11
Hi guys

i have an Acer 4420-5963 laptop and i recently installed ubuntu hardy heron on it and realised that the wireless antenna isnt working on ubuntu meaning that it works when i use vista but when i use ubuntu it says wireless internet is not compatible...

The problem is not with the router but with my laptop itself as my dads laptop is able to connect with the router and so does my laprop but with Vista only...
When i log in using ubuntu, i cannot even see the wireless option on the screen and even the light doesnt blink on my laptop to show that wireless is on...

I think that the drivers arent present but i am not sure and am unable to work this out...

please help me out here guys...
Thanks

---

### Post by Peter09 on 2009-05-11
Can you post the output of the terminal commands

```
ifconfig
```

and

```
lshw -C network
```

---

### Post by sahabcse on 2009-05-11
Paste the o/p of 

#lspci
#dmesg

---

### Post by superkop007 on 2009-05-11
for lshw -C network the output is:

 *-network               
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:1d:72:35:00:71
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=10.0.0.2 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

---

### Post by superkop007 on 2009-05-11
there is no output coming from the following 2 commands:

#dmesg
#lspci

this is really bugging me...

I went into the synaptic package manager and installed the latest version suitable of ndiswrapper...
it is now available in the system->administration as "windows wireless drivers", but when i run it, it says that there arent any windows wireless drivers available on deck but i can run wireless internet when i use Vista...

Maybe i can use WINE to make that windows wireless driver stored on the windows partition of my hard drive accessible from Ubuntu as well...

Am i going in the right direction here... 
this is really frustrating me...
Thanks guys

---

### Post by MysticGold04 on 2009-05-11
I tried to install Hardy on my laptop when I first got it... It didn't work.  I was really disappointed because I wanted to run an LTS... but I installed Intrepid and it worked, and just recently upgraded to Jaunty... works great in those versions... however I just could not get the wireless to work under Hardy at all.

---

### Post by Peter09 on 2009-05-11
try

```
sudo apt-get install b43-fwcutter
```

---

### Post by superkop007 on 2009-05-11
Thanks a lot you guys...
Its now working...

It seems the mistake i was doing was not installing Ndiswrapper properly...
I checked it out from this link:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver)

really helped A lot...

so happy...
thanks a million...

---

