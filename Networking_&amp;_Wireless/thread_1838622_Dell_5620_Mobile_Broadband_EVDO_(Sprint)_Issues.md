---
title: "Dell 5620 Mobile Broadband EVDO (Sprint) Issues"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by MatthewTemple on 2011-09-04
I have been trying for a week to get this card to go.  If I can't it's back to Windows for me :-(

Anyway, I have been searching the net and here is what I think I know so far...

1.  The device shows up as a Qualcomm gobi 2000 V-413C P-8185 in lsusb
2.  when I run nmcli nm is shows wwan-hardware enabled and wwan disabled.
3.  When I run sudo nmcli nm wwan on it still won't enable the mobile broadband.  

uname -a
Linux LC-7 2.6.38-11-generic-pae #48-Ubuntu SMP Fri Jul 29 20:51:21 UTC 2011 i686 i686 i386 GNU/Linux


lsusb

Bus 002 Device 004: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 002 Device 003: ID 413c:8185 Dell Computer Corp. Gobi 2000 Wireless Modem (QDL mode)
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 413c:2513 Dell Computer Corp. internal USB Hub of E-Port Replicator
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


nmcli nm

RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         connected                   enabled         enabled               enabled              disabled

---

### Post by pdc on 2011-09-04
I wonder if this post is of help to you

[https://nowhere.dk/articles/ubuntu-natty-making-a-gobi-2000-wireless-modem-work](https://nowhere.dk/articles/ubuntu-natty-making-a-gobi-2000-wireless-modem-work)

as always, one can complicate things and give you other references ..........

eg.........

this 

[http://westhoffswelt.de/blog/0045_howto_setup_sony_vaio_x_wwan_gobi_2000_under_ubuntu_linux.html](http://westhoffswelt.de/blog/0045_howto_setup_sony_vaio_x_wwan_gobi_2000_under_ubuntu_linux.html)

......it depends how much intense reading you wish for:

wouldn't it be great if the simple instructions in the FIRST link worked?

let us know how you go 

the words .....gobi loader etc have been problematic in the past

---

### Post by MatthewTemple on 2011-09-04
PDC,

Your reply was very helpful.  Now i have the broadband card in my network manager applet and it shows up as a device in nmcli dev.

HOWEVER :-)  my most recent connection attempt from my syslog.

Sep  4 02:30:48 LC-7 NetworkManager[805]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
Sep  4 02:31:12 LC-7 AptDaemon: INFO: Quitting due to inactivity
Sep  4 02:31:12 LC-7 AptDaemon: INFO: Shutdown was requested
Sep  4 02:31:48 LC-7 NetworkManager[805]: <warn> CDMA connection failed: (32) No service
Sep  4 02:31:48 LC-7 NetworkManager[805]: <info> (ttyUSB1): device state change: 4 -> 9 (reason 0)
Sep  4 02:31:48 LC-7 NetworkManager[805]: <info> Marking connection 'sprint' invalid.
Sep  4 02:31:48 LC-7 NetworkManager[805]: <warn> Activation (ttyUSB1) failed.
Sep  4 02:31:48 LC-7 NetworkManager[805]: <info> (ttyUSB1): device state change: 9 -> 3 (reason 0)
Sep  4 02:31:48 LC-7 NetworkManager[805]: <info> (ttyUSB1): deactivating device (reason: 0).

---

### Post by pdc on 2011-09-04
I had not heard of nmcli till you mentioned it; I have no idea about it

I note

> CDMA connection failed: (32) No service

googling on the above I get various hits.......

eg

> I found a way around this issue.
p { margin-bottom: 0.08in; } It seems to be an issue with network-manager and how it is controlling the modem.



sudo service network-manager stop

This opens your modem up then use gnome-ppp

sudo gnome-ppp

And then put your username, password and #777

And hit connect. It will not show that your are connected! Open a browser and surf it up :D!

Hopefully they fix this in the next network-manager release!

You can remove network-manager from your start up programms so you don't have to stop it everytime!

last post...........bottom of the page........

---

