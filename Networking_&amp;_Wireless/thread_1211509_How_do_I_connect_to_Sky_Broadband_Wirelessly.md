---
title: "How do I connect to Sky Broadband Wirelessly?"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by bob-linux-user on 2009-07-12
Can someone help please?
I am in the UK with Sky Broadband which runs on my main pc with Jaunty. I connect to Sky via a LAN.No problems. My Fiancée runs Windows XP and connects her laptop to Sky wirelessly. Needless to say her XP installation is very slow and I want to persuade her to use Ubuntu (Jaunty) instead. To prove it works I want to connect wirelessly to sky while running from the live CD.
I am fairly experienced with Ubuntu (and Windows) but am a bit of a noobie with wireless.I have noted down all the different settings from Windows. 
Please can someone give me an idiots guide to what settings I need to change in Ubuntu to get it working?

---

### Post by superprash2003 on 2009-07-13
it could be a bit difficult to setup wireless on a live cd.. but you can give it a shot.. first we need to see which wireless card your machine has.. post output of **lshw -C network** from the ubuntu terminal

---

### Post by moody_mark on 2009-07-13
Sorry if my question is a bit basic, do you see the SSID when you left click the network manager icon in the top right hand gnome toolbar? Ive used live CDs on a number of different PCs and the wireless connection in network manager has worked pretty much everytime, apart from with some new BT homehubs on a couple of machines.

---

### Post by bob-linux-user on 2009-07-13
Thanks Moody Mark and SuperPrash

Yes I do see the SSID along with several others and unsurprisingly my network has the strongest signal.I single clicked on my network name and a thing like a blue tadpole whizzed around between a grey and a green spot.It next asked for "Wireless Network Authentication Required" I put in my network password and the box reappears with a long string of jumbled letters instead of my original password. When I press connect nothing happens and the box reappears again.What should I do next please?

Output as requested below.

ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5702X Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:0d:56:75:f0:17
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5702-v2.25 latency=64 mingnt=64 module=tg3 multicast=yes
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 04
       serial: 00:04:23:8f:79:8e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=32 maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b2:ac:96:77:5e:47
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
ubuntu@ubuntu:~$

---

### Post by superprash2003 on 2009-07-14
is it a WEP or WPA key?

---

### Post by moody_mark on 2009-07-14
Sometimes when that box pops up you have a drop down to select the type of encryption, try changing it if its not set to the right type. I have seen this kind of problem on a couple of old laptops I got at home here, both were running 8.04. A neighbour kindly gave me his passkey to hop onto his network when i had trouble with my BT broadband. He had BT too but the newest type of home hub, interestingly enough only one of 3 laptops would connect ok. I think there maybe some problems with some wireless driver supporting the encryption correctly, depending on the card you have. I wish I knew more specifics, hopefully that output may help someone more knowledgeable on this forum to diagnose.

Heres what id do for now. - Connect to your router with hardwired ethernet, login to the router (username "admin" password "sky" by default) and change your wireless encryption to WPA or none, just for now. See if you can then connect wirelessly, you may find you can, in which case your narrowing the problem down to possible configuration settings.

I have heard some people mention that its better to turn off encryption completely and just use MAC filtering, not sure what the community's opinion would be on that one. You can still spoof a MACID though.

Let us know how you get on, id be interested to find out. Can you try another wireless machine? Perhaps if its not got ubuntu installed, try the live CD?

---

### Post by moody_mark on 2009-07-14
Update: I tested my new sky Netgear DG934G-1 with this laptop here today (Dell E6400) and the wireless worked ok. I just thought it worth mentioning in case I could grab any useful info for you. Heres the output of my "lshw -C network" command

```
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:21:70:e6:2e:dc
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.7-7 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:23:4e:7e:e1:5c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.2.13 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 96:04:16:0b:28:c9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

The encryption by default was WPA & WPA2 Personal in the gnome network settings window

---

### Post by bob-linux-user on 2009-07-14
The encryption according to Windows is WPA-PSK. When I boot onto the live cd and click on my network the default (and only possible ) setting on the "Wireless Network Authentication Required" box is WPA & WPA2 Personal which I assume is correct. I type in my password and press connect and the "Create Default Keyring" box comes up. I do not know anything about keyrings, what should i do here?

---

### Post by superprash2003 on 2009-07-15
you cant change the security key right?

---

### Post by moody_mark on 2009-07-15
> **bob-linux-user said:**
> The encryption according to Windows is WPA-PSK. When I boot onto the live cd and click on my network the default (and only possible ) setting on the "Wireless Network Authentication Required" box is WPA & WPA2 Personal which I assume is correct. I type in my password and press connect and the "Create Default Keyring" box comes up. I do not know anything about keyrings, what should i do here?

That box always comes up. Its to do with holding the passwords locally on your machine, they are encrypted with a key so they are not stored in clear text. Just enter a password in this box (anything will do), keep a note of it as you would do any password just in case and click ok, from here network manger should continue to go on and login. As you using the live CD you'll have to do this everytime as your are booting from a read-only disc (the CD-ROM)

---

### Post by bob-linux-user on 2009-07-15
Hello Mark and Superprash

Thanks for your help.
Finally got it working just when I was about to give up. I changed the network mode to ad hoc and also ticked the all users box. Deleting all the other networks (there seem to be about 10 just in my little cul-de-sac-the air must be buzzing) also helped.

That was the easy part-now have to persuade my Fiancée to make the change to Ubuntu!

Regards

Bob

---

