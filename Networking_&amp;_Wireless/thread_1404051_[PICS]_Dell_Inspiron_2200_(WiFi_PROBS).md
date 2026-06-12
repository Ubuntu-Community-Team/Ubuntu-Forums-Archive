---
title: "[PICS] Dell Inspiron 2200 (WiFi PROBS)"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by retro_killa on 2010-02-11
I just got my CD in the mail from Ubuntu 9.10 32bit. I did a clean install wiped out the windows OS & I now have Linux on this laptop. The internet works when the cable is plugged into the Ethernet port but when plunged in the built in WiFi will not find or show anything :( 

I am having a heck of a time getting my WiFi set up please enjoy the screen shots

So this is what I did 

[[IMG]http://img682.imageshack.us/img682/996/screenshotci.png[/IMG]](http://img682.imageshack.us/i/screenshotci.png/)

then 

[[IMG]http://img682.imageshack.us/img682/8937/screenshothardwaredrive.png[/IMG]](http://img682.imageshack.us/i/screenshothardwaredrive.png/)

& then I restarted / booted ubuntu 

[[IMG]http://img534.imageshack.us/img534/4308/screenshotrestart.png[/IMG]](http://img534.imageshack.us/i/screenshotrestart.png/)

Still not able to use my WiFi :/ & yes I happen to have a wireless router that is working on on a windows XP laptop with out any probs.. 

HELP PLZ !!!! 



I went ahead & did this just to help you all help me ;) 
lsmod
nm-tool
lshw -C Network

```
warren@Dell-Inspiron-2200:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10240  0 
arc4                    1660  2 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
ecb                     2524  2 
pcmcia                 36808  0 
snd_seq_dummy           2656  0 
dell_wmi                2564  0 
iptable_filter          3100  0 
snd_seq_oss            28576  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
dell_laptop             8128  0 
dcdbas                  7292  1 dell_laptop
b43                   122168  0 
mac80211              181140  1 b43
cfg80211               93052  2 b43,mac80211
led_class               4096  1 b43
psmouse                56500  0 
serio_raw               5280  0 
yenta_socket           24296  1 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
hid_a4tech              2652  0 
usbhid                 38208  0 
i915                  221320  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
ssb                    35364  1 b43
e100                   32420  0 
mii                     5212  1 e100
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
warren@Dell-Inspiron-2200:~$ nm-tool

NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        00:90:4B:E6:E1:11

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        00:14:22:C4:57:50

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


warren@Dell-Inspiron-2200:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:19 memory:dfdfe000-dfdfffff
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:14:22:c4:57:50
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A ip=192.168.1.2 latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:dfdfd000-dfdfdfff ioport:df40(size=64)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:e6:e1:11
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
warren@Dell-Inspiron-2200:~$ lshw -C Network

```

---

### Post by retro_killa on 2010-02-11
Bump bump bump

---

### Post by retro_killa on 2010-02-11
Help me please.... I would like to get this laptop online via WiFi.

PS... I am on a different laptop right now running Windows 7 & I hate it. 

So please help me thanks

:)

---

### Post by bkratz on 2010-02-11
People have gotten the BCM4318 to work in various ways. It is supposed to be supported by b43 and lots of people claim that it works with that. Some say it doesn't and use ndiswrapper. If you use the search box at the top of the page you will see a lot of them for the 4318-many go unanswered.  This was one of the successful ones.

[http://ubuntuforums.org/showthread.php?t=1347487&highlight=BCM4318](http://ubuntuforums.org/showthread.php?t=1347487&highlight=BCM4318)

---

### Post by SoFl W on 2010-02-11
Is this topic posted twice?
[http://ubuntuforums.org/showthread.php?t=1403278](http://ubuntuforums.org/showthread.php?t=1403278)

---

### Post by bkratz on 2010-02-11
> **retro_killa said:**
> Help me please.... I would like to get this laptop online via WiFi.

PS... I am on a different laptop right now running Windows 7 & I hate it. 

So please help me thanks

:)

You might also look at this thread.

[http://ubuntuforums.org/showthread.php?t=1055078&highlight=BCM4318](http://ubuntuforums.org/showthread.php?t=1055078&highlight=BCM4318)

Does look familiar doesn't it.

---

### Post by retro_killa on 2010-02-12
Help please if anyone knows how to help me that would be great I would love to dive back into using Ubuntu but I need my Wi-Fi to work as all my other computers are hard wired into the internet & this laptop will be the using Wi-Fi only

---

