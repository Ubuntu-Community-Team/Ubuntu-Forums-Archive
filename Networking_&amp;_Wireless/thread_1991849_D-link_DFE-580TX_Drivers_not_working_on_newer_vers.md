---
title: "D-link DFE-580TX: Drivers not working on newer versions of Ubuntu"
date: 2012-05-31
forum: Networking &amp; Wireless
---

### Post by stamati76 on 2012-05-31
Hi All,

I have a D-link dfe-580tx card.  It works perfectly fine on Ubuntu 9.10 amd64 but on newer versions of ubuntu it seems they have disabled 802.1q or dot1q.

The drivers that are installed on my Ubuntu 9.10:

lspci | grep Ethernet
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
06:04.0 Ethernet controller: D-Link System Inc DL10050 Sundance Ethernet (rev 15)
06:05.0 Ethernet controller: D-Link System Inc DL10050 Sundance Ethernet (rev 15)
06:06.0 Ethernet controller: D-Link System Inc DL10050 Sundance Ethernet (rev 15)
06:07.0 Ethernet controller: D-Link System Inc DL10050 Sundance Ethernet (rev 15)
07:04.0 Ethernet controller: D-Link System Inc DL10050 Sundance Ethernet (rev 15)
07:05.0 Ethernet controller: D-Link System Inc DL10050 Sundance Ethernet (rev 15)
07:06.0 Ethernet controller: D-Link System Inc DL10050 Sundance Ethernet (rev 15)
07:07.0 Ethernet controller: D-Link System Inc DL10050 Sundance Ethernet (rev 15)



Is there a way of enabling this within the driver?  I have enabled using modprobe but to no avail.

Please help, i hate using a defunct OS :-(

Look forward to your help.

:KS

---

### Post by chili555 on 2012-05-31
I don't know the answer, but I noticed that your post fell down quite a bit with no answer, so I'll take an educated guess. I believe your 580TX use the driver *sundance*. Please verify with:```
sudo lshw -C network
```Does it say *driver=sundance*? If so, I saw this (old) post: [http://blog.gmane.org/gmane.linux.drivers.vlan/month=20070701](http://blog.gmane.org/gmane.linux.drivers.vlan/month=20070701) It is titled **Linux 802.1Q a.k.a VLAN (Virtual LAN) kernel driver**> From what I read, I guesss the vlan on sundance is software only, and need a special MTU of 1504. Most gigabit cards (not all!) already strip the vlan tag, so the driver only sees a payload of 1500 and somewhere else in the receiver buffer the vlan tag is found. 
<snip>
I've been using vlans since 2.4.14 or so, and I have never had to set the MTU size to 1504 for any of my cards. I do know however that some of the drivers need the MTU size of 1504 to keep it from discarding it as a long packet and to cope for the increased buffer size needed.I wonder if it might help to add to your /etc/network/interfaces:```
auto eth2
iface eth2 inet static
address whatever.108
netmask 255.255.2xy.0
gateway whomever.1
[COLOR="Red"]mtu 1504[/COLOR]

```If *sundance* is not the driver or if I am on the wrong path, please feel free to advise me.

---

### Post by stamati76 on 2012-06-01
Hi There,

Thanks for replying. Yes it is a sundance driver:-

       description: Ethernet interface
       product: DL10050 Sundance Ethernet
       vendor: D-Link System Inc
       physical id: 4
       bus info: pci@0000:06:04.0
       logical name: eth1
       version: 15
       serial: 00:0d:88:68:4c:9c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sundance driverversion=1.2 duplex=full latency=64 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: irq:20 ioport:b000(size=128) memory:fba00000-fba0ffff


I have managed to upgrade to Ubuntu 10.10 and dot1q it's still working, however if i run a fresh install of Ubuntu OS it doesn't work.

In respect to the MTU size i had thought of that previously because i did a packet capture.  I changed the setting to 1900 but it still didn't allow dot1q packets through.

There is a Redhat Linux driver available on the D-link website but i'm not sure if it's possible to compile the drivers to work on Ubuntu kernel?  I'm not that proficient in Linux to be able to do that.  Besides i couldn't see a setting in the config file to include dot1q.

---

### Post by chili555 on 2012-06-01
> There is a Redhat Linux driver available on the D-link website May I please see a link.> i'm not sure if it's possible to compile the drivers to work on Ubuntu kernelIt probably is. Let's take a look.

PS - If it's this dinosaur, then my answer changes to no way, no how. [ftp://ftp.dlink.co.uk/ethernet_adapters/dfe-580tx/](ftp://ftp.dlink.co.uk/ethernet_adapters/dfe-580tx/)

We no longer use wooden spoke wheels on our sleek BMWs.

---

### Post by stamati76 on 2012-06-01
Yes they stopped making computers out of wood quite a while ago :lolflag:

What about recompiling or changing the sundance driver that is automatically loaded in the newer versions of Ubuntu?  Or extracting the sundance driver that is included in Ubuntu 9.10 and then importing it to a fresh install of Ubuntu 12.10?  Is that possible?

---

### Post by chili555 on 2012-06-01
> **stamati76 said:**
> 
What about recompiling or changing the sundance driver that is automatically loaded in the newer versions of Ubuntu? It can be done but is far beyond my area of expertise. The first step would be to find the place in the .c code you think would help. I think you'd have to install linux-source to find it. I think this is another place you could see it: [http://www.cs.fsu.edu/~baker/devices/lxr/http/source/linux/drivers/net/sundance.c](http://www.cs.fsu.edu/~baker/devices/lxr/http/source/linux/drivers/net/sundance.c)

Once you made your change, I guess you'd need to recompile the driver and then the kernel; again, far beyond the powers of the old Doc.

Isn't it feasible to junk these old-timers and replace them with cards using modern drivers that do 802.1Q? 

Hmmm. I have the source for 2.6.38 and see this in the .c code:> #if defined(CONFIG_VLAN_[COLOR="Red"]8021Q[/COLOR]) || defined(CONFIG_VLAN_8021Q_MODULE)
        iowrite16(dev->[COLOR="Red"]mtu[/COLOR] + 18, ioaddr + MaxFrameSize);It seems that MTU *is* a factor. I wonder if it's productive to experiment with MTU 1482 or 1518 or similar.

I know of no way to copy the 9.10 driver to 12.04 so that it actually works.

---

### Post by tekheretik on 2012-11-17
I have the same adapter and the same problem. Working fine in Kubuntu 11.10, be sure to install kubuntu-low-fat-settings, speeds it right up and shuts off all that snoopy indexing and search garbage. :popcorn:

Oh, and DON'T do the updates, they break the install! Just install, install low-fat (reboot after installing low-fat) and Bob's yer uncle. Go to Startup and Shutdown/Service Manager and disable Muon Updater, to avoid the nags. Nepomuk loves to complain it's been shut off too, but that goes away eventually.

---

