---
title: "New user needs 2wire driver"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by JerryI on 2009-03-09
I am completely new to linux.  This is my first post. I have installed ubuntu on my laptop.  I cannot connect to the internet.  I assume that first I need a driver for my 2wire 802.11g USB Wireless adaptor.  The command lsusb shows my wireless mouse and 
Bus 001 Device 002 ID 0ace:1215 ZyDAS WLA-54L WiFi and some linux foundation root hubs. What do I do next?

---

### Post by dmizer on 2009-03-09
Try this: [http://www.ubuntu-unleashed.com/2008/02/howto-setup-2wire-80211g-wireless-usb.html](http://www.ubuntu-unleashed.com/2008/02/howto-setup-2wire-80211g-wireless-usb.html)

---

### Post by JerryI on 2009-03-09
Someone is going to have to communicate with me at a much lower level. Please keep in mind that yesterday I couldn't even spell linux or Ubuntu.  When I type lsusb, I get:
Bus 001 Device 0002 ID 0ace:1215 ZuDas WLA-54L WiFiI also see my wireless mouse and Bus 001 Device 004 samsung... which is a 2GB flash drive,
so my card does not seem to match the referenced link.

Furthermore, since I do not have access to the internet yet via Ubuntu, I have to get web stuff via another computer and then transfer it to my Ubuntu computer via my flashdrive. I understand the command line concept (I started with MSDOS 1.0), but I do not know how to use commands such as wget or sudo (e.g., where to put the files so that the commands will find the files I copy in.  Do they go into the root directory, onto the desktop, wherever?)

sudo ndiswrapper not found

bash ndiswrapper: command not found

typed sudo apat-get install ndiswrapper-common 
couldn't find package ndiswrapper-common
downloaded ndis driver wrapper for the linux kernal 
ndiswrapper-1.54.tar.gz.gz 
from 
[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)
Put it on Ubuntu Desktop

Double clicked it.  Now I have ndiswrapper-1.54.tar.gz on desktop also.

Double clicked it. Got error message. gzip: stdin: not in gzip format. 

I am totally bewildered and overwhelmed at this point.  I decided to try Ubuntu because Vista is giving me fits, making me spend hours to do tasks I used to be able to do in seconds on XP.  Pls help me get past this first hurdle (getting access to my wireless router and the internet).

---

### Post by JerryI on 2009-03-09
I'm making a little progress now.  I have determined via:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

that I am using 8.10 Intrepid Ibex and that I need to install some packages via my internet access on this Vista computer.

I will proceed and advise.

---

### Post by JerryI on 2009-03-09
Update - next snag

To install ndiswrapper
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
sudo dpkg -i ndiswrapper-utils_*.deb
has error: sudo dpkg -i ndiswrapper-utils-*.deb should read sudo dpkg -i ndiswrapper-utils-*.deb
Also I had to install ndiswrapper-common first (which I should have known)

Installed ndiswrappper, its utilities, and ndisgtk

I then moved all three of the files ndi*.* that I had processed from the desktop into a desktop folder called 'Archives'.

When I tried to install the driver from WlanUIG.inf
via command: sudo ndiswrapper -i WlanUIG.inf
system returned
  Warning installation may be incomplete
couldn't find WlanCIG.sys or WlanUIG.sys

I can't install the sys files with the sudo ndiswrapper-i WlanUIG.sys because it only installs inf files.

What now?

---

### Post by JerryI on 2009-03-09
Per [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
I disabled some bcm drivers and rebooted and ran lsusb
My Usb wireless is Bus 001 Device 002:  ID 0ace:1215 ZyDAS WLA-54L WiFi

Contrary to the above link, no response is in the format xxxx:xx:xx:xx.x 

Then I entered lspci -n
and did not get anything that started with 0ace.

Now what can I try?

---

### Post by JerryI on 2009-03-09
When I type ndiswrapper -l I get the response
wlanuig : invalid driver

so I presume I need to uninstall it.  I will research to find out how to do that.

---

### Post by JerryI on 2009-03-09
I have successfully uninstalled invalid wlanuig.  Now I am going to try to install by getting into my Argives directory where the sys file and the inf file both exist.

---

### Post by JerryI on 2009-03-09
I uninstalled invalid wlanuig and put all files in Archives; then went to Archives directory and used command sudo ndiswrapper -i WlanUIG.inf

Got response that couldn't find wlancig.sys - installation may be incomplete.  

Issued command ndiswrapper -l

Shows wlanuig : driver installed;

Hooray.  Now what?  Need help to see if this driver lets me connect via wireless to internet.

---

### Post by JerryI on 2009-03-09
Edited wireless connection.  Checked 'connect automatically'.  Wireless tab shows SSID: 2wire411  Mode: Ad-hoc  BSSID is blank  MAC address is 00:22:A4:1c:bd:b0  MTU: automatic  

Wireless security tab shows WEP 40/128 Key and has key shown and show key bok is checked.

I still show no wireless connection. My ISP help desk declines to offer any help help in setting up a linux computer.

Now What do I do?

---

### Post by dmizer on 2009-03-09
We need to make sure that ndiswrapper is driving your card. Please post the output of:
```
lshw -C network
```

Sorry I was not around earlier. I was studying the back of my eyelids :)

---

### Post by JerryI on 2009-03-10
My research suggests this is a pervasive long-lived problem that nobody has reported solving for this silver colored non-pinch-waisted USB adapter.  I have bought another USB adapter (Belkin F5D7050 - $15) that is reported to be compatible with Intrepid, viz. [http://linuxsoftwareblog.com/blog/?p=30](http://linuxsoftwareblog.com/blog/?p=30)

I will report results after I obtain and attempt to install it.

---

### Post by JerryI on 2009-03-10
Output from lshw -C network
-------------------------------------------

gai@gai-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:86:5c:8e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7a:e9:be:f6:0a:2a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1e:37:f6:cc:c4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by JerryI on 2009-03-12
I have researched the issue and have concluded that a Belkin USB adaptor might solve the problem.  I have purchased one on internet for $15 and await its delivery for further testing.  Thanks to all who have provided assistance.

---

