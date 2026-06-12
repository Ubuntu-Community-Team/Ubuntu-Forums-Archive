---
title: "Avahi and wireless vs wired"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by wycowboy911 on 2009-04-26
I've ran into an interesting problem.  This has happened to me using 8.04, 8.10 and now Jaunty on two separate laptops.  Avahi works great, only as long as I'm on a wired connection.  The minute I switch to wireless, I can't see anything but my computer when I do a discovery.  Since it works fine on a wired connection, I know it's some kind of issue with avahi.  Wired and wireless nets are both on the same subnet with the same ip address allocation.  Network settings are for static IP.  I've tried using the mad-wifi drivers AND the standard driver that comes with the distro.  I've tried all kinds of switches in avahi-daemon.conf and still nothing works.

I've attached the output of ifconfig, lspci and my currently loaded modules.  Any suggestions you could give me would help!

Jay

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:3c:cb:5c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:09:d8:6a  
          inet addr:192.168.0.20  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2bff:fe09:d86a/64 Scope:Link
          UP BROADCAST RUNNING PROMISC ALLMULTI MULTICAST  MTU:1500  Metric:1
          RX packets:3252 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2685 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2545671 (2.5 MB)  TX bytes:588355 (588.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2B-09-D8-6A-38-36-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

 lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

lsmod
Module                  Size  Used by
arc4                    9856  2 
ecb                    10752  2 
ath5k                 107008  0 
binfmt_misc            16776  1 
i915                   65540  2 
drm                    96296  3 i915
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               63240  0 
compat_ioctl32          9344  1 uvcvideo
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                61972  0 
videodev               41600  1 uvcvideo
acer_wmi               24260  0 
intel_agp              34108  1 
soundcore              15200  1 snd
pcspkr                 10496  0 
mac80211              217208  1 ath5k
serio_raw              13316  0 
v4l1_compat            21764  2 uvcvideo,videodev
btusb                  19608  2 
video                  25360  0 
agpgart                42696  3 drm,intel_agp
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
led_class              12036  2 ath5k,acer_wmi
output                 11008  1 video
cfg80211               38032  2 ath5k,mac80211
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

---

### Post by wycowboy911 on 2009-05-03
Bump

---

### Post by mrrnlds on 2009-07-20
Any luck solving this?

I am having exactly the same problem... set up UNR on a netbook and can only see avahi services with the wired connection. The wireless connection works fine for other purposes but no services are visible when connected only by wifi.

I also have Jaunty on a regular laptop and avahi services work fine either by wifi or wired connection. Only clue I can find is that on my netbook the wifi connection is wlan0 while on my laptop it is eth1. The wired connection is eth0 in both cases.

---

### Post by mrrnlds on 2009-07-24
Reason found for my case; my wireless chip driver ([FONT=Arial][SIZE=1]RTL8187SE[/SIZE][/FONT]) does not support multicast correctly - see: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360926](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/360926)

Suggest anyone with this issue read the Avahi FAQ here:
[http://avahi.org/wiki/Avah4users#FAQ](http://avahi.org/wiki/Avah4users#FAQ)

---

