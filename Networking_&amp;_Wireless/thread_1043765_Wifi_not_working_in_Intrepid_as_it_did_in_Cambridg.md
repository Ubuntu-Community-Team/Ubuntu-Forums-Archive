---
title: "Wifi not working in Intrepid as it did in Cambridge"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by inspriation26 on 2009-01-18
Hello everyone,

I'm not a linux newbie but I do need some help. As you can tell based on the subject I switched from Fedora 10 to Ubuntu 8.10 because I ran Ubuntu on a virtual machine and fell in love with the ease of use over Fedora. I just came across one problem as I switched over: It has a driver for my wireless card but it refuses to work. The computer I'm currently useing is a Sony Vaio NR330E with a Atheros 802.11 PCI Express card. The network manager never even showed wireless networking as an option and I can't seem to get find the network manager from the system menu. All it has is network tools, frustrating me further. I do have to use Windows sometimes to play the Sims 2 and my wireless works there. Also on a side note, my wireless network comes off of my other computer through a netgear wireless router off of my ethernet connection from Windstream. I don't want to have to convert back to Fedora, not that it wasnt a great os. I just dont want to have to convert to being a windows only user again because of vista. When I run lshw -C network it says its disabled but it says the driver is on. and if i do iwconfig it says there is no wireless.
Please tell me how I may fix this problem? I need it soon because I'm a student and I need the internet for school purposes. I'd apreciate any help at all. 

Thank you

---

### Post by darksideforge on 2009-01-19
I'm interested in hearing any responses. I'm running a Toshiba with the Atheros 802.11 WiFi card built in and I've never had trouble before switching over to Ubuntu. I have great connectivity with the Ath01 networking via Cat5E to the wireless router (Linksys 802.11B), but I'm not even offered a wireless option under System>Network. I've created a Wireless 1 connection, and my Toshiba is showing recognizing the Atheros card as being installed under $lshw -C network but it's coming back as Disabled, meaning no driver is installed for the card. Where can I find the driver(s) needed? The Atheros offers a .EXE program download, but since I'm not running windows I can't download the executable to in turn download the Atheros driver. Any suggestions will be greatly appreciated.

---

### Post by superprash2003 on 2009-01-19
post output of 
1)lshw -C network

from the terminal

---

### Post by inspriation26 on 2009-01-19
Well I did find this program in the repository that can install windows drivers. I havent messed with it as of yet but I'll post what happens. How do you post out put on here any way?

---

### Post by inspriation26 on 2009-01-21
ok this is the out put for lshw -C

PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:1a:80:b9:c2:97
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.1.5 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9e:d1:16:09:58:ae
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

I hope this will help. I'm not sure what to make of it.

---

### Post by breaky9973 on 2009-01-21
Maybe it is the same issue as my wireless network card. The soft switch to turn on wifi doesn't work anymore after I upgrade to 8.10. I have to unload and re-load the driver again to make it work. In my case that is iwl3945.

try this for a change: 

turn on wireless on your laptop/desktop

then unload the driver:

sudo rmmod sky2 (assuming sky2 is the driver name)

reload the driver:

sudo modprobe sky2

---

### Post by ibutho on 2009-01-21
Your have an Atheros AR242x wireless card. For some reason Ubuntu (Including Jaunty alpha 3) does not seem to play along nicely with these cards, but they work out of the box on other distros. Try the suggestions in this [thread]("http://ubuntuforums.org/showthread.php?t=1026770") and see if that helps resolve your problem.

---

### Post by inspriation26 on 2009-06-02
Thank god that the offical release of Jaunty supports my card. I'm a ubuntu only user now! XP

---

### Post by Mgiacchetti on 2009-06-02
Wow, Cambridge to Intrepid?

No wonder it doesn't work the same, they're years apart :)

---

### Post by inspriation26 on 2009-06-02
> **Mgiacchetti said:**
> Wow, Cambridge to Intrepid?

No wonder it doesn't work the same, they're years apart :)
hey dont dis Fedora! It worked pretty well once I switched back to gnome. I think it was because i was using kde at the time. I think the fedora community works its @$$ off like the rest of us so back off. Sorry to get so defensive but I love that distro just as much as Ubuntu.

---

