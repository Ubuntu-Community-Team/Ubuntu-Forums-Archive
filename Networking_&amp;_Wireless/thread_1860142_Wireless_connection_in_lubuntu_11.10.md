---
title: "Wireless connection in lubuntu 11.10"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by komo on 2011-10-14
I am not new to Linux so to speak, but I am having a problem I can't solve on my own. I'm using a Dell Latitude D600 laptop with a Broadcom BCM4306 802.11b/g wireless card, and I am not able to connect to my router wirelessly .

The last time I was using Ubuntu on this laptop I just went to Start> Preferences > Additional Drivers and installed fwcutter, but this option is no longer there. I tried installing fwcutter from the synaptic package manager. Nothing, so I just uninstalled it.

I tried installing Ndiswrapper from the terminal. Nothing, so I just uninstalled it. I am not entirely sure what to do next, so I need some help solving this problem. I know you guys need more information than this, so what ever you need to help me I can get.

---

### Post by wildmanne39 on 2011-10-14
Hi, you can try what I posted in this thread in post 7.
[http://ubuntuforums.org/showthread.php?t=1859446](http://ubuntuforums.org/showthread.php?t=1859446)
Let me know if it works.
Thank you

---

### Post by komo on 2011-10-14
> **wildmanne39 said:**
> Hi, you can try what I posted in this thread in post 7.
[http://ubuntuforums.org/showthread.php?t=1859446](http://ubuntuforums.org/showthread.php?t=1859446)
Let me know if it works.
Thank you

I've got nothing, thanks for the help though.

---

### Post by wildmanne39 on 2011-10-14
Hi, please post the results of:
```
sudo lshw -C network
``` 
```
nm-tool
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
```
sudo iwlist scan
```
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wlan0| tail -n25
```
```
lsmod | grep b43
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by amjjawad on 2011-10-16
Hello komo,

I subscribed to your thread because I'm a member in LXDE and Lubuntu Team and I'm searching as always for Lubuntu Problems here on the forum.

Please feel comfortable, you are in a very capable hands :)
My friend here wildmanne will do his best to fix your issue.

I must go now but will check on your soon!

Sorry for not helping, I must go ...

---

### Post by komo on 2011-10-21
here it is, some of the codes you had me input didn't appear to run, let me know if I need to re-input them.

```
alantae@D600:~$ sudo lshw -C network
[sudo] password for alantae: 
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5702X Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:0b:db:da:da:46
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 duplex=full firmware=5702-v2.25 ip=192.168.1.105 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:11 memory:faff0000-faffffff
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
       resources: memory:fafee000-fafeffff
alantae@D600:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        00:0B:DB:DA:DA:46

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.105
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             68.105.28.11
    DNS:             68.105.29.11
    DNS:             68.105.28.12


alantae@D600:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet [14e4:16a6] (rev 02)
	Subsystem: Dell Device [1028:8126]
	Kernel driver in use: tg3
--
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
	Subsystem: Dell TrueMobile 1300 WLAN Mini-PCI Card [1028:0001]
	Kernel modules: ssb
alantae@D600:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

alantae@D600:~$ rfkill list all
The program 'rfkill' is currently not installed.  You can install it by typing:
sudo apt-get install rfkill
alantae@D600:~$ sudo apt-get install rfkill
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  python-glade2
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  rfkill
0 upgraded, 1 newly installed, 0 to remove and 11 not upgraded.
Need to get 7,806 B of archives.
After this operation, 65.5 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric/main rfkill i386 0.4-1 [7,806 B]
Fetched 7,806 B in 0s (15.0 kB/s)
Selecting previously deselected package rfkill.
(Reading database ... 92626 files and directories currently installed.)
Unpacking rfkill (from .../archives/rfkill_0.4-1_i386.deb) ...
Processing triggers for man-db ...
Setting up rfkill (0.4-1) ...
alantae@D600:~$ rfkill list all
alantae@D600:~$ lsmod
Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 bnep,rfcomm
joydev                 17393  0 
ppdev                  12849  0 
snd_intel8x0           33318  1 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
dcdbas                 14098  0 
radeon                925020  2 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39822  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  9 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73673  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
serio_raw              12990  0 
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
soundcore              12600  1 snd
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
video                  18908  0 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
drm                   192226  4 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
parport_pc             32114  1 
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
tg3                   132972  0 
alantae@D600:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

alantae@D600:~$ sudo cat /var/log/syslog | grep -e b43 -e firmware -e wlan0| tail -n25alantae@D600:~$ lsmod | grep b43
alantae@D600:~$ 

```

Have fun :popcorn:

---

### Post by wildmanne39 on 2011-10-22
Hi please run this command and watch for errors.
```
sudo apt-get install b43-fwcutter firmware-b43legacy-installer
```
Then disconnect your wired connection and restart your computer.
Thank you

---

### Post by komo on 2011-10-23
> **wildmanne39 said:**
> Hi please run this command and watch for errors.
```
sudo apt-get install b43-fwcutter firmware-b43legacy-installer
```Then disconnect your wired connection and restart your computer.
Thank you

It didn't work, thanks for the help though.

---

### Post by wildmanne39 on 2011-10-23
Hi, did you get errors when you installed the driver and firmware?
Thank you

---

### Post by sdinnel on 2011-11-24
After updating (if one can call it that now) to 11.10, my Broadcom BCM4306 802.11b/g wireless card does not work (firmware missing).  I have a Dell Latitude D610.  Does anyone have any step-by-step instructions on updating the driver for this wireless card?

---

### Post by undrline on 2011-12-19
> **sdinnel said:**
> After updating (if one can call it that now) to 11.10, my Broadcom BCM4306 802.11b/g wireless card does not work (firmware missing).  I have a Dell Latitude D610.  Does anyone have any step-by-step instructions on updating the driver for this wireless card?

Try this and see if it works for you:
[http://ubuntuforums.org/showthread.php?t=1621331](http://ubuntuforums.org/showthread.php?t=1621331)

---

### Post by traskilajussi on 2011-12-22
Running Lubuntu 11.10 on Acer 3613LMi with BCM4318 AirForce One rev 02

Having made a clean installation of Lubuntu 11.10 my wifi hasn't worked since. Tried to install driver myself and changed rights to folder lib/firmware/b43 - no success. Also, installed the fwcutter an no succes. Under 10.10 all worked fine. 8-(

---

### Post by traskilajussi on 2011-12-22
To reply to my own question. Installing firmware-b43-installer and hitting the wireless antenna button did the trick... embarassing.:D

---

### Post by wildmanne39 on 2011-12-22
Hi, I am glad it got it working.
Enjoy

---

