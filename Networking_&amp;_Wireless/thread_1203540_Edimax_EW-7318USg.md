---
title: "Edimax EW-7318USg"
date: 2009-07-03
forum: Networking &amp; Wireless
---

### Post by caseyb on 2009-07-03
I'm trying to get an Edimax EW-7318USg working on my system.  I searched online to make sure it worked well with Linux before purchasing it (says it should work "out of the box" [here]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax#USB")), and now I'm thoroughly frustrated with it. When I plug it in, nothing happens, NetworkManager does nothing with it. So off to find the source, try to compile and install it, and I can't get it to work.

First, I tried following these instructions: [http://ubuntuforums.org/showthread.php?t=836577](http://ubuntuforums.org/showthread.php?t=836577)
But then I couldn't find the driver source (as linked to in the thread), so looked around for different instructions.

Next, I tried following these instructions: [https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29")
I downloaded the "RT2501USB(RT73:RT2571W/RT2573/RT2671" driver ([here]("http://www.ralink.com.tw/Home/Support/Linux.html")) and got down to the spot of running "sudo modprobe rt73", at which point my computer froze. Now if the Edimax is plugged into the USB port, my computer will either not boot or instantly freeze. (UPDATE: Decided to do a clean reinstall of Ubuntu.)

Help?

---

### Post by glug101 on 2009-07-03
Couple of crazy ideas that might make a difference:

The link you listed lists Ubuntu Intrepid and WEP specifically.  I don't know why WPA might not work, or if you are using an older version of Ubuntu, but it might be something to think about if you get more desperate later:)

Second, having the computer hang like that while doing a modprobe makes me think either hardware problem, or crappy drivers.  If you have the option, try connecting to a different USB port.  

Sounds like snake oil, but it's all I can come up with off the top of my head.  If I think of anything later I'll call or post:)

---

### Post by carroll.ray on 2009-07-03
I'm having similar difficulty with the same adapter.  I've installed the adapter on my Win XP Pro machine with no problems, so the adapter **can** be found.  It just isn't found by my Toshiba 1415-S173 laptop running Jaunty Jackalope 9.04

---

### Post by caseyb on 2009-07-03
After a clean reinstall of Ubuntu, I gave it another shot. This time I tried using the driver source code included on the CD out of the box the adapter came in.  For reference, this is the filename of the driver it shipped with:  2008_0506_RT73_Linux_STA_Drv1.1.0.1.tar.bz2

So I tried to configure it for making, but it needed the kernel source. So I did:
```
sudo apt-get install linux-headers-`uname -r`
sudo apt-get source linux-image-`uname -r`
sudo mkdir /usr/src/linux-2.6.28
sudo cp -r linux-2.6.28/* /usr/src/linux-2.6.28/
```That seemed to work, even though "uname -r" yields for me "2.6.28-13-generic". I don't know if there's a difference between linux-2.6.28 and 2.6.28-13-generic, even though the apt-get command I ran asked for the more specific source.

The make config didn't error out this time, but when I attempted to compile it wasn't happy:
```
queso@quark:~/dl/drivers/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module$ make config


-------------------- Ralink RT73 Station Configuration -------------------- 

  Linux kernel source directory [/usr/src/linux-2.6.28-13-generic]: /usr/src/linux-2.6.28
 
  Linux kernel source directory : /usr/src/linux-2.6.28
 
  Module install directory : /lib/modules/2.6.28-13-generic/kernel/drivers/net
 
queso@quark:~/dl/drivers/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module$ make all
make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/queso/dl/drivers/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  CC [M]  /home/queso/dl/drivers/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module/rtmp_main.o
/home/queso/dl/drivers/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module/rtmp_main.c: In function ‘usb_rtusb_close_device’:
/home/queso/dl/drivers/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module/rtmp_main.c:443: error: implicit declaration of function ‘kill_proc’
make[2]: *** [/home/queso/dl/drivers/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/queso/dl/drivers/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make: *** [all] Error 2
queso@quark:~/dl/drivers/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module$ 
```Any ideas? :-k

---

### Post by caseyb on 2009-07-04
In accordance with [this thread]("http://ubuntuforums.org/showthread.php?p=6183681"), I'm posting additional info about my system in case it helps:

**1 ) Machine Brand and Model (PC/Laptop)**:

