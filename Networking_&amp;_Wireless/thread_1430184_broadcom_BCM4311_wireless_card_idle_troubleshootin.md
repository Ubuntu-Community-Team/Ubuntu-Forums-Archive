---
title: "broadcom BCM4311 wireless card idle troubleshooting"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by broccolina on 2010-03-15
Hello!

I installed ubuntu on this laptop today because windows was absolutely shot and being a store-bought laptop they didn't give any boot discs and it costs money to get it fixed...

Everything works fine, wireless card is recognised but listed as "disabled".
There is a button on the laptop to physically enable wireless, and the light is on but ubuntu seems to think it's still disabled.

I have tried the following...

I followed instruction from another thread: [http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)
I got to step 2 successfully, but when it comes to the last step within step 2 which says to create wl.ko file - "Now, we want to make the wl.ko file, so we enter: 
(<2.6.xx.xx> is your kernel version: mine was "2.6.24-19-generic". Use tab-completion to find yours.)"
     Code:
     make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` clean
make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` 

 i keep getting an error - "bash: 2.6.30-20-generic: no such file or directory"

The drivers I downloaded as far as I know are linux compatible. I read the readme file that came with them and it said I had to install headers and tools to build a kernel module.
I installed build-essential via the cdrom and as far as I know it installed correctly.
Also tried installing build-dep and that seemed to install properly too.

I looked at ways around this and found instructions on ndiswrapper, tried installing that but from what I could gather that was for windows based drivers and I'm pretty sure the drivers I downloaded are for linux. 

Anything I'm doing wrong? Maybe I stuffed it all up and need to start again? Please help! I don't like being tethered to my router :D

oh I saw some instructions on information to post with this so here you go...

Machine brand - compaq presario (not sure what model)
Wifi adapter - Broadcom BCM4311
 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:bc:ab:bc  
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:febc:abbc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11985 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10096439 (10.0 MB)  TX bytes:999590 (999.5 KB)
          Interrupt:16 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
*-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:20000000-20003fff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:bc:ab:bc
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.106 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:16 ioport:2000(size=256) memory:d0100000-d01000ff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:2f:18:de
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
Description:    Ubuntu 9.10
2.6.31-20-generic i686

---

