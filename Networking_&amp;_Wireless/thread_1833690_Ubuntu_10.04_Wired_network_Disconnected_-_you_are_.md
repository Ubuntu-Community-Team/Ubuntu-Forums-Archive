---
title: "Ubuntu 10.04 Wired network Disconnected - you are now offline"
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by gopaleen on 2011-08-26
Hi, I just installed Ubuntu 10.04, complete noob, but I can't connect to the internet. I connect the ethernet cable, select auto ethernet and the icon animates for about 30 seconds. But then I get a notification "Wired network Disconnected - you are now offline".

Don't know what other information I should provide. I tried a few things from different posts like editing the dhcpclient.config but don't really know what I'm doing and none of these worked anyways. I'm not even sure if they were solutions to a similar problem!  

I'm using the same connection on my Mac OS 10.4.11 (different machine) and I have no problems. Could I use these same settiings in Ubuntu? I don't know what the different fields represent or what I should input in manual settings.

Help!

---

### Post by praseodym on 2011-08-26
Hello,

can you post the following terminal outputs:

```
lspci -nnk | grep -iA2 net
cat /etc/network/interfaces
cat /etc/resolv.conf
ifconfig -a
lsmod
```
Do you have a router + modem or a single DSL-modem?

---

### Post by gopaleen on 2011-08-26
I have a router and modem

```

:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Kernel driver in use: ath9k
    Kernel modules: ath9k
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Kernel driver in use: r8169
    Kernel modules: r8169
:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

:~$ cat /etc/resolv.conf
: No such file or directory
:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr f0:de:f1:4b:40:86  
          inet6 addr: fe80::f2de:f1ff:fe4b:4086/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10953 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:664755 (664.7 KB)  TX bytes:4698 (4.6 KB)
          Interrupt:27 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)

pan0      Link encap:Ethernet  HWaddr 72:b7:09:a1:47:b9  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 68:a3:c4:40:70:ab  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

:~$ lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
rfcomm                 40393  4 
ppdev                   6375  0 
sco                     9649  2 
bridge                 53152  0 
stp                     2171  1 bridge
bnep                   11884  2 
l2cap                  34807  16 rfcomm,bnep
snd_hda_codec_realtek   279008  1 
joydev                 11104  0 
snd_hda_intel          25805  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
arc4                    1473  2 
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fbcon                  39270  71 
snd_timer              23649  2 snd_pcm,snd_seq
tileblit                2487  1 fbcon
font                    8053  1 fbcon
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath9k                 329085  0 
psmouse                65040  0 
mac80211              238896  1 ath9k
bitblit                 5811  1 fbcon
ath                     9723  1 ath9k
uvcvideo               62851  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
btusb                  13097  2 
v4l2_compat_ioctl32    11892  1 videodev
softcursor              1565  1 bitblit
bluetooth              58685  9 rfcomm,sco,bnep,l2cap,btusb
snd                    71283  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               4918  0 
cfg80211              148341  3 ath9k,mac80211,ath
led_class               3764  1 ath9k
video                  20623  0 
output                  2503  1 video
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
vga16fb                12757  1 
vgastate                9857  1 vga16fb
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   38030  2 
r8169                  39714  0 
mii                     5237  1 r8169

```

---

### Post by praseodym on 2011-08-26
Does your wireless work for some installation? Driver r8169 causes some problems with device [10ec:8168]. Installation procedure [here]("http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217")

---

### Post by Actonix on 2011-08-26
> **gopaleen said:**
> Hi, I just installed Ubuntu 10.04, complete noob, but I can't connect to the internet. I connect the ethernet cable, select auto ethernet and the icon animates for about 30 seconds. But then I get a notification "Wired network Disconnected - you are now offline".

Don't know what other information I should provide. I tried a few things from different posts like editing the dhcpclient.config but don't really know what I'm doing and none of these worked anyways. I'm not even sure if they were solutions to a similar problem!  

I'm using the same connection on my Mac OS 10.4.11 (different machine) and I have no problems. Could I use these same settiings in Ubuntu? I don't know what the different fields represent or what I should input in manual settings.

Help!

Well, do you know how your Router is setup ?

Are you running DHCP or do you use a static IP address

or to put the question slightly differently, how did you connect to the internet on your Mac, did you have to input settings via the Network Pane and do you have those settings to hand - no need to tell me what they specifically are just that you know them

---

### Post by gopaleen on 2011-08-26
I don't know how the router is setup. In Mac in network settings under Built-in Ethernet it says configure IPv4: DHCP and I have an IP address, Subnet Mask and Router IP. I have an IPv6 MAC address as well I think. This was all automatically inputted, I didn't enter anything myself. 

Praseodym, I tried to install the r8169 driver but it threw out an error: 
```
package build essential is not available, but is referred to by another package... 
E: Package build-essential has no installation candidate
```