Self-built desktop, Intel Core2 Quad Q8300 @ 2.50GHz, ASUS P5N7A-VM motherboard

**2 ) Wireless Brand, Model and Wireless Chipset:**

lsusb:
```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c526 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 04fe:0006 PFU, Ltd 
Bus 003 Device 002: ID 04fe:0008 PFU, Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 7392:7318  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```I think "Bus 001 Device 002: ID 7392:7318" is the wireless usb, since when I take it out it changes to Linux Foundation root hub.

**3 ) check interface:**

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

virbr0    no wireless extensions.

pan0      no wireless extensions.
```**4 ) Check for modules:**

lsmod:
```
Module                  Size  Used by
isofs                  43688  0 
udf                    92584  0 
crc_itu_t              10496  1 udf
binfmt_misc            18572  1 
bnep                   22912  2 
ipt_MASQUERADE         11520  1 
iptable_nat            14724  1 
nf_nat                 30100  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      24216  4 iptable_nat,nf_nat
nf_defrag_ipv4         10496  1 nf_conntrack_ipv4
xt_state               10624  1 
nf_conntrack           84752  5 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state
ipt_REJECT             11776  2 
xt_tcpudp              11776  4 
iptable_filter         11392  1 
ip_tables              28304  2 iptable_nat,iptable_filter
x_tables               31624  6 ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_tcpudp,ip_tables
bridge                 63904  0 
stp                    11140  1 bridge
input_polldev          12688  0 
video                  29204  0 
output                 11648  1 video
lp                     19588  0 
snd_hda_intel         557492  3 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
joydev                 20864  0 
psmouse                64028  0 
nvidia              10274504  46 
usbhid                 47040  0 
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
serio_raw              14468  0 
ppdev                  16904  0 
pcspkr                 11136  0 
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             45096  1 
shpchp                 44572  0 
parport                49584  3 lp,ppdev,parport_pc
snd                    78792  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
forcedeth              68368  0 
floppy                 75816  0 
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
```**5 ) Kernel boot messages**

dmesg (this is the output given after I take it OUT and plug it back IN):
```
[51481.086948] usb 1-1: USB disconnect, address 2
[51485.288018] usb 1-1: new high speed USB device using ehci_hcd and address 4
[51485.559455] usb 1-1: configuration #1 chosen from 1 choice
```**6 ) Network configuration**

sudo lshw -C network:
```
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:24:8c:6e:fc:b4
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=10.0.0.3 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network:0
       description: Ethernet interface
       physical id: 1
       logical name: virbr0
       serial: ee:30:45:a0:05:0f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.168.122.1 link=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: d2:9e:dd:1f:d2:46
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```**7 ) Scan for networks:**

iwlist scan:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

virbr0    Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
```**8 ) Ubuntu Version: **

lsb_release -d:
```
Description:    Ubuntu 9.04
```**9 ) Kernel/architecture (including 32 vs. 64 bit): **

uname -mr:
```
2.6.28-13-generic x86_64
```

---

