---
title: "System freeze on shutdown - wireless card RaLink"
date: 2010-11-06
forum: Networking &amp; Wireless
---

### Post by hoakerk. on 2010-11-06
Hello everyone,

I have strange behaviour on my portable computer Asus UX30. I'm using latest Ubuntu 10.10 release.
The main problem, and the most annoying, is a system freeze on shutdown, suspend, hibernate or even restart.
For a week I'm trying to find a solution on the web, but no result. From what I noticed, computer freezes when a wireless card is turned off or on.
Here are some basic info from wireless card:
```
  sudo lshw -class Network

       *-network               
       description: Wireless interface
       product: RT3091 Wireless 802.11n 1T/2R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:25:d3:3a:d3:de
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-22-generic-pae firmware=N/A ip=192.168.1.65 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:feaf0000-feafffff

```Sometimes on shutdown post screens (when system freezes) shows some strange lines related to a wireless driver. It says:
```
(...) rt2800 (...) Error - WPDMA TX/RX busy, aborting (...).
(...) Error - indirect register access failed.
```Appreciate any help,
Thank you.

---

### Post by hoakerk. on 2010-11-06
I have solved my problem. As I was thinking it was a driver issue.
```
  sudo lshw -class Network

       *-network               
       description: Wireless interface
       product:** [COLOR="Red"]RT3091[/COLOR]** Wireless 802.11n 1T/2R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:25:d3:3a:d3:de
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **[COLOR="red"]driver=rt2800pci[/COLOR] **driverversion=2.6.35-22-generic-pae firmware=N/A ip=192.168.1.65 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:feaf0000-feafffff
```
For a wireless card RaLink RT3091 the right driver is a rt2860. For a default, Ubuntu, Kubuntu and Xubuntu (which I've tryed), the driver installed is a rt2800pci. The rt2860 is installed as well, but not as a default.

The solution for this problem is very simple (thanks to a friend of mine).

**1 - Open blacklist file:**
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
Then you need to blacklist your current driver (rt2800pci).

**2 - Wright new line at the end of a file:**
```
blacklist rt2800pci
```

Save file and reboot your computer.
In my case system loaded the rt2860 driver, which is the correct one for my wireless card RaLink RT3091.

Here is a new output after reboot:
```
sudo lshw -class Network
       *-network               
       description: Wireless interface
       product: RT3091 Wireless 802.11n 1T/2R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:25:d3:3a:d3:de
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **[COLOR="Red"]driver=rt2860[/COLOR]** ip=192.168.1.65 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:17 memory:feaf0000-feafffff

```


With best regards,
hoakerk.

---

### Post by thedatamatrix on 2011-03-28
I had the same problem once I upgraded my kernel to 2.6.35-28 in maverick (64-bit) on an HP tm2t. I can verify that your solution is correct. You should file a bug report with this workaround if you haven't already. That way someone with authority may be able to fix this issue so people like me don't troll around for hours for a solution to a problem they shouldn't have on the day they receive their new computer.

Thanks!

---

### Post by RockoRobotics on 2011-05-30
I would also like to add that this work around fixed the start up issue on my Tm2t 2200 running 32 bit Natty as well as the shutdown issue mentioned above.

Prior to this fix, about 1/2 the time, my computer would not boot into Ubuntu and I would only see a black screen.  One strange indication that wireless was the issue was that the light on my wireless on/off button would rapidly flash between blue and orange.

---

### Post by hoakerk. on 2011-06-26
In my case the problem was related to wireless card, but it may be some other hardware/software that makes conflict with something. At the beginning it was a pain to find the cause of system freezing. I recommend to look into shutdown screen (F2 during shutdown), and look for a line (description) with errors at freezing point. If you find an error and a description, it's already half way to solve the problem. Hope it helps you, and other users, in some way.

---

### Post by uumpa on 2011-09-15
I have the same wireless modem in my tm2t but my issue is when I load Ubuntu my wireless turns off and I cannot get it back on unless I leave Ubuntu and go back to windows 7. is there a known problem with this or at least a fix ?I am new to the whole Linux/Ubuntu world and am a current technoligy/programing student and I'm having second thoughts as to my major though I have yet to start any of my core programing classes you would figure a month of playing around and trying to get this thing running during my free time I would have figured it out by now, but regretfully all im getting is more frustrated and determined to get this thing working and any help with the matter would be great, I have a Ralink RT3090 Wireless 802.11n 1T/1R PCIE WIFI receiver the wireless works fine with in a Win 7 boot but it turns off when Ubuntu is booted and will not turn on no matter what I try even when on USB, with-in Win 7, or on its own partition.

---

### Post by hoakerk. on 2011-10-13
Hi there,

Sorry for long delay. First thing I recommend you to do is to check your wireless driver on load (See my second post). If it shows "[COLOR="Red"]driver=rt2800pci[/COLOR]" then it is wrong one. You have to put it in black list.

All steps are described in my second post of this topic. If you do all correctly, it should work fine.

If any doubts, please don't hesitate to ask.

---

