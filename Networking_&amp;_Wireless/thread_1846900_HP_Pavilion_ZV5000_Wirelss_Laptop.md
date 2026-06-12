---
title: "HP Pavilion ZV5000 Wirelss Laptop"
date: 2011-09-19
forum: Networking &amp; Wireless
---

### Post by User3k on 2011-09-19
I have been trying to get the wireless on this laptop working. I tried with Xubuntu, Fedora, Debian and even tried Puppy. Now I know it does work. They owner of this laptop had Windows XP on it. It was acting buggy and is outdated so he wanted me to put Linux on it. My question is this. Does Ubuntu, Xubuntu, Lubuntu work with this laptop model? I never had to set up wireless before. I can install everything and update it through an Ethernet cable. But I need to know what to do after all of it is installed, updated, etc, to get the wireless to work.

I am asking because I am lost and frustrated with trying this so far. I am pretty sure it is not Linux but something I am doing or not doing that is the issue.

---

### Post by wildmanne39 on 2011-09-19
Hi, run these commands in a terminal please one at a time:
```
cat /etc/lsb-release; uname -a
sudo lshw -C network
lspci -nn | grep -e 0280 -e 0200
iwconfig
rfkill list all
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by User3k on 2011-09-20
I had asked the question before I reinstalled Ubuntu. Took a little longer. I had installed it the first time but forgot to plug it in before I went to bed, the battery died during the install :oops:

Now it is all installed, need to update it but wanted to get this info pasted here as soon as possible. There is a wireless button on the laptop. Usually you are suppose to push it to start/stop the wireless. I can't do it with Ubuntu.

I currently have the Ethernet cable plugged in, but that is not what he wants.


```

*_cat /etc/lsb-release; uname -a_*
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 athlon i386 GNU/Linux


*_sudo lshw -C network_*
   *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:4a:84:d8
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.3 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes 

port=MII speed=100Mbit/s
       resources: irq:18 ioport:7000(size=256) memory:e0108800-e01088ff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:e0104000-e0105fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:b7:2c:c5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg


*_lspci -nn | grep -e 0280 -e 0200_*
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)


*_iwconfig_*
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off



*_rfkill list all_*
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no


*_lsmod_*
Module                  Size  Used by
usb_storage            43946  1 
uas                    17676  0 
binfmt_misc            13213  1 
arc4                   12473  2 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
b43                   296610  0 
nouveau               621970  3 
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
ttm                    65184  1 nouveau
snd_seq_midi           13132  0 
drm_kms_helper         40745  1 nouveau
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
drm                   180037  5 nouveau,ttm,drm_kms_helper
joydev                 17322  0 
ppdev                  12849  0 
mac80211              257001  1 b43
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39671  0 
i2c_algo_bit           13184  1 nouveau
parport_pc             32111  1 
cfg80211              156212  2 b43,mac80211
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
serio_raw              12990  0 
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
video                  18951  1 nouveau
i2c_nforce2            12906  0 
soundcore              12600  1 snd
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
lp                     13349  0 
k8temp                 12872  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
shpchp                 32345  0 
parport                36746  3 ppdev,parport_pc,lp
firewire_ohci          31504  0 
8139too                23208  0 
ssb                    45942  1 b43
firewire_core          56138  1 firewire_ohci
8139cp                 22497  0 
pata_amd               13762  2 
crc_itu_t              12627  1 firewire_core
```

---

### Post by wildmanne39 on 2011-09-20
Hi, run this command please after it is done restart your computer with the wired connection unplugged and see if it works.
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
Thank you

---

### Post by User3k on 2011-09-20
Thanks. Will do once the update is done. Will post results.

---

### Post by User3k on 2011-09-20
After I installed the b43 packages I saw that blue light show up on the wireless button. I kept all my fingers crossed (which really makes typing difficult ;) ) and rebooted. It showed that there was a wireless network available and it works.


Thanks for the help :)

---

### Post by wildmanne39 on 2011-09-20
Hi, that is great I am glad I could help, I see you have already marked as solved, I would appreciate it if you would click on the red link in my signature and show your support for me becoming an ubuntu member if not that is ok too.
Thank you

---

### Post by User3k on 2011-09-20
It's the least I can do :)

---

### Post by wildmanne39 on 2011-09-20
Hi, Thank you I really appreciate the support.

---

### Post by proppk5 on 2012-12-18
I have exact same problem.  I never dissect the HP Pavilion zv5000 into pieces-parts to see what make & model the wireless NIC card is, but it worked fine seeing wireless WiFi networks when the laptop was loaded with Win XP and later with Win 7, but could never see wireless with even the most recent versions of Ubuntu.  When looking closer into SYSTEM SETTINGS > NETWORK there is a notice saying "FIRMWARE MISSING, HARDWARE ADDRESS 00:90:4B:98:94:EC".   The fact that it says "FIRMWARE" (ie: software embedded into a chip) and it shows a hardware address, this seems to be a slot on the motherboard, but unsure if this is the slot where the wireless NIC card sits. 

Maybe this is some incompatibility quirk with this particular wireless NIC card (or maybe the BIOS itself) on this type of laptop that Canonical failed to notice or otherwise address in the wireless kernel.  HOW DO I GET THIS DONE ?

---

