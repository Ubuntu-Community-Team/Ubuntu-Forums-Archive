---
title: "Setting up Wireless!"
date: 2009-10-15
forum: Networking &amp; Wireless
---

### Post by thatboyb86 on 2009-10-15
This has to be the most frustrating thing I have ever been through with a computer! I have tried everything to try to get my wireless working with ubuntu. I recently installed ubuntu on my Dell Inspiron 1545. It has a built in Dell 1397 Wlan mini-card which i have downloaded the drivers for and transferred them to Linux, and I have also copied the drivers from windows onto a disk to try to get them to work with Linux but it still wont work.I have ndiswrapper, I tried to use STA driver that was installed with Ubuntu but nothing works. It seems that the drivers I used actually makes my card recognizable, but I still cant get a connnection. Im totally new to Linux and I would like to give it a try. To me its pointless if I cant even get connected to my own router. Ive searched so many threads in the last 2 days but still no results. Can someone please help me!?

---

### Post by t0mppa on 2009-10-15
Ok, can you first post the output of **lshw -C network**? It will show the state of your wireless interface, its drivers and what chip your wireless card is using.

---

### Post by thatboyb86 on 2009-10-15
Im not sure about the chipset, I just see (0c:00.0) Broadcom Corporation BCM4312, 802.11b/g [14e4:4315]
Here is the output of lshw -C network:


WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:18:9b:81
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.1.4 latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 8a:7c:75:40:95:47
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by t0mppa on 2009-10-15
Ok, unclaimed means that no drivers are getting associated with it for the moment.

The simplest way to install a driver for the chip should be by going to System / Administration / Hardware Drivers and activating the Broadcom STA from there. Or compiling it manually, if that's your thing, the source is on [Broadcom's website]("http://www.broadcom.com/support/802.11/linux_sta.php"). But from your first post, it appears as though you've tried that one already without much luck.

Another option is the b43 (allows master mode, packet injection, etc. unlike the STA), which needs some extra details for this chip. [Here]("http://ubuntuforums.org/showthread.php?t=1266620")'s a nice little thread about that one.

---

### Post by thatboyb86 on 2009-10-15
Thank you for the link to that tutorial. Like you said I have tried to go to Broadcoms site to use the STA driver but it didnt work. Now that I went through the steps of the tutorial you had posted the NIC is no longer "unclaimed", but still no connection:


  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:24:2b:68:97:c3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl3 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:18:9b:81
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 26:cf:c4:be:51:91
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by t0mppa on 2009-10-15
Ironically the focus of that tutorial was to unload the STA (driver module named wl) and switch to b43 instead and following it, you managed to turn your interface from unclaimed to associated with STA.

How does the STA not work for you? Could it pick up networks on a scan? Try to connect to networks, but return to ask for a password, even if you supplied the right one? Connect to networks, but can't browse the Internet on your browser?

As for trying out b43, try running ```
sudo modprobe -r wl b43
sudo modprobe b43
``` to first unload both modules and then load only the b43 to see if it will work that way.

---

### Post by thatboyb86 on 2009-10-15
I tried to use the STA driver but even when it is active I have a red "X" by my network signal. I cant run a scan and it wont pick up anything at all even with me sitting right next to router.It says there are no networks. This is what I got from what you told me to do.

brandon@brandon-laptop:~$ sudo modprobe -r wl b43
[sudo] password for brandon: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
brandon@brandon-laptop:~$ sudo modprobe b43
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

---

### Post by thatboyb86 on 2009-10-16
Anybody out there!? lol

---

### Post by SydneyGB on 2009-10-16
I too am the new owner of an Inspiron 1545 and have not had luck setting up wireless.  I'm running the LiveCD so far, but plan to install Ubuntu as a dual boot with Vista.  Possibly this weekend I'll be working on it, but you're not alone out there, thatboy!

---

### Post by t0mppa on 2009-10-17
Sorry, was busy yesterday. Anyway, those are just warnings, like you can see, if you read the text. They're telling you that the files in said directory need to be given *.conf* extension for them to work in *future* versions of Ubuntu, but that they work perfectly well for now.

Also, since the default blacklist file on Jaunty is */etc/modprobe.d/blacklist.conf*, did you create the one without the *.conf* extension as a result of some tutorial? Should check what's inside there, since if it's blacklisting all other drivers than say ndiswrapper, that'd explain why your wireless was unclaimed to begin with.

Thus, after running the two modprobes, you should check with *lshw* to see if the wireless gets associated with b43 instead and then see if that one manages to do a scan with **sudo iwlist scanning**.

---

