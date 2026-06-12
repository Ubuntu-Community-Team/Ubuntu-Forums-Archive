---
title: "No internet"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by Tearaft on 2009-09-10
:PHi all,

Could someone please help me? I am at my wit's end. I recieved my new Dell Inspiron laptop today with Ubuntu 8.10. Absloute beautiful machine, however I can not get online no matter what I try. I have Motorola SBV5220 modem. I can't even get a ping. Nothing, nada, zip. I've tried everything that the help suggests on the computer and nothing. I contacted Dell by phone and the guy was nice but he knew nothing about Linux. I tried to chat with them online but when I provided the service number on the bottom of my computer they said that it wasn't a number from an american machine. I thought that perhaps in my attempt to get online I may have messed up a setting so I decided to start from scratch and reinstall BUT that's not happening either even though I set the boot order to cd/dvd first and then the Hard Drive (is there something else I need to do, I tried holding down the C key like you do in a Mac to boot from a disk.) The modem is fine I'm using  it right now. I have used Linux in the past I actually have Ubuntu 6.01 dual booting on my Mac and years ago I used Red Hat and Mandrake so even though I have forgotten much I'm not a total noob. When I purchased the computer it came with 30 day starter support form Ubuntu but I can't seem to find a site or a phone number to contact them. I'm sorry for rambling I am just so disappointed right now. I love Unix/Linux Open Source and I sing their praises all the time but this is starting out as a horrible experience. I'm regretting not buying another Mac.

Pax

Tomk

---

### Post by chili555 on 2009-09-10
Are you connected to the modem with an ethernet cable? Please post the output of these terminal commands:```
ifconfig eth0
sudo lshw -C network
```Thanks.

---

### Post by mbrush on 2009-09-10
I'm assuming that is a cable or dsl modem (do people still use dial-up?).

What's the output of 'ifconfig'?

What are the contents of '/etc/network/interfaces'?

---

### Post by Tearaft on 2009-09-10
Yes, I am using cable broadband internet

ifconfig etho

Link encap: Ethernet  HW addr 00:25:64;57"68:26
inet addr;fe80 : : 225:64ff:fe57:6826164 scope:Link
Up Broadcast Running Multicast MTU:150 Metric:1
Rx packets:13226 errors:0 dropped:0 overruns:0 frame:0
Tx packets: 10 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 TXqueuelen:100
RX bytes:746199 (746.1kb) TX bytes :1836 (1.8kb)
Interupt : 18

I hope there wasn't too many typos

I'll try and hurry and get the others

Thanks so much!

---

### Post by mbrush on 2009-09-10
I forgot you didn't have net on that machine, that must be a pain to type!

I'd ask you to give the output of 'ifconfig' (without the eth0) but that would take even longer to type.

You might want to try 'sudo /etc/init.d/networking restart' and note any errors or messages that it spits out.

---

### Post by Tearaft on 2009-09-10
This is a little more than half of it, I'm still copying the rest

sudo Lshw -C network

*-network
descripyion wirless interface
product: BCM4312 802.116/g
vendr:Broadcom Corporation
physical id: 0
bus info: pci@0000:0c:00.0
logicalnmae:ethl
version:01
serial:00:22:5f:f2:26:6f
width:64 bits
clock:33 mhz
capabilities: pm msi pciexpress bus_master
cap_list ethernet physical wireless
coonfiguration=broadcast-yes driver=wl
latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
*network
 description=ethernet. interface
product:88E8040 PCI-E Fast Ethernet Controller
vendor:Maxwell Technology group LTD
physical id:0

Thanks again. Do you need the rest?

---

### Post by Tearaft on 2009-09-10
'sudo/ec/init.d/networkingrestart/

says no such file or directory

---

### Post by Tearaft on 2009-09-10
'/etc/network/interfaces/'

no such file or directory!

---

### Post by chili555 on 2009-09-10
> **Tearaft said:**
> 'sudo/ec/init.d/networkingrestart/

says no such file or directoryWould you please try:```
sudo /e[COLOR="Red"]t[/COLOR]c/init.d/networking  restart
```Proper spacing and spelling are mandatory.

---

### Post by chili555 on 2009-09-10
> **Tearaft said:**
> '/etc/network/interfaces/'

no such file or directory!Please try:```
cat /etc/network/interfaces
```Thanks.

---

### Post by Tearaft on 2009-09-10
both 
etc/network/interfaces
and
car etc/network/interfaces

give

no such file or directory

---

### Post by Tearaft on 2009-09-10
sorry that was a typo above

suppose to be cat
not car

---

### Post by mbrush on 2009-09-11
To read the contents of the file, it's:

```

cat /etc/network/interfaces

```

The leading slash character matters.  And to restart networking the command is (note the spaces):

```

sudo /etc/init.d/networking restart

```

Good luck

---

### Post by Tearaft on 2009-09-11
Still nothing. I even reloaded the OS last night and yet still nothing. This has been an absolute disaster.

---

### Post by mbrush on 2009-09-14
Sorry for the late reply.

You have some pretty big problems if the suggested commands don't output anything.  It's possible that /etc/network/interfaces may just have your loopback adapter in there because of network-manager, but you should see something when you restart networking.

It may seem obvious, but you've tried configuring the nm-applet (the little network icon in the panel near the clock)?  You may just need to configure it using the GUI.

If that doesn't pan out, find out the name of your network adapter using the following command:

```

lspci

```

Scan through that list looking for the name/make of the network adapter and then hit google again with that network card name, your laptop name, "ubuntu" and the version of ubuntu you're using (or any combination of those) and you'll probably find your answer.  If you find no one else with the same problem, it's likely that you have a bad network card and possibly need to get it repaired.  Ubuntu has great support for wired network cards (in my experience) and seeing as the Dell machine was tested to work with Ubuntu, it's probably gonna be faulty hardware.

Good luck

---

### Post by p1t0u on 2009-09-15
Are you connected directly to the modem?

Are you using a different computer on the same modem?

Possibly your modem will not accept a computer with a different MAC address than the one it knows.
Sometimes you can just power off / on the modem and the new device will work; other times you have
to contact your ISP but that would be a pain if you had to do that every time you want to switch
computers.

---

