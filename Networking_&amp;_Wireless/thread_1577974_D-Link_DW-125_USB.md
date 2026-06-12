---
title: "D-Link DW-125 USB"
date: 2010-09-19
forum: Networking &amp; Wireless
---

### Post by chemlocke on 2010-09-19
Hello, I've had Ubuntu 10.4 for a while on my laptop and decided to install ubuntu on my desktop today. Everything's been working excellently but I can't connect to the internet. I use a D-link DWA-125 usb adapter. It had been working perfectly fine prior to the installation. I've already reviewed several forums and blogs that talk about this problem but no solution seems to work. So far, I've got the right driver (3070) on a CD and I've extracted it onto my local folder on the desktop. Only problem is that I don't know where to go from there. Thanks in advance. :P

---

### Post by bkratz on 2010-09-19
If you do an 

lsusb

in the terminal (that is LSUSB in lowercase) and the ID given is

this is for those devices with usb.id of 07d1:3c0d 

Then this is the thread for you.
[http://art.ubuntuforums.org/showthread.php?t=1425564](http://art.ubuntuforums.org/showthread.php?t=1425564)
esp post 37.

---

### Post by chemlocke on 2010-09-20
Much thanks, I'll check it out.

---

### Post by chemlocke on 2010-09-21
Well, I tried that to no avail. I followed it to the t and it wouldn't work. The usb is recognized by the computer, it even recognizes that it is for internet because when I plug it in or unplug it, the "you are now disconnected" dialogue box opens on my top right corner. However, when I click on the networking icon, there are no available internet connections. Regardless, I can connect to my wi-fi with every other computer so its definately the d-link. Any help?

---

### Post by bkratz on 2010-09-21
> **chemlocke said:**
> Well, I tried that to no avail. I followed it to the t and it wouldn't work. The usb is recognized by the computer, it even recognizes that it is for internet because when I plug it in or unplug it, the "you are now disconnected" dialogue box opens on my top right corner. However, when I click on the networking icon, there are no available internet connections. Regardless, I can connect to my wi-fi with every other computer so its definately the d-link. Any help?

First, you do need to make sure that the ethernet connection is unplugged when you try the wireless. Network manager uses the wired if available. If you go to the terminal (application>>accessories>>terminal) and type in

```
sudo iwlist scan
```


Do you see A/P's? the command above will require your password which will not be echoed to the screen--just press enter when done.

you might want to post the output of 

```
lshw -C Network
```

and also 

iwconfig

---

### Post by chemlocke on 2010-09-21
Thanks! For the first, I get 
```
lo                       Interface doesn't support scanning.

eth0                  Interface doesn't support scanning.
```and 
```
 *-network
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: 5
bus info: pci@0000:02:05.5
logical name: eth0
version: 10
serial: 00:19:21:b1:8f:4e
width: 32 bits
clocks: 33MHz
capabilities: bus_master_ cap_list ethernet physical
configuration: broadcast=yes driver=8139too driver version=0.9.28 latency= 64 max latency=64 mingnt=32 multicast=yes
resources: irq:20 ioport: b8000(size=256) memory:feaefc00-feaefcff

```and for the last I get:

```
lo no wireless extensions.

eth0 no wireless extensions.
```I'm online with my laptop (also ubuntu) and typing this stuff over. @_@

---

### Post by bkratz on 2010-09-21
Did you even see your wireless card listed when you did the lsusb earlier?
There should have been some output about it in the commands you just did.


Didn't know you were transferring between computers. If you had done something like

sudo lshw -C network > hardware.txt

You would have ended up with a file called hardware.txt in your  /home/user directory which you could have transferred via usb key to the other computer for posting.

---

### Post by chemlocke on 2010-09-21
Mmmm... This is not good. Before the wi-fi card would flash and it would be recognized on the computer but now it's completely dead. Regardless, when I ran lsusb, i can clearly see the D-Link System.

---

