---
title: "USB wireless adapter"
date: 2013-01-19
forum: Networking &amp; Wireless
---

### Post by lesmey on 2013-01-19
Hi guys  I just bought a desktop which didn't come with a wireless adapter card, so I bought one of the USB wireless things..  

However the speed I have been getting is really really slow.. About 1mbps when my laptop and ps3 is getting 25mbps..  

I've tried plugging the wireless usb adapter into my laptop and i get the normal speeds.. It's really bugging me as I have no idea how to fix this, and that my desktop is a lot more powerful than my laptop but can barely load a youtube video/webpage.

---

### Post by UltimateCat on 2013-01-19
Hi: lesmey!

And Welcome to Ubuntu Forums.Org!

I had the same problem when I purchased my Desktop.

> 
However the speed I have been getting is really really slow.

If that continues you may want to give your Internet Service Provider a call and question the Representative as to what exactly is going on and why.
Ask for a Manager or a Supervisor if the Rep gives you some ridiculous answer.

You mentioned that you had to get a USB Adapter for your Desktop and your wireless to work. (I don't get why some manufacturer's don't include a NIC)
That's good but you may need a [B]driver for it.

[I][COLOR=Navy]Go to the website of the manufacturer that made your adapter and look for a driver.  Download the driver and install it on your system.

To install the driver you would use:
[/COLOR][/I][/B]
```
apt-get install <nameofdriver>

```[B][I][COLOR=Navy]

Hope this helps
[/COLOR][/I][/B]

---

### Post by Bucky Ball on 2013-01-19
> **UltimateCat said:**
> 
If that continues you may want to give your Internet Service Provider a call and question the Representative as to what exactly is going on and why.
[B][I][COLOR=Navy]
[/COLOR][/I][/B]

OP states that on another machine this dongle works faultlessly so has nothing to do with ISP and a call would be a waste of time as the problem exists at the OP's end, not at theirs.

With the dongle plugged in, please supply the output of these two commands:

```
lsusb
sudo lshw -C network
```

Also, with the dongle plugged in, do an update and then check 'Additional Drivers'. Please provide the make and model of the wireless dongle as you have omitted to in the your first post.

---

### Post by lesmey on 2013-01-19
Thanks for the quick reply guys. I'm a first time user of ubuntu and I'm really enjoying it (other than the slow internet speed part)..

lesmey@lesmey-MS-7786:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:3072 Ralink Technology, Corp. RT3072 Wireless Adapter
Bus 005 Device 002: ID 1c4f:0003 SiGma Micro HID controller
Bus 007 Device 002: ID 1a2c:0021  
lesmey@lesmey-MS-7786:~$ sudo lshw -C network
[sudo] password for lesmey: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: d4:3d:7e:37:9c:cd
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1
       logical name: wlan0
       serial: c8:3a:35:c6:94:ce
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.2.0-36-generic-pae firmware=0.29 ip=192.168.1.74 link=yes multicast=yes wireless=IEEE 802.11bgn

---

### Post by Bucky Ball on 2013-01-19
Ralink Technology, Corp. RT3072 Wireless Adapter

That's what you have.

driver=rt2800usb

That's the driver that has been installed as part of the Ubuntu kernel, thus it is working 'out of the box' but that may not be the right driver. I see no driver for the 3072 on their website:

[http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501](http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501)

... but there is one for the 3070. Hmm. Could be a clue to the speed, maybe not. How about the output of:

```
iwconfig
```Hold everything! Ah, ha. Try the answer here:

[http://askubuntu.com/questions/34742/how-do-i-get-a-d-link-dwa-140-usb-wlan-working](http://askubuntu.com/questions/34742/how-do-i-get-a-d-link-dwa-140-usb-wlan-working)

It is for a D-Link dongle but that uses the same chip as yours. I found it at post #4 on this thread:

[http://ubuntuforums.org/showthread.php?t=1565165](http://ubuntuforums.org/showthread.php?t=1565165)

Stop Press: An easier fix might be here:

[http://ubuntuforums.org/showthread.php?p=12183601](http://ubuntuforums.org/showthread.php?p=12183601)

Chilli555 is involved on both threads and is a resident networking guru around here. ;)

---

### Post by lesmey on 2013-01-19
I'm having a hard time downloading the rt2870 driver from the website (as requested in the fix that you linked)... The file is missing from the website.. Any ideas?

EDIT: Found it off google. Having a hard time following the instructions (I'm such a noob at this!)

---

### Post by lesmey on 2013-01-19
Now there's an error when I try to install the driver

It occurs when I type "make"  and "make install" into terminal.

lesmey@lesmey-MS-7786:~/Downloads/2008_0925_RT2870_Linux_STA_v1.4.0.0$ makemake -C tools
make[1]: Entering directory `/home/lesmey/Downloads/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/lesmey/Downloads/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
/home/lesmey/Downloads/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/lesmey/Downloads/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/Makefile
make  -C  /lib/modules/3.2.0-36-generic-pae/build SUBDIRS=/home/lesmey/Downloads/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-36-generic-pae'
  CC [M]  /home/lesmey/Downloads/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/lesmey/Downloads/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.o
/home/lesmey/Downloads/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c: In function ‘RTMPReadParametersHook’:
/home/lesmey/Downloads/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:928:20: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/lesmey/Downloads/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:929:20: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/lesmey/Downloads/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:930:9: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/lesmey/Downloads/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:930:24: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/lesmey/Downloads/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:1593:9: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/lesmey/Downloads/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:1594:9: error: ‘struct task_struct’ has no member named ‘fsgid’
make[2]: *** [/home/lesmey/Downloads/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.o] Error 1
make[1]: *** [_module_/home/lesmey/Downloads/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-36-generic-pae'
make: *** [LINUX] Error 2

---

### Post by lesmey on 2013-01-20
Yeah I don't have the RT2870STA installed, and I have no idea how to install it either..

I actually booted up a virtualbox windows xp and my internet speed is fine there.. Should I just give up and just install windows... Sorry if it seems like I'm whinging, it's really quite frustrating when I can't even install a driver :S

---

### Post by Elfy on 2013-01-20
Closed - OP used a different adapter.

---

### Post by Bucky Ball on 2013-01-20
You need to use:

sudo make ... etc

---

