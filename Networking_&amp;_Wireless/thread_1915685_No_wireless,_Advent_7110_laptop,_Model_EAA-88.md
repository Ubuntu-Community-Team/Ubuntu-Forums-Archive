---
title: "No wireless, Advent 7110 laptop, Model EAA-88"
date: 2012-01-26
forum: Networking &amp; Wireless
---

### Post by 1cookie on 2012-01-26
hi

I just acquired an old Advent laptop as above. It's not a dinosaur dont get me wrong, so I won't be throwing it away just yet.  Ive installed Ubuntu 11.04 on it and it connects fine through the ethernet hard wire.  Trouble is I can't connect to the wireless.  From the menu, the 'Enable Wireless' and 'Wireless Networks' options are grayed out. I run some tests as follows:

```


jessica@jessica-00000000000000000:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux jessica-00000000000000000 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

jessica@jessica-00000000000000000:~$ sudo lshw -C network
[sudo] password for jessica: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:a7:e4:c4
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.5 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=1Gbit/s
       resources: irq:19 ioport:3000(size=256) memory:b0106000-b01060ff memory:44000000-4401ffff
  *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:06:04.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:a9:4f:68
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:b0107000-b0107fff


jessica@jessica-00000000000000000:~$ lspci -nn | grep -e 0280 -e 0200
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)
06:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)

jessica@jessica-00000000000000000:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jessica@jessica-00000000000000000:~$ sudo pccardctl ident
Socket 0:
  no product info available

jessica@jessica-00000000000000000:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jessica@jessica-00000000000000000:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

jessica@jessica-00000000000000000:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
joydev                 17322  0 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
i915                  450944  3 
snd_rawmidi            25269  1 snd_seq_midi
binfmt_misc            13213  1 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39671  0 
ipw2200               145664  0 
snd_timer              28659  2 snd_pcm,snd_seq
drm_kms_helper         40745  1 i915
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
libipw                 46641  1 ipw2200
cfg80211              156212  2 ipw2200,libipw
drm                   180037  4 i915,drm_kms_helper
tifm_7xx1              12898  0 
yenta_socket           27230  0 
irda                  185091  0 
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
tifm_core              15040  1 tifm_7xx1
serio_raw              12990  0 
lib80211               14570  2 ipw2200,libipw
soundcore              12600  1 snd
crc_ccitt              12595  1 irda
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
r8169                  42534  0 
sdhci_pci              13623  0 
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core



```I'm lost with all this information really. One thing that is clear me thinks is that there is a missing driver or wireless network interface somewhere. Is it a common problem with older laptops? Can anyone offer some advice in laymans terms? I'd love to buy you a beer if we can fix it!
:(

---

### Post by 1cookie on 2012-01-27
well, from the tests:

```

-*network:1 DISABLED
Wireless interface



```
this is the clue that tells me my interface exists! I was looking for a switch, to switch wireless networking on. It turns out this is a key combination of Fn + F2. I installed a spare copy of windows i had, pressed the key combination above and voila, wireless networks appeared!

Noobs guide, but hey...:)

---

