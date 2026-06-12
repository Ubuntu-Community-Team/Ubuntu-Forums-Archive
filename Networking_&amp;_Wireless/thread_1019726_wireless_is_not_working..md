---
title: "wireless is not working."
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by vivalaleah on 2008-12-23
I have a Compaq Presario 2200 notebook that I just put Ubuntu 8.10 on yesterday. My wireless isn't working at all on it, and internet is basically the only thing i use my laptop for, and this is extremely frustrating. I've tried several things posted here on the forums, and none of them work. When I click the physical wireless switch on my computer, nothing happens, where a blue light should come on. Wireless is the only thing that isn't working. Video, sound, etc all work without problem. 

I don't even know all the specs to my computer any more, because it is super old. Whatever the specs are, they are all default. The only modification I've made to the computer is adding RAM, which brought it up to 750, or somewhere around there. If someone could give me some simple to follow instructions, I'd love it a ton. My computer is pretty much an empty shell to me right now. Oh I have Ubuntu installed on a WD Elements 250 GB External HD. So if that has something to do with it.

---

### Post by vivalaleah on 2008-12-23
My driver even shows up in System>Administration>Hardware Drivers, it just will not activate.

---

### Post by acmariner99 on 2008-12-23
What wireless card do you have and do you have a hardwire connection.

---

### Post by Idefix82 on 2008-12-23
Let's start by finding out what wireless card you have. Please open the terminal and type in
```
lshw -C network
```
and post the output here.

---

### Post by vivalaleah on 2008-12-23
According to the Hardware Drivers list on Ubuntu, it is a Broadcom B43 driver. And no, it is completely wireless. Our router is a LinkSys of some variety.

---

### Post by acmariner99 on 2008-12-23
input sudo modprobe b43 in a terminal, then sudo /etc/init.d/networking restart

if this does not work you need to install the app fwcutter

---

### Post by vivalaleah on 2008-12-23
> **Idefix82 said:**
> Let's start by finding out what wireless card you have. Please open the terminal and type in
```
lshw -C network
```
and post the output here.

I'm typing this from my laptop screen. Since I can't copy/paste right now.

```

*-network:0
     description: Ethernet interface
     product: RTL-8139/8139C/8139C+
     vendor: Realtek Semiconductor Co., Ltd.
     physical id: 0
     bus info: pci@0000:02:00.0
     logical name: eth0
     version: 10
     serial: 00:c0:9f:60:7c:55
     width: 32 bits
     clock: 33MHz
     capabilities: bus_master cap_list ethernet physical
     configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

*-network:1
     description: Network controller
     product: BCM4306 802.11b/g Wireless LAN Controller
     vendor: Broadcom Corporation
     physical id: 6
     bus info: pci@0000:02.06.0
     version: 03
     width: 32 bits
     clock: 33MHz
     capabilites: bus_master
     configuration: driver=b43-pci-bridge latency=64 module=ssb

*-network:0 DISABLED
     description: Wireless interface
     physical id: 2
     logical name: wlan0
     serial: 00:90:4b:9c:f0:83
     capabilities: ethernet physical wireless
     configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

*-network:1 DISABLED
     description: Ethernet interface
     physical id: 3
     logical name: pan0
     serial: 06:99:d5:31:51:d5
     capabilities: ethernet physical
     configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

---

### Post by vivalaleah on 2008-12-23
> **acmariner99 said:**
> input sudo modprobe b43 in a terminal, then sudo /etc/init.d/networking restart

if this does not work you need to install the app fwcutter

Tried both, when installing b43-fwcutter, I get this

```
E: b43-fwcutter: subprocess post-installation script returned error exit status 1
```

---

### Post by Idefix82 on 2008-12-23
Thank you. One more thing: can you post the output of
```
lspci | grep BCM
```

---

### Post by acmariner99 on 2008-12-23
try sudo aptitude install b43-fwcutter, then the restart command, then load the b43 module with the modprobe and restart command above. (You may need a hardwire connection to install the application) There is an extensive thread on b43, but I cannot find it. I used it to get my wireless up and running and it worked perfectly, until it stopped working this morning.

---

### Post by vivalaleah on 2008-12-23
> **Idefix82 said:**
> Thank you. One more thing: can you post the output of
```
lspci | grep BCM
```

```
02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

