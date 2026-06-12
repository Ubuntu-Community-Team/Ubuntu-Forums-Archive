---
title: "Wi Fi Speeds got slow ONLY FOR MY LAPTOP when I installed Linux"
date: 2013-04-15
forum: Networking &amp; Wireless
---

### Post by nickgee667 on 2013-04-15
It's true.  It's as simple as that.  Windows 7, perfect connection.  Even faster than my girlfriends.  Now: sitting in bed beside her (and her windows 7) and she gets a normal internet speed while mine reminds me of dial up.  Seriously.  No youtube.  Or streaming audio.  It's ridiculous.

Being an open source user, I googled my problem til I was blue in the face.  Found some suggestions for people who had similar problems, and alas, no resolution for me.

Any ideas why Ubuntu would make my wi fi so slow?  Not a hardware problem, as I stated, prior to installing linux, all was fine.

---

### Post by ahallubuntu on 2013-04-15
~

---

### Post by nickgee667 on 2013-04-16
I will add that info when I get home. 

My laptop is an emachine e442.

---

### Post by nickgee667 on 2013-04-16
Hey, I ran the commands as per the post above.  I hope this can help.  Maybe there are better drivers or something?  Still new to linux.

nick@groundzero ~ $ sudo lshw -C network
[sudo] password for nick: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 1c:75:08:ba:42:74
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 memory:d1100000-d110ffff
  *-network
       description: Wireless interface
       product: AR9287 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 18:f4:6a:65:9a:14
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-27-generic firmware=N/A ip=192.168.0.7 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d1000000-d100ffff
nick@groundzero ~ $ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"FBI Surveillance Van "  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 20:10:7A:1F:78:06   
          Bit Rate=19.5 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:82  Invalid misc:43   Missed beacon:0

---

### Post by nickgee667 on 2013-04-16
In review.  It appears there may be something up with how my network card is interpreting the rx/tx signal?

---

### Post by nickgee667 on 2013-04-18
Can anyone help me with this?

---

### Post by ahallubuntu on 2013-04-18
~

---

### Post by nickgee667 on 2013-04-19
Thanks.  I think your first suggestion regarding the hardware encryption fixed it!  I have been struggling with this for months.  Thank you so much.

Things appear faster now, but I will also try your wpa2 only fix.  Again, thank you!

---

### Post by ahallubuntu on 2013-04-19
~

---

### Post by nickgee667 on 2013-04-19
For all file stuff, I'm still not used to doing it in the command line, so in a terminal I just typed "sudo nautilus" and went to etc/modprobe.d and created an empty file and named it ath9.conf and added that line.

While in there I noticed I already had an ath5k.conf with this line already in it.  ?

---

### Post by ahallubuntu on 2013-04-19
~

---

