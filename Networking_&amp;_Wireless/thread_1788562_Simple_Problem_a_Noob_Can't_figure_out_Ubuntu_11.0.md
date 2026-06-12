---
title: "Simple Problem a Noob Can't figure out Ubuntu 11.04"
date: 2011-06-22
forum: Networking &amp; Wireless
---

### Post by helphelphelp! on 2011-06-22
So I've forgotten any of the processes i had to use for 10.10 on how to activate the wireless internet after a fresh install. I've looked at some the guides but i feel like im reading an ancient language, can anyone help?

---

### Post by MooPi on 2011-06-22
What type of adapter do you have ?
Can you give us the results of this command from terminal ?
```
ifconfig
``` 
```
sudo lshw -C network
```
Those should show us the type and possibly if it is recognized already

---

### Post by helphelphelp! on 2011-06-24
> **MooPi said:**
> What type of adapter do you have ?
Can you give us the results of this command from terminal ?
```
ifconfig
``` 

```
 funkman13@funkman13-Latitude-D530:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:70:7a:b1:42  
          inet6 addr: fe80::221:70ff:fe7a:b142/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1326 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1356570 (1.3 MB)  TX bytes:161346 (161.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5080 (5.0 KB)  TX bytes:5080 (5.0 KB)

```

> ```
sudo lshw -C network
```
Those should show us the type and possibly if it is recognized already
```
 funkman13@funkman13-Latitude-D530:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:7a:b1:42
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5755m-v3.32 latency=0 link=no multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 memory:fe7f0000-fe7fffff

```

---

### Post by nm_geo on 2011-06-24
Two more commands and we are on the way

```
lspci -nn
```

```
lsmod
```

I think you will find your wireless driver is incorrect or not installed.  We can fix that.

---

### Post by jsgosselin on 2011-06-24
Hi, 

It appears you have a BCM4311 wireless card, but do not have the drivers installed or loaded to run it. You need to have proprietary drivers installed in order for your card to run. You can install/activate this driver from the Additional Drivers feature in Ubuntu.

I would suggest you this wiki to help you solve your problem:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by nm_geo on 2011-06-24
helphelphelp!

The addtional driver recommended in Natty is the STA driver unless things have changed in the last few weeks it will not work for your chipset.

Now with that being said if you activated the STA driver ; deactivate it and  install the following:

[B]b43-fwcutter
firmware-b43-installer[/B]

You can do it from Synaptic or command line:

Then the results from the terminal commands would help.

```
lsmod
``````
sudo lshw -C network
``````
rfkill list all
```

---

### Post by helphelphelp! on 2011-06-24
> **nm_geo said:**
> helphelphelp!

The addtional driver recommended in Natty is the STA driver unless things have changed in the last few weeks it will not work for your chipset.

Now with that being said if you activated the STA driver ; deactivate it and  install the following:

[B]b43-fwcutter
firmware-b43-installer[/B] 

Okay. Installed


>  You can do it from Synaptic or command line:

Then the results from the terminal commands would help.

```
lsmod
``` 

```
 funkman13@funkman13-Latitude-D530:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
03:01.0 CardBus bridge [0607]: O2 Micro, Inc. Cardbus bridge [1217:7135] (rev 21)
03:01.4 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01) 
```



> ```
sudo lshw -C network
``` 

```
 funkman13@funkman13-Latitude-D530:~$ sudo lshw -C network
[sudo] password for funkman13: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:7a:b1:42
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5755m-v3.32 ip=192.168.1.141 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 memory:fe7f0000-fe7fffff 
```


>  ```
rfkill list all
``` 

```
 funkman13@funkman13-Latitude-D530:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by nm_geo on 2011-06-24
I think we have some blacklist issues ..  Maybe

```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl
```'

Paste result

---

### Post by superduperlinuxperson on 2011-06-24
the best guide to internet on ubunut b43: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by nm_geo on 2011-06-24
do 

```
sudo modprobe b43
```

If that gets things going we probably have a blacklist issue. 

Gotta go for now ..

---

### Post by helphelphelp! on 2011-06-24
> **nm_geo said:**
> do 

```
sudo modprobe b43
```

If that gets things going we probably have a blacklist issue. 

Gotta go for now ..

That did the trick! thank you so much

---

### Post by nm_geo on 2011-06-24
> **helphelphelp! said:**
> That did the trick! thank you so much

If you reboot and have problems with the wireless you can run the modprobe b43 command and it should work.  However a more elegant approach would be to fix the blacklist problem if it exists.

Run this code

```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl
```'

If you see blacklist b43 or blacklist ssb ... We can fix it..

```
gksudo gedit /etc/modprobe.d/*
```Will get you where the blacklist files are located.  Simply put a # sign in front of the blacklist b43 line and save the file. You should have no problems.

---

### Post by helphelphelp! on 2011-06-26
> **nm_geo said:**
> If you reboot and have problems with the wireless you can run the modprobe b43 command and it should work.  However a more elegant approach would be to fix the blacklist problem if it exists.

Run this code

```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl
```'

If you see blacklist b43 or blacklist ssb ... We can fix it..

```
gksudo gedit /etc/modprobe.d/*
```Will get you where the blacklist files are located.  Simply put a # sign in front of the blacklist b43 line and save the file. You should have no problems.

I ran the last code and i got this

```
 # autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
```

anyway you could correct anything wrong with it for me? I really am very limited in the language and i don't want to mess anything up further

---

### Post by nm_geo on 2011-06-26
Something was not correct in that output. Are you still able to connect wireless on each new reboot?

---

### Post by helphelphelp! on 2011-06-26
> **nm_geo said:**
> Something was not correct in that output. Are you still able to connect wireless on each new reboot?

no im not i have to run the modprobe command everytime

---

### Post by nm_geo on 2011-06-26
> **helphelphelp! said:**
> no im not i have to run the modprobe command everytime

Okay we can fix that too.

Let's do it graphically 

```
gksudo gedit /etc/modprobe.d/blacklist-bcm43.conf
```Where you see blacklist b43 add the # sign in front ..
Example # blacklist b43
Also where you see blacklist ssb add the # sign in front..
Example # blacklist ssb

Then save the file.. And reboot.. All should be done..

Explanation; The STA (wl) driver creates the blacklist-bcm43.conf file when you tried to use the STA (wl) driver, and it automatically blacklist b43 and ssb with the automatic file.
You have to be root (sudo or su) to modify the blacklist files, and we will use gedit (text editor) to do that.
We could also remove the file but this is just as easy.

Try that , reboot and let us know..

---

### Post by josephmills on 2011-06-26
> **nm_geo said:**
> Okay we can fix that too.

Let's do it graphically 

```
gksudo gedit /etc/modprobe.d/blacklist-bcm43.conf
```Where you see blacklist b43 add the # sign in front ..
Example # blacklist b43
Also where you see blacklist ssb add the # sign in front..
Example # blacklist ssb

Then save the file.. And reboot.. All should be done..

Explanation; The STA (wl) driver creates the blacklist-bcm43.conf file when you tried to use the STA (wl) driver, and it automatically blacklist b43 and ssb with the automatic file.
You have to be root (sudo or su) to modify the blacklist files, and we will use gedit (text editor) to do that.
We could also remove the file but this is just as easy.

Try that , reboot and let us know..

nm_geo check your pms

---

