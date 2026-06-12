---
title: "motorola surfboad b5101modem config for ubuntu"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by rosh08 on 2010-04-04
hi i want to know how to config my motorola surfboad b5101modem in ubuntu and how to setup a dial up connection for it.

---

### Post by dineshs on 2010-04-04
how is this modem connected to PC?Ethernet?If yes post the output of```
ifconfig
```

---

### Post by rosh08 on 2010-04-04
this is the output and im connected through usb connection


Link encap:Ethernet  HWaddr 00:1d:72:6f:23:b9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:17:ee:6c:85:7c  
          inet6 addr: fe80::217:eeff:fe6c:857c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4243 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:213527 (213.5 KB)  TX bytes:1836 (1.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:a4:90:72  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-A4-90-72-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by cascade9 on 2010-04-04
> **rosh08 said:**
> hi i want to know how to config my motorola surfboad b5101modem in ubuntu and how to setup a dial up connection for it.

You will never setup a dialup conenction with that modem- its a cable modem. 

Better to use the ethernet conenction- I never tried setting up my surfboard I had with USB in linux, but I'm pretty sure it needs drivers- and they are windows only as far as I know.

---

### Post by dineshs on 2010-04-04
post the output of ```
lsusb
```

---

### Post by cascade9 on 2010-04-04
Checked the motorola site- 

> **Where can I get drivers for USB support?**
[Click here]("http://broadband.motorola.com/consumers/support/default.asp") to download the USB drivers.
   **Do you have Macintosh USB drivers?**
No. Since Macintosh® computers generally ship with built-in Ethernet interfaces, no USB driver is available.
   **Do SURFboard cable modems support Linux USB drivers?**
Not at this time.
[http://broadband.motorola.com/consumers/support/faqs/surfboard_faq.asp#linux_usb_drivers](http://broadband.motorola.com/consumers/support/faqs/surfboard_faq.asp#linux_usb_drivers)

It does need drivers for USB, and there are no linux (or macos) drivers. 

Sure, it might be possible to get it going via USB on linux, but its going to be no fun at all. Just use ethernet, its pretty much plug and play with the ethernet connection.

---

### Post by rosh08 on 2010-04-04
[B]Bus 002 Device 003: ID 04f2:b016 Chicony Electronics Co., Ltd VGA 30fps UVC Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 07b2:5101 Motorola BCS, Inc. SurfBoard SB5101 Cable Modem
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


[/B]

---

### Post by rosh08 on 2010-04-04
i can even connect through lan as well but for that i need to update the mac id with the internet provider

---

### Post by dineshs on 2010-04-04
Pl try this(though not exactly)
[http://www.zyxware.com/articles/2008/02/11/setting-airtel-gprs-ubuntu-nokia-communicator-9300-and-data-cable](http://www.zyxware.com/articles/2008/02/11/setting-airtel-gprs-ubuntu-nokia-communicator-9300-and-data-cable)

---

### Post by rosh08 on 2010-04-04
when im doing the sudo wvdialconf /etc/wvdial.conf part its showing error...in my network connection its showing auto ent1...how to create a dialup now

---

### Post by cascade9 on 2010-04-04
wvdial is a dialer...you dont have to dial with cable. 

You might have to go into the modem and set a username/password, if your ISP needs them (which I've never had to with cable, but who knows what the cable is like in the country you are in). As far as I know, if your modem has the 'power', 'recive' 'send' and 'online' lights lit up, you shouldnt need to enter anything, just plug in the the ethernet cable into the modem and yoru computer, start it, and it should just work.

If you need to enter a username/passowrd to conenct to your ISP, you need the PPPoE packagee (comes with most distros) and you will have to enter the modem 1st- go to a webbrowser, and type this in as address- 

192.168.100.1 

If it needs a username/password to get into the modem, they should be these (this is pretty much the standard for motorola)- 

Username- admin
Password- motorola  (if motorola doesnt work, try 'password', no quiotes). 

There should be somewhere to enter the username/password if your ISP needs one.

---

### Post by rosh08 on 2010-04-04
cannot access the modem using 192.168.100.1 in ubuntu but in windows im able to..my isp connection requires id nd password for connecting...whn im connectiind using usb cable its showing auto eth1

---

### Post by cascade9 on 2010-04-04
> **rosh08 said:**
> cannot access the modem using 192.168.100.1 in ubuntu but in windows im able to..my isp connection requires id nd password for connecting...whn im connectiind using usb cable its showing auto eth1

Cant connect to the modem in ubuntu using ethernet or USB?

---

### Post by rosh08 on 2010-04-04
no

---

### Post by cascade9 on 2010-04-04
If it doesnt work with ethernet, then the only thing I can think of is your ethernet cable is broken. 

Even if you cant connect to the internet, you should still be able to access the modem.

---

### Post by dineshs on 2010-04-05
If you are not able to access modem via ethernet,try to assign an IP manually to your ethernet interface.For this,follow this guide
[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)
ie
Right-click on the nm-applet and then click on Edit Connections.
Select the tab, wired 
select the connection and click edit(you can add the ethernet connection if not listed)
select ipv4
method-manual
click add
address 192.168.100.100
mask 255.255.255.0
gateway 192.168.100.1
then hit enter
DNS 8.8.8.8
then click apply

---