---

### Post by gopaleen on 2011-08-27
I don't have wireless on either machine. I pasted the code (for driver r8169) into terminal again and I got the following

> 
:~$ wget [http://r8168.googlecode.com/files/r8168-8.024.00.tar.bz2](http://r8168.googlecode.com/files/r8168-8.024.00.tar.bz2) 
--2011-08-27 23:37:15--  [http://r8168.googlecode.com/files/r8168-8.024.00.tar.bz2](http://r8168.googlecode.com/files/r8168-8.024.00.tar.bz2) 
Resolving r8168.googlecode.com... failed: Name or service not known. 
wget: unable to resolve host address `r8168.googlecode.com' 
:~$ tar xvf r8168-8.024.00.tar.bz2 
tar: r8168-8.024.00.tar.bz2: Cannot open: No such file or directory 
tar: Error is not recoverable: exiting now 
:~$ cd r8168-8.024.00 
bash: cd: r8168-8.024.00: No such file or directory 
:~$ sudo ./autorun.sh 
sudo: ./autorun.sh: command not found 
:~$ echo 'blacklist r8169' | sudo tee -a /etc/modprobe.d/blacklist.conf 
blacklist r8169 
:~$ sudo modprobe -rf r8169 
:~$ sudo modprobe -v r8168 
FATAL: Module r8168 not found. 
:~$ sudo depmod -a 

:~$ sudo update-initramfs -u 
update-initramfs: Generating /boot/initrd.img-2.6.32-33-generic 


And when I rebooted the system there are no wired networks available. When I click on the icon I just have Wireless Networks greyed out and VPN Connections.

---

### Post by gopaleen on 2011-08-27
I'm sorry, I was being very dense there. Downloaded the drivers and pasted the code into terminal:

> :~$ sudo apt-get install --reinstall linux-headers-generic build-essential
[sudo] password for : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate
:~$ sudo apt-get install --reinstall linux-headers-generic build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate
:~$ tar xvf /home//Downloads/r8168-8.024.00.tar.bz2tar: Record size = 8 blocks
r8168-8.024.00/
r8168-8.024.00/Makefile
r8168-8.024.00/src/
r8168-8.024.00/src/Makefile
r8168-8.024.00/src/r8168_asf.h
r8168-8.024.00/src/rtl_eeprom.c
r8168-8.024.00/src/r8168.h
r8168-8.024.00/src/r8168_n.c
r8168-8.024.00/src/r8168_asf.c
r8168-8.024.00/src/rtl_eeprom.h
r8168-8.024.00/src/rtltool.h
r8168-8.024.00/src/rtltool.c
r8168-8.024.00/src/Makefile_linux24x
r8168-8.024.00/README
r8168-8.024.00/autorun.sh
:~$ cd r8168-8.024.00
:~/r8168-8.024.00$ sudo ./autorun.sh

Check old driver and unload it.
rmmod r8168
Build the module and install
[: 48: r8168: unexpected operator
Depending module. Please wait.
load module r8168
Completed.
:~/r8168-8.024.00$ echo 'blacklist r8169' | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist r8169
:~/r8168-8.024.00$ sudo modprobe -rf r8169
FATAL: Module r8169 not found.
:~/r8168-8.024.00$ sudo modprobe -v r8168
:~/r8168-8.024.00$ sudo depmod -a
:~/r8168-8.024.00$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.32-33-generic
:~/r8168-8.024.00$ 


Same problem as before after reboot, "wired network disconnected - you are now offline".

---

### Post by praseodym on 2011-08-27
Please show:

```
cat /var/lib/NetworkManager/NetworkManager.state
ifconfig -a
lsmod
dmesg | egrep 'r8|eth0'
cat /etc/NetworkManager/nm-system-settings.conf
```

---

### Post by gopaleen on 2011-08-27
Here it is:
> :~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr f0:de:f1:4b:40:86  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

pan0      Link encap:Ethernet  HWaddr 8e:d1:5c:91:54:a0  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 68:a3:c4:40:70:ab  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10866  1 
fat                    55350  1 vfat
usb_storage            50377  1 
binfmt_misc             7960  1 
ppdev                   6375  0 
rfcomm                 40393  4 
sco                     9649  2 
bridge                 53152  0 
stp                     2171  1 bridge
bnep                   11884  2 
l2cap                  34807  16 rfcomm,bnep
snd_hda_codec_realtek   279008  1 
joydev                 11104  0 
snd_hda_intel          25805  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
r8168                 186702  0 
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
arc4                    1473  2 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath9k                 329085  0 
btusb                  13097  2 
bluetooth              58685  9 rfcomm,sco,bnep,l2cap,btusb
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
snd                    71283  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
softcursor              1565  1 bitblit
uvcvideo               62851  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
video                  20623  0 
output                  2503  1 video
mac80211              238896  1 ath9k
ath                     9723  1 ath9k
psmouse                65040  0 
serio_raw               4918  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
cfg80211              148341  3 ath9k,mac80211,ath
led_class               3764  1 ath9k
vga16fb                12757  1 
vgastate                9857  1 vga16fb
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   38030  2 
:~$ dmesg | egrep 'r8|eth0'
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91864 r8192 d22824 u262144
[    0.000000] pcpu-alloc: s91864 r8192 d22824 u262144 alloc=1*2097152
[   11.696446] r8168 Gigabit Ethernet driver 8.024.00-NAPI loaded
[   11.696495] r8168 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   11.696568] r8168 0000:03:00.0: setting latency timer to 64
[   11.696808] r8168 0000:03:00.0: irq 28 for MSI/MSI-X
[   11.847258] r8168: This product is covered by one or more of the following patents: US5,307,459, US5,434,872, US5,732,094, US6,570,884, US6,115,776, and US6,327,625.
[   11.847261] eth0: Identified chip type is 'RTL8168E/8111E'.
[   11.847263] r8168  Copyright (C) 2011  Realtek NIC software team <nicfae@realtek.com> 
[   12.382590] r8168: eth0: link down
[   12.383236] ADDRCONF(NETDEV_UP): eth0: link is not ready
:~$ cat /etc/NetworkManager/nm-system-settings.conf
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

no-auto-default=f0:de:f1:4b:40:86,

[ifupdown]
managed=false

:~$ 


---

### Post by praseodym on 2011-08-27
Did you check the cable?

---

### Post by gopaleen on 2011-08-27
Sorry! Didn't have the cable connected!

> :~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr f0:de:f1:4b:40:86  
          inet6 addr: fe80::f2de:f1ff:fe4b:4086/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7980 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:484248 (484.2 KB)  TX bytes:2178 (2.1 KB)
          Interrupt:28 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5600 (5.6 KB)  TX bytes:5600 (5.6 KB)

pan0      Link encap:Ethernet  HWaddr 8e:d1:5c:91:54:a0  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 68:a3:c4:40:70:ab  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10866  1 
fat                    55350  1 vfat
usb_storage            50377  1 
binfmt_misc             7960  1 
ppdev                   6375  0 
rfcomm                 40393  4 
sco                     9649  2 
bridge                 53152  0 
stp                     2171  1 bridge
bnep                   11884  2 
l2cap                  34807  16 rfcomm,bnep
snd_hda_codec_realtek   279008  1 
joydev                 11104  0 
snd_hda_intel          25805  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
r8168                 186702  0 
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
arc4                    1473  2 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath9k                 329085  0 
btusb                  13097  2 
bluetooth              58685  9 rfcomm,sco,bnep,l2cap,btusb
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
snd                    71283  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
softcursor              1565  1 bitblit
uvcvideo               62851  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
video                  20623  0 
output                  2503  1 video
mac80211              238896  1 ath9k
ath                     9723  1 ath9k
psmouse                65040  0 
serio_raw               4918  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
cfg80211              148341  3 ath9k,mac80211,ath
led_class               3764  1 ath9k
vga16fb                12757  1 
vgastate                9857  1 vga16fb
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   38030  2 
:~$ dmesg | egrep 'r8|eth0'
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91864 r8192 d22824 u262144
[    0.000000] pcpu-alloc: s91864 r8192 d22824 u262144 alloc=1*2097152
[   11.696446] r8168 Gigabit Ethernet driver 8.024.00-NAPI loaded
[   11.696495] r8168 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   11.696568] r8168 0000:03:00.0: setting latency timer to 64
[   11.696808] r8168 0000:03:00.0: irq 28 for MSI/MSI-X
[   11.847258] r8168: This product is covered by one or more of the following patents: US5,307,459, US5,434,872, US5,732,094, US6,570,884, US6,115,776, and US6,327,625.
[   11.847261] eth0: Identified chip type is 'RTL8168E/8111E'.
[   11.847263] r8168  Copyright (C) 2011  Realtek NIC software team <nicfae@realtek.com> 
[   12.382590] r8168: eth0: link down
[   12.383236] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4985.377469] r8168: eth0: link up
[ 4985.378969] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 4985.893102] r8168: eth0: link up
[ 4995.688995] eth0: no IPv6 routers present
:~$ cat /etc/NetworkManager/nm-system-settings.conf
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

no-auto-default=f0:de:f1:4b:40:86,

[ifupdown]
managed=false




---

### Post by praseodym on 2011-08-27
Does

```
route -n
cat /etc/resolv.conf
```
show you the router-IP adress? Can you ping?

```
ping -c 4 Your.Router.IP.Adress [COLOR="Red"]#replace with yours[/COLOR]
ping -c 4 8.8.4.4
ping -c 4 213.95.41.11

```

---

### Post by gopaleen on 2011-08-27
resolv.conf no such file or directory!
> :~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
:~$ 
:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: No such file or directory


---

### Post by praseodym on 2011-08-27
No nameservers specified. Try:

```
echo "nameserver 8.8.8.8" | sudo tee -a /etc/resolv.conf
echo "nameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo dhclient eth0
sudo service network-manager restart
```
Control:

```
ifconfig -a
cat /etc/network/interfaces
route -n
```

---

### Post by gopaleen on 2011-08-27
Ok
> :~$ echo "nameserver 8.8.8.8" | sudo tee -a /etc/resolv.conf
nameserver 8.8.8.8
:~$ echo "nameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
nameserver 8.8.4.4
:~$ sudo dhclient eth0
internet systems consortium dhcp client v3.1.3
copyright 2004-2009 internet systems consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

listening on lpf/eth0/f0:de:f1:4b:40:86
sending on   lpf/eth0/f0:de:f1:4b:40:86
sending on   socket/fallback
dhcpdiscover on eth0 to 255.255.255.255 port 67 interval 8
dhcpdiscover on eth0 to 255.255.255.255 port 67 interval 8
dhcpdiscover on eth0 to 255.255.255.255 port 67 interval 17
dhcpdiscover on eth0 to 255.255.255.255 port 67 interval 9
dhcpdiscover on eth0 to 255.255.255.255 port 67 interval 15
dhcpdiscover on eth0 to 255.255.255.255 port 67 interval 4
no dhcpoffers received.
No working leases in persistent database - sleeping.
:~$ sudo service network-manager restart
network-manager start/running, process 1628
:~$ ifconfig -a
eth0      link encap:ethernet  hwaddr f0:de:f1:4b:40:86  
          inet6 addr: Fe80::f2de:f1ff:fe4b:4086/64 scope:link
          up broadcast running multicast  mtu:1500  metric:1
          rx packets:10220 errors:0 dropped:0 overruns:0 frame:0
          tx packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          rx bytes:615812 (615.8 kb)  tx bytes:7287 (7.2 kb)
          interrupt:28 base address:0x4000 

lo        link encap:local loopback  
          inet addr:127.0.0.1  mask:255.0.0.0
          inet6 addr: ::1/128 scope:host
          up loopback running  mtu:16436  metric:1
          rx packets:76 errors:0 dropped:0 overruns:0 frame:0
          tx packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          rx bytes:5840 (5.8 kb)  tx bytes:5840 (5.8 kb)

pan0      link encap:ethernet  hwaddr 5a:1b:a0:8b:99:b5  
          broadcast multicast  mtu:1500  metric:1
          rx packets:0 errors:0 dropped:0 overruns:0 frame:0
          tx packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          rx bytes:0 (0.0 b)  tx bytes:0 (0.0 b)

wlan0     link encap:ethernet  hwaddr 68:a3:c4:40:70:ab  
          broadcast multicast  mtu:1500  metric:1
          rx packets:0 errors:0 dropped:0 overruns:0 frame:0
          tx packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          rx bytes:0 (0.0 b)  tx bytes:0 (0.0 b)

:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

:~$ route -n
kernel ip routing table
destination     gateway         genmask         flags metric ref    use iface
:~$ cat /etc/resolv.conf
nameserver 8.8.8.8
nameserver 8.8.8.8
nameserver 8.8.4.4
:~$ ping -c 4 8.8.8.8
connect: Network is unreachable
:~$ 
:~$ ping -c 4 8.8.4.4
connect: Network is unreachable
:~$ 
:~$ ping -c 4 213.95.41.11
connect: Network is unreachable


---

### Post by praseodym on 2011-08-27
Hmmm,

checkbox _all_ user rights in "Users&Groups" and login again. Afterwards remove all your profiles in "Wired" and "DSL" in the network-manager applet and reboot.

---

### Post by gopaleen on 2011-08-27
Done. Still the same problem.

---

### Post by gopaleen on 2011-08-29
It's working! Thanks a million praseodym! Really appreciate it.

I restarted my router and voila, I was connected. Should've done this before,, sorry about that. Vielen dank nochmal, especially for your patience.

---

### Post by billaboy on 2012-04-12
I am completely noob using ubuntu...
I have installed ubuntu 11.10...
but jst donno how to use it...
but the major problem I have is that I can't use Internet...

it constantly shows me error stating "Wired Network Disconnected - You are now Offline"

I am using only the modem & cable wired connection..
& connect through broadband connection (with using only username & password) in windows...

I just want to know how can I enable internet access on linux using these information....



please help me asap....
I'm very curious to the replies....

---

### Post by praseodym on 2012-04-12
Hi,

open the network-manager via terminal (CTRL+ALT+T)
```
gksu nm-connection-editor
```
and add these infos to the "DSL" section.

---

