---
title: "PCI wireless adapter, worked fine on all previous versions, doesn&quot;t on Karmic, help.."
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by bjaz on 2009-11-11
hello all

i'm trying to get the wireless running on an old japanese sony vaio model, FS21.
the wireless adapter, a PCMCIA card, worked out the the box on the previous version installed, xubuntu, and stil does after the upgrade to karmic

yet i've installed a new Ubuntu install which we would like to use from now on.
and for a reason, the wireless does not work. i've been trying for days, to no avail.
ethernet works, but the adapter desn't appear anywhere.
when I checked for the drivers it said "no proprietary drivers available".


can somebody help me fix this ? since it works in xubuntu karmic, I think it should be pretty easy to solve.

here are the specs :

here is the info mentioned as necessary in the wifi thread :

kayo@kayo-ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
kayo@kayo-ubuntu:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
kayo@kayo-ubuntu:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 03
       serial: 00:01:4a:60:fa:c0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:b0106000-b0106fff ioport:2000(size=64)
kayo@kayo-ubuntu:~$ uname -a
Linux kayo-ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
kayo@kayo-ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic
kayo@kayo-ubuntu:~$ 

kayo@kayo-ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
kayo@kayo-ubuntu:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
kayo@kayo-ubuntu:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 03
       serial: 00:01:4a:60:fa:c0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:b0106000-b0106fff ioport:2000(size=64)
kayo@kayo-ubuntu:~$ uname -a
Linux kayo-ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
kayo@kayo-ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic
kayo@kayo-ubuntu:~$

and sudo ifconfig gives

here's the ifconfig, it's my wife's computer hence in french, let me know if this is ok :

                                       [LEFT]eth0      Link encap:Ethernet  HWaddr 00:01:4a:60:fa:c0  [/LEFT]
    [LEFT]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/LEFT]
    [LEFT]          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0[/LEFT]
    [LEFT]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/LEFT]
    [LEFT]          collisions:0 lg file transmission:1000 [/LEFT]
    [LEFT]          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)[/LEFT]
    
    [LEFT]lo        Link encap:Boucle locale  [/LEFT]
    [LEFT]          inet adr:127.0.0.1  Masque:255.0.0.0[/LEFT]
    [LEFT]          adr inet6: ::1/128 Scope:Hôte[/LEFT]
    [LEFT]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/LEFT]
    [LEFT]          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0[/LEFT]
    [LEFT]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/LEFT]
    [LEFT]          collisions:0 lg file transmission:0 [/LEFT]
    [LEFT]          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)[/LEFT]
    
    [LEFT]kayo@kayo-ubuntu:~$

there seems to be no entries for wlan0
and wmaster0....


---------------------------------------------------

now here's t the ifconfig from the karmic  xubuntu version that i woud like to get rid of (too many issues); same machine, same adapet, wireless works fine.

kayo@kayogoro:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:4a:60:fa:c0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:06:f4:04:8c:5b  
          inet adr:192.168.1.21  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::206:f4ff:fe04:8c5b/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:998 erreurs:73 :0 overruns:0 frame:0
          TX packets:672 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:1107233 (1.1 MB) Octets transmis:149687 (149.6 KB)
          Interruption:3 Adresse de base:0x2040 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

kayo@kayogoro:~$ 
 [/LEFT]


--------------------------

the card itself is 
an old WIFI AMTEL PCMCIA adapter card which worked out of the box in xubuntu jaunty, and still does after the karmic update, but simply refuses to in a new clean ubuntu 9.1 intall

the wifi card is a *ATMEL INVENTEL* Wireless Network Adapter AT76C502A. FCC ID:*KFY*-[I]WA1113
[/I]at76c502ar_e 

worked out of the box in the xubuntu and still does after the karmic update, but refuses to work in standard ubuntu which i know plan on using for this machine





thanks a milion for your help, I really cannot progress in this alone

ben

---

### Post by bjaz on 2009-11-11
where are the wifi / wireless settings kept ?
maybe I can simply copy the working xubuntu config file to the ubuntu version ?