### Post by caseyb on 2009-07-06
Any help, please? :-(

---

### Post by b00lean on 2009-07-19
> **caseyb said:**
> After a clean reinstall of Ubuntu, I gave it another shot. This time I tried using the driver source code included on the CD out of the box the adapter came in.  For reference, this is the filename of the driver it shipped with:  2008_0506_RT73_Linux_STA_Drv1.1.0.1.tar.bz2

So I tried to configure it for making, but it needed the kernel source. So I did:
```
sudo apt-get install linux-headers-`uname -r`
sudo apt-get source linux-image-`uname -r`
sudo mkdir /usr/src/linux-2.6.28
sudo cp -r linux-2.6.28/* /usr/src/linux-2.6.28/
```That seemed to work, even though "uname -r" yields for me "2.6.28-13-generic". I don't know if there's a difference between linux-2.6.28 and 2.6.28-13-generic, even though the apt-get command I ran asked for the more specific source.

The make config didn't error out this time, but when I attempted to compile it wasn't happy:
```
queso@quark:~/dl/drivers/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module$ make config


-------------------- Ralink RT73 Station Configuration -------------------- 

  Linux kernel source directory [/usr/src/linux-2.6.28-13-generic]: /usr/src/linux-2.6.28
 
  Linux kernel source directory : /usr/src/linux-2.6.28
 
  Module install directory : /lib/modules/2.6.28-13-generic/kernel/drivers/net
 
queso@quark:~/dl/drivers/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module$ make all
make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/queso/dl/drivers/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  CC [M]  /home/queso/dl/drivers/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module/rtmp_main.o
/home/queso/dl/drivers/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module/rtmp_main.c: In function ‘usb_rtusb_close_device’:
/home/queso/dl/drivers/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module/rtmp_main.c:443: error: implicit declaration of function ‘kill_proc’
make[2]: *** [/home/queso/dl/drivers/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/queso/dl/drivers/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make: *** [all] Error 2
queso@quark:~/dl/drivers/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module$ 
```Any ideas? :-k

Hi caseyb,
I also bought today this cheap edimax and wondering why the support in 9.04 is not present. I hate wifi support on linux, this is one of the biggest weakneses of linux. 

Try to apply attached patch i created by copying it to /2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module
And run:
```

patch -p1 -i ubuntu_904_rt73.patch.txt
make all

```
Now the driver should compile and you should be able to continue in instructions provided in README file from original driver.

---

### Post by ugm6hr on 2009-08-01
As an Edimax EW-7318USG user, I thought I'd include my latest experience with Jaunty.

NB: See EDITs below for further updates on progress...

Remember, there appears to be a new version of this device - check lsusb to see which you have:

```
lsusb
Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
```

The default driver appears to be rt73usb, which works with Network Manager.  However, it intermittently misbehaves and refuses to connect, and particularly refuses to accept a correct WPA password.

My thoughts (perhaps incorrect)...

I have found rt2500usb driver interfering.  Hence, I blacklisted it:
```
sudo nano /etc/modprobe.d/blacklist-rt2500usb.conf
```
Add the line
```
blacklist rt2500usb
```
Then Ctrl+X to save.

This appears to ensure it always works, but it sometimes requires unplugging and replugging back in.  Additionally, it frequently drops a signal, and has to reconnect.

To resolve this, I tried the latest rt73 firmware:
```
sudo apt-get install rt73-common rt73-source
sudo update-rt73-firmware
```

A reboot later, and I have had a stable connection for about an hour now...

Will report back later if it is as steady as my other wifi connections.

EDIT: Another thread worth trying (did not work for me - yet):
[http://ubuntuforums.org/showthread.php?t=1215251](http://ubuntuforums.org/showthread.php?t=1215251)

EDIT2: Disconnects again overnight with Network Manager, and fails to reconnect with a prompt for password.  Still trying...

EDIT 3: Try this: [http://ubuntuforums.org/showthread.php?t=1211513](http://ubuntuforums.org/showthread.php?t=1211513)
No need to blacklist anything (i.e. remove the blacklist-rt2500usb.conf file created earlier.  Appears to work fairly well, with infrequent brief disconnections on Wicd 1.6.2 with default driver (rt73usb) using wext driver.

EDIT 4: I suspect I have a hardware issue, since the device works for others.

---

### Post by invalidreality on 2009-08-30
This might have to do with a missing device ID.  Look here:

[URL="http://www.electricshaman.com/2009/07/17/edimax-ew-7318usg/"]
http://www.electricshaman.com/2009/07/17/edimax-ew-7318usg/[/URL]

---

### Post by ProNux on 2009-10-31
It took me about 4 days to make it work (as I was new to Linux at that time) when I installed it to my desktop (Ubuntu Hardy Heron).

In my experience, this was automatically detected on Ubuntu Intrepid, which, I presume, would be automatically detected too in Jaunty Jackalope.

---

