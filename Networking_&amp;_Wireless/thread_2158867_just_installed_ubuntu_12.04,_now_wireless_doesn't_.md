---
title: "just installed ubuntu 12.04, now wireless doesn't work"
date: 2013-06-30
forum: Networking &amp; Wireless
---

### Post by hw2005 on 2013-06-30
Hey, I'm new to Ubuntu.  I installed 12.04 on my hp pavillion zv6000.  My computer won't display the wireless network.  I read through some threads and found one with people that seemed to have a similar problem.  [http://ubuntuforums.org/showthread.php?t=1997880&page=6](http://ubuntuforums.org/showthread.php?t=1997880&page=6)

a number of people claimed that these two commands (followed by a reboot) solved their problems. 
[COLOR=#000000]sudo apt-get remove --purge bcmwl-kernel-source[/COLOR]
[COLOR=#000000]sudo apt-get install linux-firmware-nonfree[/COLOR]

This did not work on my computer.  

my computer displays "E: unable to locate package bcmwl-kernel-source" after the first command and "unable to locate package linux-firmware-nonfree" after the second.

any ideas?

---

### Post by newb85 on 2013-06-30
bcmwl-kernel-source is in the restricted repository.  linux-firmware-nonfree is in the multiverse repository.  In the Software Center, open Edit>Software Sources, and on the Ubuntu Software tab, make sure you have both checked.

---

### Post by squakie on 2013-07-01
And excuse me for adding something so basic, but......

Do you have a wired connection?  You can't do those commands without being connected to the net.

If you don't have any other internet connection please post back and perhaps someone can help you in off-line mode.

---

### Post by hw2005 on 2013-07-01
So, I had the Ethernet cable plugged in, but now that I look at it, I don't think that my laptop is connected (obviously, I'm using a different computer to post on this site).  When I plug the Ethernet cable into the hp pavilion, the cone symbol in the top left corner no longer is blank, but becomes pulsing bands, which I guess indicate a connection.  However, when I try to open a website in Firefox, the program informs me that it can't find the server...so no internet.  When I right click the pulsing bands and select "edit connections", 'Wired connection 1' appears on the 'Wired' tab, but it is listed as lasted used 20min ago, which was when I first plugged the Ethernet cable in.  

If there is a way to fix the problem off-line that may be the way I need to go.  Because I installed Ubuntu, I did get on the wireless, so I know that the computer is capable.  I don't remember the last time that I got on the internet with a direct line though...so I don't know if a hardware problem is interfering with a direct connection to the web.

So, how to I go about addressing this issue in off-line mode?

---

### Post by steeldriver on 2013-07-01
I think 'last used' means when the connection last became active (not the last packets transmitted / received for instance) - so it's possible the device is working but the connection is just misconfigured - see if your ifconfig shows a valid LAN IP address

```
ifconfig
```

You can also try to ping an external site by IP - if that works, but pinging by hostname doesn't, then you have DNS problems

```
ping 173.194.43.71
```

```
ping google.com
```

It's usually easier to get the wired connection going if at all possible rather then jump straight to offline package installations

---

### Post by newb85 on 2013-07-01
> **hw2005 said:**
> When I plug the Ethernet cable into the hp pavilion, the cone symbol in the top left corner no longer is blank, but becomes pulsing bands, which I guess indicate a connection.  

Those pulsing bands do not indicate an Ethernet connection.  They indicate that your wireless is attempting to connect.  When wireless successfully connects, the bands stop pulsing and indicate the signal strength.  (Edit: This is the description of the default Ubuntu icons.  Using a different icon set or another variant of Ubuntu might result in different behavior.)

An Ethernet connection is indicated by two arrows side-by-side, one pointing up and one pointing down.

Running this will tell us more about what's going on:
```
sudo lshw -C network
```

---

### Post by hw2005 on 2013-07-02
my first reply will be for steeldriver.  my next reply will be for newb85

when I entered ifconfig with the ethernet cable plugged in, I got:

eth0      Link encap:Ethernet  HWaddr 00:0f:b0:74:70:7e
          inet6 addr: fe80::20f:b0ff:fe74:707e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:11 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:6553 (6.5 KB)


lo        Link encap:Local Loopback
        inet addr:127.0.0.1  Mask:255.0.0.0
        inet6 addr: ::1/128 Scope:Host 
        UP LOOPBACK RUNNING  MTU:16436  Metric:1 
        RX packets:16 errors:0 dropped:0 overruns:0 frame:0 
        TX packets:16 errors:0 dropped:0 overruns:0 carrier:0 
        collisions:0 txqueuelen:0 
        RX bytes:1296 (1.2 KB)  TX bytes:1296 (1.2 KB) 


ping 173.194.43.71 game me:

connect: Network is unreachable


ping google.com game me:

ping: unknown host google.com

---

### Post by hw2005 on 2013-07-02
newb85, 

with the ethnetnet cable plugged in, sudo lshw -C network gave me:

*-network:0             
       description: Network controller 
       product: BCM4306 802.11b/g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 2 
       bus info: pci@0000:03:02.0 
       version: 03 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=64 
       resources: irq:9 memory:b0204000-b0205fff 
  *-network:1 
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 6 
       bus info: pci@0000:03:06.0 
       logical name: eth0 
       version: 10 
       serial: 00:0f:b0:74:70:7e 
       size: 100Mbit/s 
       capacity: 100Mbit/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s 
       resources: irq:22 ioport:a000(size=256) memory:b020a400-b020a4ff

---

### Post by newb85 on 2013-07-02
Your Ethernet cable isn't getting you to the internet.  You'll need an internet connection before you can download anything from the online repositories.

---

### Post by Bucky Ball on 2013-07-02
*Thread moved to **Networking & Wireless**.*

---

### Post by wildmanne39 on 2013-07-02
Hi, download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
if you do not have another driver installed this should get your wireless working.
Thanks

---

