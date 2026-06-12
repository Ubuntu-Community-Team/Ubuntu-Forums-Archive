---
title: "Toshiba Satellite L10 / Inprocomm IPN 2220 / Driver Installed, Does Not Connect"
date: 2012-08-12
forum: Networking &amp; Wireless
---

### Post by LXDE on 2012-08-12
Hi-

Running Lubuntu 12.04.

I used ndiswrapper in the past to install a wifi driver for a Dell Latitude laptop I owned in the past with no problems. The thing ran perfectly. However, with my current Toshiba Satellite L10, with an Inprocomm IPN 2220 wifi chipset, the driver seems to install fine, but there is no wlan0 being recognized, so I cannot connect to a wireless access point.

Here's the data. The wired ethernet works fine, as you can see. Also, ndiswrapper shows the driver installed fine:

> ndiswrapper -l
neti2220 : driver installed
	device (17FE:2220) present



> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:86:27:09  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe86:2709/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4651 errors:76 dropped:79 overruns:76 frame:0
          TX packets:3451 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3972671 (3.9 MB)  TX bytes:443316 (443.3 KB)
          Interrupt:6 Base address:0x3800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1046 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1046 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:85479 (85.4 KB)  TX bytes:85479 (85.4 KB)


> lsmod
Module                  Size  Used by
isofs                  39553  1 
dm_crypt               22528  1 
joydev                 17393  0 
snd_intel8x0           33455  1 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia                 39791  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ndiswrapper           192268  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    62064  9 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87213  0 
soundcore              14635  1 snd
serio_raw              13027  0 
sbs                    18178  0 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
shpchp                 32325  0 
sbshc                  13536  1 sbs
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
i915                  414620  2 
8139too                23283  0 
8139cp                 22633  0 
drm_kms_helper         45466  1 i915
drm                   197692  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915


> sudo lshw -C network
[sudo] password for ****: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:86:27:09
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.2 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:6 ioport:3800(size=256) memory:e0401800-e04018ff
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: IPN 2220 802.11g
       vendor: InProComm Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=32 mingnt=32
       resources: ioport:3c00(size=32) memory:e0401c00-e0401c1f memory:e0401000-e04017ff


> sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 


The Toshiba L10 wifi is listed on the supported ndiswrapper devices on the sourceforge wiki, so I am holding out hope.

What to do?

---

### Post by henkjanj on 2012-12-30
I have the same problem!
Can someone help me?

Kind regards,
HJJ

What more can I check to see if everything is installed correctly?

---

### Post by henkjanj on 2012-12-30
Solved it myself!

I had to change the driver, do not use the 3.07.02.2005-driver which is found everywhere on the net. Problem is that there is only one .inf file, and it picks the wrong .sys file (and you can't make it pick the right one, if I were you I wouldn't try...). it picks the i2220nta.sys version which is for 64-bit. And I have a 32 bit computer and a 32 bit ubuntu version.

There's a couple of alternative drivers here: [http://ubuntuforums.org/showthread.php?t=1042480](http://ubuntuforums.org/showthread.php?t=1042480)

I have used the ipn2220_32_64_all.tar driver, and then the 
ipn2220_x32ntw2000_mod.inf file. 

Maybe someone will need this...

HJJ

---

