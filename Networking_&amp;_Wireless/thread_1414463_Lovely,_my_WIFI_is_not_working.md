---
title: "Lovely, my WIFI is not working"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by greg387 on 2010-02-23
Hey Guys,
Just made the switch to Ubuntu from Windows 7. Not such a techie dude, so bear with me.

My wifi does not work (but my wired connection does). After doing some troubleshooting, I think it has to do with my laptop not having a recognized card. After typing 
 sudo pccardctl ident

I do not get any output.

According to the Ubuntu, troubleshooting wifi guide, Im supposed to  open a configuration file and add this information to it:   ( gksudo gedit /etc/pcmcia/config.opts )

  Socket 0:
    product info: "Atheros Communications, Inc.", "AR5001-0000-0000", "Wireless LAN Reference Card", "00"
    manfid: 0x0271, 0x0012
    function: 6 (network)

Where the above info is my network card. However, I dont know how to find this info.

FYI when I type lshw -C network, I get: 

*-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:62:9b:d1
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 ip=192.168.2.12 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:27 memory:fc488000-fc488fff ioport:30f8(size=8) memory:fc489c00-fc489cff memory:fc489800-fc48980f
  *-network
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:21 memory:fc000000-fc003fff memory:fc500000-fc5fffff(prefetchable)


Can someone help me out here? I am so lost, and have tried hours upon hours of troubleshooting!


Thanks guys!

Greg

---

### Post by bruno9779 on 2010-02-23
Your wifi card BCMXXX was one of the hardest wifi cards to get working in Ubuntu.

Nowadays it is fairly better, but still not straightforward.

have a look here: [http://www.bluebottle.net.au/blog/2009/broadcom-bcm4328-on-ubuntu-904-jaunty](http://www.bluebottle.net.au/blog/2009/broadcom-bcm4328-on-ubuntu-904-jaunty)

It is a mini-howto to get that card running in 9.04, ought to work in koala too.

If it doesn't post back, I managed to get one of those working before, with tinkering I am sure I could again

---

### Post by greg387 on 2010-02-23
Tried to install fwcutter and it said: "Error: Wrong architecture 'amd64'"

Even though I am running on an AMD turion X2. Thoughts?

---

### Post by Iowan on 2010-02-23
> **greg387 said:**
> Tried to install fwcutter and it said: "Error: Wrong architecture 'amd64'"
Even though I am running on an AMD turion X2. Thoughts?Drivers are still outta my league, but I'm curious if you have the 64-bit Ubuntu (AMD) installed?

---

### Post by trunkmonkeytoo on 2010-02-23
I have a similar problem, I have Ubuntu installed inside Windows 7, and cannot get wifi to work, even after installing and uninstalling, and a guide from [https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html)

Maybe this guide will help you, but it unfortunately didn't work for me.

---

### Post by greg387 on 2010-02-23
I have 32 bit.

Unfortunately, the guide didnt work.

Oh well, guess its back to Windows...

---

### Post by mörgæs on 2010-02-24
You could try Ubuntu 10.04. It is an alpha, but surprisingly stable (at least on my machine).

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by greg387 on 2010-02-24
How do i install it

---

### Post by chili555 on 2010-02-24
> Tried to install fwcutter and it said: "Error: Wrong architecture 'amd64'"When you go to the site referenced:  [http://packages.ubuntu.com/jaunty/b43-fwcutter](http://packages.ubuntu.com/jaunty/b43-fwcutter) , there are two download links: amd64 and i386. If you are running a 32-bit system, please download and install the i386 package.

---

### Post by Peter09 on 2010-02-24
Try looking for BCM in synaptic package manager, I think there is an installation for these devices in there.

---

### Post by mörgæs on 2010-02-24
> **greg387 said:**
> How do i install it

It installs like all the previous Ubuntus. You can run the live CD to test how it works on your machine, and if you like it you just install, but since there are two new advices in this thread you probably want to try them first.

---

### Post by greg387 on 2010-02-24
Still doesnt work after installing fwcutter.

---

### Post by chili555 on 2010-02-24
When you click the Network Manager icon at the top right, do you see networks? If not, please post:```
iwconfig
dmesg | grep wlan
```Thanks.

---

### Post by greg387 on 2010-02-24
The second command didnt work, but from the first command I got:
 lo     no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

### Post by chili555 on 2010-02-24
Can you see the "Broadcom STA" driver under System > Administration > Hardware Drivers? If so, is it active or not?

---

### Post by greg387 on 2010-02-24
I see it - it says this driver is activated but not currently in use.

---

### Post by chili555 on 2010-02-24
Is the wired ethernet attached? Network Manager will not allow a wireless connection if wired is available. Please detach the wire, click the Network Manager icon and tell us if you see networks.

If not, please post:```
lsmod | grep -e b43 -e wl
```Thanks.

---

### Post by bedhead75 on 2010-02-24
Try uninstalling it, and reinstalling the Broadcom STA drivers from the hardware drivers menu and then reboot.  Do this AFTER installing all of the updates first, using your wired connection.  This is what had to be done on a friend's fresh Ubuntu 9.10 install.  The first time with the wireless drivers didn't work for unknown reasons.

---

### Post by greg387 on 2010-02-24
It worked! thanks so much.

---

### Post by bedhead75 on 2010-02-24
A search online reveals that you have to re-install a certain broadcom kernel module from synaptic in order to get the drivers working.  Re-installing the drivers through the hardware drivers menu probably does the same thing...I think.

Mark as solved?

---