it's strange, really, that this PCMCIA card worked out of the box on xubuntu, but doesn't on karmic
i also have the windows driver cd for this old card.

i understand everyone is busy, ad that no one os "entitled" to support, but i do think this one's quite easy to deal with, but can't manage on my own.

i'd really love to fix this

thanks
ben

---

### Post by bjaz on 2009-11-11
a lot of such help threads never get any answers, or just one from some one who just disappears.
i'm reading up on the forum as much as I can, and trying to be as precise as I can.
but if there's something i'm still not doing right, please let me know as i'm totally dependent on the forum for the resolution of this issue, and checking in to see if there's an hint /help / advice every few hours.

but whereas i could probably find my way around such issues on mac os or windows, i'm really in a void here, on what to try to get a previously working wireless wifi card to work on the new ubuntu karmic

thanks for your time, help, and understanding

ben

---

### Post by chili555 on 2009-11-11
I think our problem is that your lspci, lsusb and your lshw show nothing remotely resembling a wireless device! We don't know why and we don't have a clue how to fix what we can't see. We are mystified.

Please open a terminal and do:```
dmesg > dmesg.txt
```A text file will be created which you can post as an attachment here. Please do not paste the whole thing into your post; it's too long.

As a desperation move, you might move the card to a different PCI slot to see if it magically appears in lshw. Hey, I know it sounds crazy!

---

### Post by bjaz on 2009-11-12
thanks. sorry if I was confusing, it's a PCMCIA card, and there's only one slot for this PCMCIA card slot on this laptop - I might have written PCI in the thread title but it's actually PCMCIA

the fact that the same card works on this very same machine on Xubuntu, even after the update to 9.1 cannot be used to make it work on Ubuntu 9.1. ? 

here is the file; for the Ubuntu 9.1 install where the wifi adapter doesn't work

thanks again

---

### Post by bjaz on 2009-11-12
and though I don't know if this is of any help, here is the same file, done on the same machine with the same card but running** Xubuntu, updated to 9.1**