---

### Post by vivalaleah on 2008-12-23
> **acmariner99 said:**
> try sudo aptitude install b43-fwcutter, then the restart command, then load the b43 module with the modprobe and restart command above. (You may need a hardwire connection to install the application) There is an extensive thread on b43, but I cannot find it. I used it to get my wireless up and running and it worked perfectly, until it stopped working this morning.

Even this returns with an error. =/

---

### Post by Idefix82 on 2008-12-23
> **vivalaleah said:**
> ```
02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

OK, let's try this:
1. make sure, you have got ndiswrapper installed.
2. Download this zip archive:
[http://myspamb8.googlepages.com/Driver_3607.zip]("http://myspamb8.googlepages.com/Driver_3607.zip")
and unzip it.
3. Change into the folder of the unzipped file, and then into the Driver/WinXP subfolder. Copy the following commands into the terminal, always providing your password when asked for it (copy them carefully with the correct capitalisation if you can't copy and paste):

```
sudo pkill NetworkManager
```
Make sure that the network manager icon in the top right corner disappeared. Then continue:
```

sudo modprobe -r b43legacy ssb
sudo ndiswrapper -i bcmwl5.inf
sudo modprobe ndiswrapper

```
now wait 10 seconds and finally do
```

NetworkManager

```
to bring back the network manager icon. Now try to connect to a wireless network.

If this works, this is how to make the solution permanent (only do it if you can connect to a network at this stage):
```
gksudo gedit /etc/modprobe.d/blacklist
```
opens a text file. Add the following lines to the end of it:
```
blacklist ssb
blacklist b43legacy
```
and save. Now do
```
gksudo gedit /etc/modules
```
which again opens a text file. Add the line
```
ndiswrapper
```
to it. Let me know how it goes. If you get any errors along the way, please post them here.

---

### Post by vivalaleah on 2008-12-23
> **Idefix82 said:**
> OK, let's try this:
1. make sure, you have got ndiswrapper installed.
2. Download this zip archive:
[http://myspamb8.googlepages.com/Driver_3607.zip]("http://myspamb8.googlepages.com/Driver_3607.zip")
and unzip it.
3. Change into the folder of the unzipped file, and then into the Driver/WinXP subfolder. Copy the following commands into the terminal, always providing your password when asked for it (copy them carefully with the correct capitalisation if you can't copy and paste):

```
sudo pkill NetworkManager
```
Make sure that the network manager icon in the top right corner disappeared. Then continue:
```

sudo modprobe -r b43legacy ssb
sudo ndiswrapper -i bcmwl5.inf
sudo modprobe ndiswrapper

```
now wait 10 seconds and finally do
```

NetworkManager

```
to bring back the network manager icon. Now try to connect to a wireless network.

If this works, this is how to make the solution permanent (only do it if you can connect to a network at this stage):
```
gksudo gedit /etc/modprobe.d/blacklist
```
opens a text file. Add the following lines to the end of it:
```
blacklist ssb
blacklist b43legacy
```
and save. Now do
```
gksudo gedit /etc/modules
```
which again opens a text file. Add the line
```
ndiswrapper
```
to it. Let me know how it goes. If you get any errors along the way, please post them here.

Upon entering "sudo ndiswrapper -i bcmwl5.inf" i get the following:
```
couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219
```

---

### Post by Idefix82 on 2008-12-23
> **vivalaleah said:**
> Upon entering "sudo ndiswrapper -i bcmwl5.inf" i get the following:
```
couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219
```

You probably weren't sitting in the right directory (this is what I meant by changing into the Driver/WinXP directory). So assuming that you downloaded the zip file onto the desktop, you open the terminal and type
```
cd ~/Desktop
unzip Driver_3607.zip
cd Driver/WinXP
sudo ndiswrapper -i bcmwl5.inf
``` 
and so on.

---