### Post by leorolla on 2010-03-15
You can try this:
[http://ubuntuforums.org/showthread.php?t=1312603](http://ubuntuforums.org/showthread.php?t=1312603)

---

### Post by bkratz on 2010-03-15
Do you know which kernel you are using? If not, go to the terminal and enter

uname -mr

The thread you are following is kinda old so we need to determine what kernel you are using, you can copy/paste the output back here.

It seems that you are trying to manage your connection with a b43 variant, but are trying to install the STA version, so we may need to "blacklist" some things.  You might as well also post the longer output of 

lsmod

(that is LSMOD in lowercase) and use the code tools above to make it more readable.

---

### Post by 2hot6ft2 on 2010-03-15
There's a guide for 9.10 for Broadcom including the one you have here:
[The Definitive 9.10 Broadcom Solution Guide]("http://ubuntuforums.org/showthread.php?t=1368699")

If you need it.

---

### Post by broccolina on 2010-03-15
> **bkratz said:**
> Do you know which kernel you are using? If not, go to the terminal and enter

uname -mr

The thread you are following is kinda old so we need to determine what kernel you are using, you can copy/paste the output back here.

It seems that you are trying to manage your connection with a b43 variant, but are trying to install the STA version, so we may need to "blacklist" some things.  You might as well also post the longer output of 

lsmod

(that is LSMOD in lowercase) and use the code tools above to make it more readable.

Here's the results...

2.6.31-20-generic i686

Module                  Size  Used by
rt73usb                26336  0 
crc_itu_t               1852  1 rt73usb
rt2x00usb              11548  1 rt73usb
rt2x00lib              29756  2 rt73usb,rt2x00usb
input_polldev           3716  1 rt2x00lib
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_conexant    20060  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
iptable_filter          3100  0 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
ip_tables              11692  1 iptable_filter
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
x_tables               16544  1 ip_tables
joydev                 10240  0 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
arc4                    1660  2 
ecb                     2524  2 
snd                    59204  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
b43                   122200  0 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
mac80211              181140  3 rt2x00usb,rt2x00lib,b43
cfg80211               93052  3 rt2x00lib,b43,mac80211
psmouse                56500  0 
lp                      8964  0 
led_class               4096  2 rt2x00lib,b43
serio_raw               5280  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  226120  3 
drm                   160032  3 i915
i2c_algo_bit            5760  1 i915
ssb                    35524  1 b43
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

---

### Post by broccolina on 2010-03-15
> **leorolla said:**
> You can try this:
[http://ubuntuforums.org/showthread.php?t=1312603](http://ubuntuforums.org/showthread.php?t=1312603)

Thanks, 

In hardware drivers I have 2, one for broadcom 43xx and one for broadcom STA, both say not active. When I tried activating them it didnt do anything. Didnt load, just sat there saying "installing" and wouldnt close. Had to restart computer to get rid of it. that happened with both.

---

### Post by broccolina on 2010-03-15
And just one more thing..

I said before I have the linux compatible drivers, but there is something stopping me from creating a wl.ko file. Something to do with the fact the command line isn't reconising kernel version or something. Yes I am a noob but be patient haha :)

The instructions say i need to install build-essential, headers and tools. Any way of doing that? I installed build-essential fine and something else... I think it was build-dep. Anything else I need?

---

### Post by bkratz on 2010-03-15
The first two things that jump out at me are--it is trying to use the b43 module--will probably need to blacklist this eventually and


i keep getting an error - "bash: 2.6.30-20-generic: no such file or directory"


and 

2.6.31-20-generic i686


Did you get a kernel update since you started this (the error says 30 and the current kernel says 31)

?

---

### Post by bkratz on 2010-03-15
Build-essentials should be fine. By the way here is a good current description

[http://ubuntuforums.org/showpost.php?p=8827649&postcount=7](http://ubuntuforums.org/showpost.php?p=8827649&postcount=7)

---

### Post by broccolina on 2010-03-15
> **bkratz said:**
> The first two things that jump out at me are--it is trying to use the b43 module--will probably need to blacklist this eventually and


i keep getting an error - "bash: 2.6.30-20-generic: no such file or directory"


and 

2.6.31-20-generic i686


Did you get a kernel update since you started this (the error says 30 and the current kernel says 31)

?

Yeah did updates through update manager and some command line thing. I have retried since the updates and still get the bash error. 

So if I need to blacklist something are u able to tell me what it is and how to do it? I am so new to ubuntu, thanks so much for your help :)

---

### Post by broccolina on 2010-03-15
Maybe I should tell you exactly whats going on...

I downloaded the linux drivers for the card.

untarred the file into a directory I created called "wdriver" 

from the command line I should be able to create a "wl.ko" file, but when I put in the command to do so, that's when I get the error. 

> andrew@andrew-laptop:~/wdriver$ make -c /lib/modules/<2.6.31-20-generic>/build M=`pwd` clean
bash: 2.6.31-20-generic: No such file or directory

maybe I'm typing something wrong?

---

### Post by leorolla on 2010-03-16
Why recompiling if all this job has been done and it is in the Ubuntu repositories?

If you can get wired internet, run

```
sudo aptitude update && sudo aptitude upgrade && sudo aptitude install bcmwl-kernel-source

```

Reboot.

If you don't have internet, show us the output of
```
sudo lshw -C network
lspci
lsmod
grep b43 /etc/modprobe.d/*
grep blacklist /etc/modprobe.d/*
grep ndiswrapper /etc/modprobe.d/*

```

When you copy-paste the outputs to post here, PLEASE use CODE inside brackets before the outpout, and /CODE inside brackets after it, so it will look neat as my commands above.

---

### Post by broccolina on 2010-03-16
Ok I have wired internet as the ethernet port is working fine, did the update and it asked to reboot though it didn't look done...

retried, same bash error.

results of those commands you gave me...

```
andrew@andrew-laptop:~$ sudo lshw -c network
[sudo] password for andrew: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:20000000-20003fff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:bc:ab:bc
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.1.1.4 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:16 ioport:2000(size=256) memory:d0100000-d01000ff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:2f:18:de
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
andrew@andrew-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
andrew@andrew-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_conexant    20060  1 
joydev                 10240  0 
snd_hda_intel          26920  3 
iptable_filter          3100  0 
snd_hda_codec          75708  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
arc4                    1660  2 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ecb                     2524  2 
lp                      8964  0 
snd                    59204  17 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
b43                   122200  0 
mac80211              181140  1 b43
soundcore               7264  1 snd
psmouse                56500  0 
cfg80211               93052  2 b43,mac80211
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
serio_raw               5280  0 
parport                35340  2 ppdev,lp
led_class               4096  1 b43
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  226120  3 
drm                   160032  3 i915
i2c_algo_bit            5760  1 i915
ssb                    35524  1 b43
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video
andrew@andrew-laptop:~$ grep b43 /etc/modprobe.d/*
/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.
andrew@andrew-laptop:~$ grep blacklist /etc/modprobe.d/*
/etc/modprobe.d/alsa-base.conf:install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
/etc/modprobe.d/alsa-base.conf:install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
/etc/modprobe.d/alsa-base.conf:install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
/etc/modprobe.d/alsa-base.conf:install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
/etc/modprobe.d/alsa-base.conf:install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
/etc/modprobe.d/alsa-base.conf:install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
/etc/modprobe.d/alsa-base.conf:install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }
/etc/modprobe.d/alsa-base.conf:install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
/etc/modprobe.d/blacklist-ath_pci.conf:blacklist ath_pci
/etc/modprobe.d/blacklist.conf:blacklist evbug
/etc/modprobe.d/blacklist.conf:blacklist usbmouse
/etc/modprobe.d/blacklist.conf:blacklist usbkbd
/etc/modprobe.d/blacklist.conf:blacklist eepro100
/etc/modprobe.d/blacklist.conf:blacklist de4x5
/etc/modprobe.d/blacklist.conf:blacklist eth1394
/etc/modprobe.d/blacklist.conf:blacklist snd_intel8x0m
/etc/modprobe.d/blacklist.conf:blacklist snd_aw2
/etc/modprobe.d/blacklist.conf:blacklist i2c_i801
/etc/modprobe.d/blacklist.conf:blacklist prism54
/etc/modprobe.d/blacklist.conf:blacklist bcm43xx
/etc/modprobe.d/blacklist.conf:blacklist garmin_gps
/etc/modprobe.d/blacklist.conf:blacklist asus_acpi
/etc/modprobe.d/blacklist.conf:blacklist snd_pcsp
/etc/modprobe.d/blacklist.conf:blacklist pcspkr
/etc/modprobe.d/blacklist.conf:blacklist amd76x_edac
/etc/modprobe.d/blacklist-firewire.conf:#blacklist ohci1394
/etc/modprobe.d/blacklist-firewire.conf:#blacklist sbp2
/etc/modprobe.d/blacklist-firewire.conf:#blacklist dv1394
/etc/modprobe.d/blacklist-firewire.conf:#blacklist raw1394
/etc/modprobe.d/blacklist-firewire.conf:#blacklist video1394
/etc/modprobe.d/blacklist-firewire.conf:blacklist firewire-ohci
/etc/modprobe.d/blacklist-firewire.conf:blacklist firewire-sbp2
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist aty128fb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist atyfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist radeonfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist cirrusfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist cyber2000fb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist cyblafb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist gx1fb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist hgafb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist i810fb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist intelfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist kyrofb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist lxfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist matroxfb_base
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist neofb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist nvidiafb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist pm2fb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist rivafb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist s1d13xxxfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist savagefb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist sisfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist sstfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist tdfxfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist tridentfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist vesafb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist vfb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist vga16fb
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist vt8623fb
/etc/modprobe.d/blacklist-modem.conf:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-intel8x0m
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-via82xx-modem
/etc/modprobe.d/blacklist-oss.conf:blacklist ac97
/etc/modprobe.d/blacklist-oss.conf:blacklist ac97_codec
/etc/modprobe.d/blacklist-oss.conf:blacklist ac97_plugin_ad1980
/etc/modprobe.d/blacklist-oss.conf:blacklist ad1848
/etc/modprobe.d/blacklist-oss.conf:blacklist ad1889
/etc/modprobe.d/blacklist-oss.conf:blacklist adlib_card
/etc/modprobe.d/blacklist-oss.conf:blacklist aedsp16
/etc/modprobe.d/blacklist-oss.conf:blacklist ali5455
/etc/modprobe.d/blacklist-oss.conf:blacklist btaudio
/etc/modprobe.d/blacklist-oss.conf:blacklist cmpci
/etc/modprobe.d/blacklist-oss.conf:blacklist cs4232
/etc/modprobe.d/blacklist-oss.conf:blacklist cs4281
/etc/modprobe.d/blacklist-oss.conf:blacklist cs461x
/etc/modprobe.d/blacklist-oss.conf:blacklist cs46xx
/etc/modprobe.d/blacklist-oss.conf:blacklist emu10k1
/etc/modprobe.d/blacklist-oss.conf:blacklist es1370
/etc/modprobe.d/blacklist-oss.conf:blacklist es1371
/etc/modprobe.d/blacklist-oss.conf:blacklist esssolo1
/etc/modprobe.d/blacklist-oss.conf:blacklist forte
/etc/modprobe.d/blacklist-oss.conf:blacklist gus
/etc/modprobe.d/blacklist-oss.conf:blacklist i810_audio
/etc/modprobe.d/blacklist-oss.conf:blacklist kahlua
/etc/modprobe.d/blacklist-oss.conf:blacklist mad16
/etc/modprobe.d/blacklist-oss.conf:blacklist maestro
/etc/modprobe.d/blacklist-oss.conf:blacklist maestro3
/etc/modprobe.d/blacklist-oss.conf:blacklist maui
/etc/modprobe.d/blacklist-oss.conf:blacklist mpu401
/etc/modprobe.d/blacklist-oss.conf:blacklist nm256_audio
/etc/modprobe.d/blacklist-oss.conf:blacklist opl3
/etc/modprobe.d/blacklist-oss.conf:blacklist opl3sa
/etc/modprobe.d/blacklist-oss.conf:blacklist opl3sa2
/etc/modprobe.d/blacklist-oss.conf:blacklist pas2
/etc/modprobe.d/blacklist-oss.conf:blacklist pss
/etc/modprobe.d/blacklist-oss.conf:blacklist rme96xx
/etc/modprobe.d/blacklist-oss.conf:blacklist sb
/etc/modprobe.d/blacklist-oss.conf:blacklist sb_lib
/etc/modprobe.d/blacklist-oss.conf:blacklist sgalaxy
/etc/modprobe.d/blacklist-oss.conf:blacklist sonicvibes
/etc/modprobe.d/blacklist-oss.conf:blacklist sound
/etc/modprobe.d/blacklist-oss.conf:blacklist sscape
/etc/modprobe.d/blacklist-oss.conf:blacklist trident
/etc/modprobe.d/blacklist-oss.conf:blacklist trix
/etc/modprobe.d/blacklist-oss.conf:blacklist uart401
/etc/modprobe.d/blacklist-oss.conf:blacklist uart6850
/etc/modprobe.d/blacklist-oss.conf:blacklist via82cxxx_audio
/etc/modprobe.d/blacklist-oss.conf:blacklist v_midi
/etc/modprobe.d/blacklist-oss.conf:blacklist wavefront
/etc/modprobe.d/blacklist-oss.conf:blacklist ymfpci
/etc/modprobe.d/blacklist-oss.conf:blacklist ac97_plugin_wm97xx
/etc/modprobe.d/blacklist-oss.conf:blacklist ad1816
/etc/modprobe.d/blacklist-oss.conf:blacklist audio
/etc/modprobe.d/blacklist-oss.conf:blacklist awe_wave
/etc/modprobe.d/blacklist-oss.conf:blacklist dmasound_core
/etc/modprobe.d/blacklist-oss.conf:blacklist dmasound_pmac
/etc/modprobe.d/blacklist-oss.conf:blacklist harmony
/etc/modprobe.d/blacklist-oss.conf:blacklist sequencer
/etc/modprobe.d/blacklist-oss.conf:blacklist soundcard
/etc/modprobe.d/blacklist-oss.conf:blacklist usb-midi
/etc/modprobe.d/blacklist-watchdog.conf:blacklist acquirewdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist advantechwdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist alim1535_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist alim7101_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist booke_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist cpu5wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist eurotechwdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist i6300esb
/etc/modprobe.d/blacklist-watchdog.conf:blacklist i8xx_tco
/etc/modprobe.d/blacklist-watchdog.conf:blacklist ib700wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist ibmasr
/etc/modprobe.d/blacklist-watchdog.conf:blacklist indydog
/etc/modprobe.d/blacklist-watchdog.conf:blacklist iTCO_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist it8712f_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist it87_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist ixp2000_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist ixp4xx_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist machzwd
/etc/modprobe.d/blacklist-watchdog.conf:blacklist mixcomwd
/etc/modprobe.d/blacklist-watchdog.conf:blacklist mpc8xx_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist mpcore_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist mv64x60_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist pc87413_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist pcwd
/etc/modprobe.d/blacklist-watchdog.conf:blacklist pcwd_pci
/etc/modprobe.d/blacklist-watchdog.conf:blacklist pcwd_usb
/etc/modprobe.d/blacklist-watchdog.conf:blacklist s3c2410_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist sa1100_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist sbc60xxwdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist sbc7240_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist sb8360
/etc/modprobe.d/blacklist-watchdog.conf:blacklist sc1200wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist sc520_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist sch311_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist scx200_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist shwdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist smsc37b787_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist softdog
/etc/modprobe.d/blacklist-watchdog.conf:blacklist twl4030_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist w83627hf_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist w83697hf_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist w83697ug_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist w83877f_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist w83977f_wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist wafer5823wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist wdt
/etc/modprobe.d/blacklist-watchdog.conf:blacklist wdt_pci
/etc/modprobe.d/blacklist-watchdog.conf:blacklist wm8350_wdt
/etc/modprobe.d/libpisock9.conf:blacklist visor
andrew@andrew-laptop:~$ grep ndiswrapper /etc/modprobe.d/*
andrew@andrew-laptop:~$ 

```

---

### Post by Bucky Ball on 2010-03-16
That card should work out of the box (I had no trouble from 8.04). BUT, YOU NEED TO PLUG IN AN ETHERNET CABLE AND GET YOUR (regular) UPDATES!!! You do not need to change the kernel.

That should pick up the fact your card is there and install the restricted drivers. Takes about 5 minutes. Just follow your nose.

Broadcom used to be a nightmare, now simple. Plug that cable in and get cracking, shouldn't be recompiling or tweaking, sticking things in terminals, downloading things from websites or diddling around with anything. Under NO circumstances resort to ndiswrapper. It is usually unsuccessful with this card and superseded by B43 (the Broadcom driver) and b43-fwcutter.

System->Admin->Hardware Drivers. B43 there but disabled??

---

### Post by broccolina on 2010-03-16
> **Bucky Ball said:**
> That card should work out of the box (I had no trouble from 8.04). BUT, YOU NEED TO PLUG IN AN ETHERNET CABLE AND GET YOUR (regular) UPDATES!!! You do not need to change the kernel.

That should pick up the fact your card is there and install the restricted drivers. Takes about 5 minutes. Just follow your nose.

Broadcom used to be a nightmare, now simple. Plug that cable in and get cracking, shouldn't be recompiling or tweaking, sticking things in terminals, downloading things from websites or diddling around with anything. Under NO circumstances resort to ndiswrapper. It is usually unsuccessful with this card and superseded by B43 (the Broadcom driver) and b43-fwcutter.

System->Admin->Hardware Drivers. B43 there but disabled??

Trust me, if it were that simple I wouldnt have asked for help. I spent a good 4 hours trying to solve this myself before asking for help. Already done all updates that I could, the OS seems to know my card is there, the brand, type and everything as soon as i turned the laptop on. Problem is that it's permanently disabled... and the physical switch on the laptop is lit up and I can't toggle it. Thanks for trying though

---

### Post by leorolla on 2010-03-17
> **Bucky Ball said:**
> System->Admin->Hardware Drivers. B43 there but disabled?

> **broccolina said:**
> Trust me, if it were that simple I wouldnt have asked for help. I spent a good 4 hours trying to solve this myself before asking for help. Already done all updates that I could, the OS seems to know my card is there, the brand, type and everything as soon as i turned the laptop on. Problem is that it's permanently disabled... and the physical switch on the laptop is lit up and I can't toggle it. Thanks for trying though

He asked a pertinent question.

System->Admin->Hardware Drivers
For your device:
Choose BCM and not B43.

By the way, it really feels like you didn't run the update/install command exactly as I have posted, as "wl" is neither loaded nor blacklisted.

---