(I want to get rid of this since Ubuntu works  fine, and i prefer a new clean install.
 this xubuntu has numerous issues such as sound, touchpad, and diskmanagement, and we'd switched to the gnome environment anyway, so there was not much use in hanging onto it when Ubuntu works fine. 
except for the wifi. Yet in Xubuntu, the PCMCIA wifi adapter worked out of the box, and still does after the update to 9.1

here's the same document, but from the Xubuntu install on the same machine, with the same PCMCIA card, which works. hope it can help

thanks a lot

ben

---

### Post by chili555 on 2009-11-12
> sorry if I was confusing, it's a PCMCIA cardWell, that makes a difference. Please let us see:```
lspcmcia -v
```in both installations. Also, please try booting your Ubuntu (Gnome) installation with the card not inserted and then after you've logged in and the desktop is fully loaded, insert the card and run:```
dmesg
```The last few lines may give some clues as to why the card is not being recognized.

Your two dmesg listings are remarkable in that the pcmcia parts are identical; there seem to be no serious errors or warnings in either.

---

### Post by bjaz on 2009-11-12
sorry about that, thanks.

ok, i rebooted without the card in ubuntu 9.1 inserted it and ran lspcmia -v 

kayo@kayo-ubuntu:~$ lspcmcia -v
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:06:03.0)
    Configuration:    state: on    ready: unknown
            Voltage: 3.3V Vcc: 3.3V Vpp: 0.0V
Socket 0 Device 0:    [pata_pcmcia]        (bus ID: 0.0)
    Configuration:    state: on
    Product Name:   ATMEL AT76C502AR_E 
    Identification:    manf_id: 0x0000    card_id: 0x0000
            function: 6 (network)
            prod_id(1): "ATMEL" (0xabda4164)
            prod_id(2): "AT76C502AR_E" (0x4172e792)
            prod_id(3): --- (---)
            prod_id(4): --- (---)
kayo@kayo-ubuntu:~$ 


----------------------

it seems do be recognized now, but i still can't see it in the network settings.

now for dmesg

---

### Post by bjaz on 2009-11-12
and here is the same on xubuntu

Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:06:03.0)
    Configuration:    state: on    ready: unknown
            Voltage: 3.3V Vcc: 3.3V Vpp: 0.0V
Socket 0 Device 0:    [pata_pcmcia]        (bus ID: 0.0)
    Configuration:    state: on
    Product Name:   ATMEL AT76C502AR_E 
    Identification:    manf_id: 0x0000    card_id: 0x0000
            function: 6 (network)
            prod_id(1): "ATMEL" (0xabda4164)
            prod_id(2): "AT76C502AR_E" (0x4172e792)
            prod_id(3): --- (---)
            prod_id(4): --- (---)


----------

and the xubuntu dmesg

---

### Post by chili555 on 2009-11-12
I just ran:```
chili@LAPTOP60:~$ modinfo atmel_cs
filename:       /lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/atmel_cs.ko
license:        GPL
description:    Support for [COLOR="Red"]Atmel at76c50x[/COLOR] 802.11 wireless ethernet cards.
--- snip ---
```Looks like a likely candidate. Please insert the card and try:```
sudo modprobe atmel_cs
iwconfig
```Is your wireless card now recognized? If so, we can make this permanent. If not, please let me see *dmesg* after the modprobe happened.

---

### Post by bjaz on 2009-11-12
thanks.

i got this at the first try

kayo@kayo-ubuntu:~$ sudo modprobe atmel_cs
kayo@kayo-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

kayo@kayo-ubuntu:~$ 


trying again with a reboot without the card, inserting it

got the same as the above

here's the new dmesg

if config gives me

kayo@kayo-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:4a:60:fa:c0  
          inet adr:192.168.1.20  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::201:4aff:fe60:fac0/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:782 erreurs:0 :0 overruns:0 frame:0
          TX packets:713 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:851855 (851.8 KB) Octets transmis:142613 (142.6 KB)

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

---

### Post by chili555 on 2009-11-12
> PCMCIA card, worked out the the box on the previous version installed, xubuntu, and stil does after the upgrade to karmicWhen you are booted into xubuntu, and the card is inserted and working, please let me have the result of:```
lsmod > lsmod.txt
```I am curious as to what module, if not atmel_cs, is being used successfully.

---

### Post by bjaz on 2009-11-12
Id like to really thank you for the time you're investing in this, it's a great help

I need to go get some sleep now, as I have an important early meeting in the morning, but i'll check up on suggestions with my first cup of coffee


on xubuntu, i can't boot graphically since i tried to change the kernel to latest one in an attempt to fix Xubuntu's non functioning touchpad (works fine in the new Ubuntu install), but I'm getting a recovery boot- then resume normal boot which seems to work fine.

ok, in xubuntu it's

                        Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  0 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
atmel_cs                5436  0 
atmel                  35808  1 atmel_cs
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
pata_pcmcia            11228  1 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
pcmcia                 36808  2 atmel_cs,pata_pcmcia
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
tifm_sd                 9252  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
yenta_socket           24200  3 
tifm_7xx1               5372  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rsrc_nonstatic         11644  1 yenta_socket
tifm_core               7832  2 tifm_sd,tifm_7xx1
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    59204  12 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
serio_raw               5280  0 
sony_laptop            31972  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  70 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221064  1 
drm                   159584  1 i915
i2c_algo_bit            5760  1 i915
e100                   32452  0 
mii                     5212  1 e100
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

---

### Post by bjaz on 2009-11-13
it seems to be this, right?

pcmcia                 36808  2 atmel_cs,pata_pcmcia

---

### Post by chili555 on 2009-11-13
> atmel_cs 5436 0
atmel 35808 1 atmel_cs
--- snip ---
pcmcia 36808 2 atmel_cs,pata_pcmciaYep, that's it. We are left with the question: why does it work in xubuntu and not in Ubuntu (aka Gnome)? Why, even after we explicitly modprobed the correct module? The windowing system, that is XFCE or Gnome has nothing to do with kernel modules loading and attaching to an interface. This is my favorite kind of problem: everything looks perfect...except it just doesn't work!

Can you easily and conveniently re-install Ubuntu? I wonder if something went wrong in the installation that we have not yet discovered.

I am running out of ideas.

---

### Post by bjaz on 2009-11-14
> **chili555 said:**
> Yep, that's it. We are left with the question: why does it work in xubuntu and not in Ubuntu (aka Gnome)? Why, even after we explicitly modprobed the correct module? The windowing system, that is XFCE or Gnome has nothing to do with kernel modules loading and attaching to an interface. This is my favorite kind of problem: everything looks perfect...except it just doesn't work!

Can you easily and conveniently re-install Ubuntu? I wonder if something went wrong in the installation that we have not yet discovered.

I am running out of ideas.

especially since we actually switched to gnome on the xubuntu install (one of the reasons why i just want a "traditional" ubuntu install). the wifi PCMIA card worked with XFCE, and it still worked when i switched it to gnome desktop.

yet this was done from a previous install, of Xubuntu Jaunty Jackalope, which was then updated to Karmic Koala 9.1, and continued to work afterwards, not from a 9.1. xubuntu install directly.

I can re-install, i just don't want to mess up my wife's japanese windows xp partitions.
maybe the best would be to delete all the existing ubuntu and xubuntu partitions in G-Parted, and then do a clean side by side install.
it's not always crystal clear, as the japanese windows as 3 partitions, one system, one general, and the sony vaio recovery disk.

unless there's a way to specify a re-install of Ubuntu exactly where it is now.

should the install be done with the card plugged in or not (it was when the install was done)

thanks

b

---

### Post by chili555 on 2009-11-15
> unless there's a way to specify a re-install of Ubuntu exactly where it is now.The installer will propose several locations for the installation. If you run:```
sudo fdisk /dev/sda
```and enter the command 'p' for print (without the tick marks, of course), it should be apparent that three partitions are in vfat or Windows-centric file systems and several are in ext3 or other Linux-centric file systems. Then, when you re-install, be sure to accept *only* the partitioning and installation scheme that install on the Linux partitions you discovered.> the best would be to delete all the existing ubuntu and xubuntu partitions in G-Parted, and then do a clean side by side install.An excellent plan, in my opinion.

I strongly recommend a back-up of your Windows data. I have done quite a few successful side-by-side installations, but I always hope for the best and plan for the worst.

---

### Post by bjaz on 2009-11-15
ok I just did it.
deleted all the linux partitions, kept the windows one, and did a full reinstall from a checksum verified, integrity verified new CD

didn't work. unless there is something I should do to activate the wireless card
i'm working on re-installing stuff.

 This is a big letdown. i'm considering switching back to xubuntu jaunty, as at least everything worked.

thanks for your help

b

---

### Post by bjaz on 2009-11-15
I re-installed twice. once with the PCMCIA card plugged in, once without. still nothing.
everything works, now there's only the japanese windows xp and karmic desktop, but the wireless adapter won't work. it does light up but doesn't appear in the network properties, i don't understand why something which previously worked out of the box doesn't  anymore

i still have the windows driver cd, but is there really nothing i could try ?

apparently some drivers were dropped according to this thread

[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-karmic.git;a=commitdiff;h=492a320431f81088443608d61f739f4f2c207d51](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-karmic.git;a=commitdiff;h=492a320431f81088443608d61f739f4f2c207d51)


if it was working in jaunty, there is surely a way to fix this ?

and is there a way to fix the title of the thread ? it still reads PCI

thanks

ben

kayo@kayo-oppo:~$ lspcmcia -v
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:06:03.0)
    Configuration:    state: on    ready: unknown
            Voltage: 3.3V Vcc: 3.3V Vpp: 0.0V

kayo@kayo-oppo:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

