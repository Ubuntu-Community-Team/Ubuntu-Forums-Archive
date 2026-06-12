---
title: "Cannot Connect with Linksys WUSB54GC"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by fiish0302 on 2009-02-02
I just set up a new computer intended to be a fully Ubuntu-based rig, running Ubuntu 8.10 Intrepid amd64. The computer is in a different room from our ADSL router so I decided on a wireless connection. 

Since the support documentation at help.ubuntu.com mentioned the Linksys WUSB54GC works out of the box with Intrepid I decided to buy that. However, I have two problems with it:

(1) Upon startup, the adapter is not detected, and does not show in lsusb. It does get detected if it is reinserted.

(2) When the adapter does get detected it cannot pick up or connect to any wireless networks, let alone my home network. 

My home network is an 802.11g network using WPA2 encryption on a Linksys WAG54G2.

It is not the reception as I am writing this post from a laptop at the same desk, connected wirelessly.

I have also tried ndiswrapper with the XP and also the Vista x64 drivers to no avail.

When I enter 'lsusb -v | grep Linksys' I get this:
> 
can't get device qualifier: Protocol error
can't get debug descriptor: Protocol error
cannot read device status, Protocol error (71)
Bus 004 Device 008: ID 13b1:0020 Linksys WUSB54GC 802.11g Adapter [ralink rt73]
  idVendor  0x13b1 Linksys


A 'wlan0' device does show up in iwconfig's output, stdout as follows:

```

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig stdout as follows:

```

eth0      Link encap:Ethernet  HWaddr 00:24:21:10:20:dc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:22756738914 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:249 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30448 (30.4 KB)  TX bytes:30448 (30.4 KB)

```



Any help or advice would be appreciated.

---

### Post by fiish0302 on 2009-02-03
I have got it to work by plugging the adapter directly to one of my computer's front USB ports (it was previously on one of the rear ports via the included USB extension cable) and it now picks up the network and is able to connect. Not very fast, but better than not having anything.

This is not my ideal solution, so I shall continue updating. I now suspect either the USB controller or the extension cable itself was the source of my problem, in light of the protocol errors I was getting.

---

### Post by adam77 on 2009-03-01
Did it work 'OotB' (apart from having to plug the adapter into a different usb port)?

I.e. no driver installation/configuration.

Thanks.

:guitar:

---

### Post by yamushk on 2009-03-05
> **adam77 said:**
> Did it work 'OotB' (apart from having to plug the adapter into a different usb port)?

I.e. no driver installation/configuration.

Thanks.

:guitar:

Hi,

I'm having trouble getting a signal. Kubunto identifies the cart "out of the box" as you mentioned - I see it in my lsusb list, but I do not see any wireless networks. I don't know where to begin, as I remember I had trouble with previous card, but eventually it simply worked without doing anything special. 

Would appreciate some help... 

Thank you

---

### Post by adam77 on 2009-03-05
I just purchased the WUSB 54GC (grey (v1?)) and it worked first time out-of-the-box, with the following minimal configuration to get connected:

Plug-in.
Wait a few seconds.
Network manager applet -> Connect to hidden network.
Enter network id, security protocol, and password.

All done.

Hot swapping works fine too (and also with extension cable).

Hardware: IBM R50e Laptop
Ubuntu: Intrepid with latest updates.

---

### Post by adam77 on 2009-03-05
> **yamushk said:**
> Hi,

I'm having trouble getting a signal. Kubunto identifies the cart "out of the box" as you mentioned - I see it in my lsusb list, but I do not see any wireless networks. I don't know where to begin, as I remember I had trouble with previous card, but eventually it simply worked without doing anything special. 

Would appreciate some help... 

Thank you

is your network 'hidden'? mine was and did not show up in the list of available networks, i had to enter the network's identifier

---

### Post by MatthewMetzger on 2009-03-10
I'm glad to hear that the WUSB54GC adapter works fine with Ubuntu 8.10. I just had a client purchase one and I wasn't exactly sure that it would work with Ubuntu. So relieved that it does.

---

### Post by MatthewMetzger on 2009-03-11
Unfortunately, the WUSB54GC v3 does not work out of the box (at least for me) on Ubuntu 8.10. I have the latest updates, which were installed while connected to a wired network.

I tried plugging it into several different USB ports. I restarted the machine several times. I restarted networking. Nothing made the USB adapter show up in the networking applet on the top gnome panel.

Any suggestions?

The computer is a Dell GX270 Small Form Factor.

---

### Post by fiish0302 on 2009-03-13
For me it worked OotB, to an extent. If it is already plugged in when Ubuntu starts it doesn't get detected, however reinserting it makes it work without major issues.

---

### Post by Klondike on 2009-03-19
I'm on a Dell XPS desktop from 2005, and I can't get my WUSB54GC v3 to work out of the box at all.  I ndiswrapper-ized the included XP drivers and everything. I tried connecting to a "Hidden Wireless Network" with the known details. Nothing doing.

---

### Post by syrupofwood on 2009-03-21
This just sucks.. I had to replace my old Linksys WUSB54GC v1 and I received a WUSB54GC v3.

v1 works right out of the box, never had a problem with it.

v3 does not work at all. I have not been able to find out a way to make it work.

It is recognized by lsusb as "Linksys". I used ndiswrapper, installing the WinXP driver that comes in the CD and even though it recognizes it and says that the device is present, it is not shown on ifconfig or iwconfig. 

I can see on this post that this is the behavior that most of the people are having.. Hopefully someone finds out. As for me, I will keep trying and researching.. Will get back if I can make it work.

-gabriel

---

### Post by adam77 on 2009-03-21
How do I find out what version I've got (v1 or v3)? (i assume you mean the device itself and not the drivers?)

Thanks.

---

### Post by syrupofwood on 2009-03-22
> **adam77 said:**
> How do I find out what version I've got (v1 or v3)? (i assume you mean the device itself and not the drivers?)

Thanks.

Well, v1 would be a gray usb dongle, v3 is black.

Hope that helps.

-gabriel

---

