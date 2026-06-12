---
title: "Very n00b wireless router question."
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by joshh88 on 2009-04-04
When I bought my laptop from dell(big mistake but whatever)I ordered it with a draft N card. I later purchased a draft N router. Belkin I believe(at work so can't say for sure will update when I get home); I tried to set it up and connect. My computer could not connect(Dell M1330) but the opther 3 dells Inspiron 15xx and an HP Pavilion. I'm the only one with a draft N card. So I'm wonder if that since I switched from Vista to Ubuntu perhaps I will now beable to connect to that router. Also I read something about router software(firmware?) that you can download a Linux version? Would that help me with my compatibility? Also if I did download Linux firmware on the router would that mess with any of the games I often play that are Windows only?

---

### Post by chili555 on 2009-04-04
Usually, when you don't connect right away, it's because the driver module for your wireless card is not installed. The router doesn't know or care that a computer on the network is using Ubuntu or any other version of Linux. Let's try to figure out what's really happening before we blame the poor innocent router! Open a terminal (Applications -> Accessories -> Terminal, if you are using Gnome) and type:```
sudo lshw -C network
```That means, roughly, 'list my hardware, but just list the class of devices: network.' Post the result here and we'll be well on the way to a fix.

---

### Post by mkgkg on 2009-04-04
Hi, 
i think that the problem is not the firware of your router, a connection not depends directly  on the os you're using. Check in your router config page (often 192.168.0.1 or 192.168.0.0 ) which standard are u using (802.11 b,g or n) and maybe the problem could be the encryption key you used.
If your others pc are able to connect to your router, it means that  your router is not using draft n standard , and it's very likely that it's using a mix of g and n and this in most of cases is a source of problem.

---

### Post by joshh88 on 2009-04-04
I'm at work so when I get home I'll post the network specifics. For now this is what I know, There are only two draft N laptops the rest are G. Both N cards are of course backwards compatible as is the router. Will it choose to go G only as that is the lowest required for the group? Also will there be a way to reset the router to defaut settings, after the firt failed attempt at connecting (4months ago) I don't have any of the information on it anymore

---

### Post by abn91c on 2009-04-04
some routers like my linksys you need to press and hold the reset button in the back for 30 seconds to reset to manufacturers settings, check the Belkin manual for something similar.

---

### Post by joshh88 on 2009-04-04
*-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:69:bd:b1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.0.2 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:7c:d7:5a
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 latency=0 link=no module=tg3 multicast=yes port=twisted pair
Heres the results, I don't have the router right now have to get it from  friends house; they have been using it since his router has been out.

---

### Post by chili555 on 2009-04-04
> ip=192.168.0.2 Looks like it's working fine. Did you assign an IP address manually or is it actually connected to your router, even though the router is next door?

What did you try and fail that made you say it could not connect?

---

### Post by joshh88 on 2009-04-04
OK I finally got it set up, thank to a very good write up on PCWorld and my crossreferencing of th Windows to Linux. Also I had to call support because it would not connect wirelessly. Turns out this router only works with a WEP not WPA2 password setting T_T. This worked for me yay even though it didn't work in vista when I tried lol. I still have a question though; right now I'am using the default wireless modem provided by Comcast, will there be any interference from using another wireless router as a modem(only until I can get a regular modem from comcast...monday)

---

### Post by abn91c on 2009-04-04
> **joshh88 said:**
> OK I finally got it set up, thank to a very good write up on PCWorld and my crossreferencing of th Windows to Linux. Also I had to call support because it would not connect wirelessly. Turns out this router only works with a WEP not WPA2 password setting T_T. This worked for me yay even though it didn't work in vista when I tried lol. I still have a question though; right now I'am using the default wireless modem provided by Comcast, will there be any interference from using another wireless router as a modem(only until I can get a regular modem from comcast...monday)
It will not matter, but go to the live chat at comcast.net and give them the MAC address of the modem, they can check your connectivity remotely to make sure your network is OK

---

