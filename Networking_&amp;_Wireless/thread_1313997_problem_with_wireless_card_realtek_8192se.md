---
title: "problem with wireless card realtek 8192se"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by chulu on 2009-11-04
hey guys,
at first sorry for my english, im from german and it is not so great.
so i try to explain my prloblem, i hope for help because really the last 2 weeks im sitting on this problem and try to fix it. i thin i have read all the web :). have found some solution but it didn helps.
i was a long time a windows user, i change to linux because of many reasons and i want to use it.
but i cant without a correct wireless connection.
i have a laptop with new hardware, everythings works but i cant use my wireless card.
s now i give some facts about my hardware  :

i use an Samsung SA21-Aura T6400 Sura with a wireless realtek 8192se chip, on ubuntu 9.10 64bit

lspci :

```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)
06:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4380 (rev 10)
jtee@DaMaschine:~$ 

```lsusb:

```

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0ac8:c335 Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 05e3:1205 Genesys Logic, Inc. Afilias Optical Mouse H3003
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```uname-r:
2.6.31-14-generic

ifconfig:
```
tee@DaMaschine:~$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:24:54:08:1a:24  
          inet Adresse:192.168.1.2  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6-Adresse: fe80::224:54ff:fe08:1a24/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:5997 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5237 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:6335082 (6.3 MB)  TX bytes:801653 (801.6 KB)
          Interrupt:19 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


```iwconfig:
```

jtee@DaMaschine:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jtee@DaMaschine:~$ 

```lsmod:

```
  lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_atihdmi     4320  1 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  2 
snd_pcm_oss            44704  0 
snd_hda_codec          87584  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_mixer_oss          18976  1 snd_pcm_oss
snd_hwdep               9352  1 snd_hda_codec
snd_seq_dummy           3460  0 
snd_pcm                93160  3 snd_hda_intel,snd_pcm_oss,snd_hda_codec
snd_seq_oss            33440  0 
joydev                 13088  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          3872  0 
snd_timer              26992  2 snd_pcm,snd_seq
uvcvideo               65260  0 
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
ip_tables              21200  1 iptable_filter
lp                     11908  0 
fglrx                2234552  33 
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport                40528  2 ppdev,lp
x_tables               25832  1 ip_tables
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_pcm_oss,snd_hda_codec,snd_mixer_oss,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                57124  0 
soundcore               9088  1 snd
serio_raw               6596  0 
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
usbhid                 43968  0 
video                  23612  0 
output                  3680  1 video
sky2                   55556  0 
intel_agp              32816  0 

```modprobe -l :
```

modprobe -l|grep wire
kernel/drivers/char/pcmcia/ipwireless/ipwireless.ko
kernel/drivers/net/wireless/ipw2x00/ipw2100.ko
kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
kernel/drivers/net/wireless/ipw2x00/libipw.ko
kernel/drivers/net/wireless/strip.ko
kernel/drivers/net/wireless/netwave_cs.ko
kernel/drivers/net/wireless/wavelan_cs.ko
kernel/drivers/net/wireless/orinoco/orinoco.ko
kernel/drivers/net/wireless/orinoco/orinoco_cs.ko
kernel/drivers/net/wireless/orinoco/orinoco_plx.ko
kernel/drivers/net/wireless/orinoco/orinoco_pci.ko
kernel/drivers/net/wireless/orinoco/orinoco_tmd.ko
kernel/drivers/net/wireless/orinoco/orinoco_nortel.ko
kernel/drivers/net/wireless/orinoco/spectrum_cs.ko
kernel/drivers/net/wireless/airo.ko
kernel/drivers/net/wireless/airo_cs.ko
kernel/drivers/net/wireless/atmel.ko
kernel/drivers/net/wireless/atmel_pci.ko
kernel/drivers/net/wireless/atmel_cs.ko
kernel/drivers/net/wireless/at76c50x-usb.ko
kernel/drivers/net/wireless/prism54/prism54.ko
kernel/drivers/net/wireless/hostap/hostap.ko
kernel/drivers/net/wireless/hostap/hostap_cs.ko
kernel/drivers/net/wireless/hostap/hostap_plx.ko
kernel/drivers/net/wireless/hostap/hostap_pci.ko
kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko
kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko
kernel/drivers/net/wireless/rtl818x/rtl8180.ko
kernel/drivers/net/wireless/rtl818x/rtl8187.ko
kernel/drivers/net/wireless/ray_cs.ko
kernel/drivers/net/wireless/wl3501_cs.ko
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/net/wireless/zd1201.ko
kernel/drivers/net/wireless/libertas/libertas.ko
kernel/drivers/net/wireless/libertas/usb8xxx.ko
kernel/drivers/net/wireless/libertas/libertas_cs.ko
kernel/drivers/net/wireless/libertas/libertas_sdio.ko
kernel/drivers/net/wireless/libertas/libertas_spi.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
kernel/drivers/net/wireless/adm8211.ko
kernel/drivers/net/wireless/mwl8k.ko
kernel/drivers/net/wireless/iwlwifi/iwlcore.ko
kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
kernel/drivers/net/wireless/rt2x00/rt61pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
kernel/drivers/net/wireless/rt2x00/rt73usb.ko
kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
kernel/drivers/net/wireless/p54/p54common.ko
kernel/drivers/net/wireless/p54/p54usb.ko
kernel/drivers/net/wireless/p54/p54pci.ko
kernel/drivers/net/wireless/p54/p54spi.ko
kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko
kernel/drivers/net/wireless/ath/ath.ko
kernel/drivers/net/wireless/mac80211_hwsim.ko
kernel/drivers/net/wireless/wl12xx/wl12xx.ko
kernel/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.ko
kernel/drivers/media/dvb/firewire/firedtv.ko
kernel/drivers/firewire/firewire-core.ko
kernel/drivers/firewire/firewire-ohci.ko
kernel/drivers/firewire/firewire-sbp2.ko
kernel/drivers/firewire/firewire-net.ko
kernel/drivers/w1/wire.ko
kernel/net/wireless/cfg80211.ko
kernel/net/wireless/lib80211.ko
kernel/net/wireless/lib80211_crypt_wep.ko
kernel/net/wireless/lib80211_crypt_ccmp.ko
kernel/net/wireless/lib80211_crypt_tkip.ko

```i tried ndiswrapper, but it always said the ndiswrapper.ko couldn be found and things like that.

so yesterday i found this :  [http://www.linuxforen.de/forums/showthread.php?t=264331](http://www.linuxforen.de/forums/showthread.php?t=264331)

there is a link to a original driver from realtek for my card but i have problems to compile and to use it.
when i start the make file i get :

```

jtee@DaMaschine:~/Downloads/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192$ make
make -C /lib/modules/2.6.31-14-generic/build M=/home/jtee/Downloads/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192 CC=gcc modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/jtee/Downloads/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192/rtl_core.o
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from include/linux/device.h:22,
                 from include/linux/pci.h:53,
                 from /home/jtee/Downloads/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192/rtl_core.c:46:
include/linux/mmzone.h:18:26: error: linux/bounds.h: No such file or directory
include/linux/mmzone.h:251:5: warning: "MAX_NR_ZONES" is not defined
include/linux/mmzone.h:253:7: warning: "MAX_NR_ZONES" is not defined
include/linux/mmzone.h:255:7: warning: "MAX_NR_ZONES" is not defined
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from include/linux/device.h:22,
                 from include/linux/pci.h:53,
                 from /home/jtee/Downloads/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192/rtl_core.c:46:
include/linux/mmzone.h:288: error: &#8216;MAX_NR_ZONES&#8217; undeclared here (not in a function)
In file included from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/pci.h:4,
                 from include/linux/pci.h:1112,
                 from /home/jtee/Downloads/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192/rtl_core.c:46:
include/linux/mm.h:444:63: warning: "NR_PAGEFLAGS" is not defined
include/linux/mm.h:492:62: warning: "NR_PAGEFLAGS" is not defined
/home/jtee/Downloads/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192/rtl_core.c: In function &#8216;rtl8192_alloc_rx_desc_ring&#8217;:
/home/jtee/Downloads/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192/rtl_core.c:2778: warning: passing argument 2 of &#8216;pci_map_single&#8217; makes pointer from integer without a cast
include/asm-generic/pci-dma-compat.h:33: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217;
/home/jtee/Downloads/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192/rtl_core.c: In function &#8216;rtl8192_rx&#8217;:
/home/jtee/Downloads/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192/rtl_core.c:4436: warning: passing argument 2 of &#8216;pci_map_single&#8217; makes pointer from integer without a cast
include/asm-generic/pci-dma-compat.h:33: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217;
make[2]: *** [/home/jtee/Downloads/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192/rtl_core.o] Fehler 1
make[1]: *** [_module_/home/jtee/Downloads/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.31-14-generic'
make: *** [modules] Fehler 2

```and then sudo make install :

```

sudo] password for jtee: 
make -C /lib/modules/2.6.31-14-generic/build M= CC=gcc modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.31-14-generic'
scripts/kconfig/conf -s arch/x86/Kconfig
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.31-14-generic'
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.31-14-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** Keine Regel vorhanden, um das Target »kernel/bounds.c«, 
  benötigt von »kernel/bounds.s«, zu erstellen.  Schluss.
make[1]: *** [prepare0] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.31-14-generic'
make: *** [modules] Fehler 2
jtee@DaMaschine:~/Downloads/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192$ 

```after copmiling it i ad i t: 
```

sudo insmod r8192se_pci.ko
jtee@DaMaschine:~/Downloads/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192$ modinfo r8192se_pci
ERROR: modinfo: could not find module r8192se_pci
jtee@DaMaschine:~/Downloads/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192$ modinfo r8192se_pci.ko
filename:       r8192se_pci.ko
license:        GPL
version:        V 1.1
author:         Copyright(c) 2008 - 2010 Realtek Corporation <wlanfae@realtek.com>
description:    Linux driver for Realtek RTL819x WiFi cards
srcversion:     EF673E344F62CFECB696ED5
alias:          pci:v000010ECd00008174sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008173sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008172sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008171sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.31.4 SMP mod_unload modversions 
parm:           ifname: Net interface name, wlan%d=default (charp)
parm:           hwwep: Try to use hardware WEP support(default use hw. set 0 to use software security) (int)
parm:           channels: Channel bitmask for specific locales. NYI (int)


```and now modprobe -l|grep 819
kernel/drivers/media/video/bt819.ko
kernel/drivers/staging/rtl8192su/r8192s_usb.ko
kernel/drivers/staging/rtl8192su/ieee80211-rsl.ko
kernel/drivers/staging/rtl8192su/ieee80211/ieee80211_crypt.ko
kernel/drivers/staging/rtl8192su/ieee80211/ieee80211_crypt_tkip.ko
kernel/drivers/staging/rtl8192su/ieee80211/ieee80211_crypt_ccmp.ko
kernel/drivers/staging/rtl8192su/ieee80211/ieee80211_crypt_wep.ko

ls mod show it :
lsmod
Module                  Size  Used by
r8192se_pci           453960  0 

bit when i use iwconfig i still see no wlan card
```

mesg|grep 819
[    3.819143] PM: Starting manual resume from disk
[    3.819146] PM: Resume from partition 8:5
[    3.819148] PM: Checking hibernation image.
[    3.819276] PM: Resume from disk failed.
[   10.404819] type=1505 audit(1257333526.174:19): operation="profile_replace" pid=888 name=/usr/lib/cups/backend/cups-pdf
[ 2128.206026] Linux kernel driver for RTL8192 based WLAN cards

```now i search help and hope you have enough informations. because alone i tried and i couldn fix it. i hope there is some body who had same problem or can help.

greets from germany.

[edit]
when i try the solution to change the first line in the make file from  ```
 
NIC_SELECT = RTL8192SE 
```

to

```

NIC_SELECT = RTL8192E

```

and compiling it, i get : 

```

~/Downloads/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192$ make clean
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
jtee@DaMaschine:~/Downloads/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192$ sudo make clean
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
jtee@DaMaschine:~/Downloads/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192$ sudo make
make -C /lib/modules/2.6.31-14-generic/build M= CC=gcc modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.31-14-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** Keine Regel vorhanden, um das Target »kernel/bounds.c«, 
  benötigt von »kernel/bounds.s«, zu erstellen.  Schluss.
make[1]: *** [prepare0] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.31-14-generic'
make: *** [modules] Fehler 2
jtee@DaMaschine:~/Downloads/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192$ sudo make install
make -C /lib/modules/2.6.31-14-generic/build M= CC=gcc modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.31-14-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** Keine Regel vorhanden, um das Target »kernel/bounds.c«, 
  benötigt von »kernel/bounds.s«, zu erstellen.  Schluss.
make[1]: *** [prepare0] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.31-14-generic'
make: *** [modules] Fehler 2
jtee@DaMaschine:~/Downloads/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192$ 


```


 [/edit]

---

### Post by dvlchd3 on 2009-11-04
Gutten Tag!  and welcome to the forums.

Try this link:
[http://forum.novatech.co.uk/showthread.php?t=15068](http://forum.novatech.co.uk/showthread.php?t=15068)

---

### Post by chulu on 2009-11-04
Thanks for the quick answer, i will take a look to the link

---

### Post by chulu on 2009-11-04
hi 

i have  tried the instruction but i didn work.

so here is what i get ```
  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jtee@DaMaschine:~$ lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_atihdmi     4320  1 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
joydev                 13088  0 
snd_hwdep               9352  1 snd_hda_codec
snd_seq_dummy           3460  0 
snd_pcm_oss            44704  0 
snd_seq_oss            33440  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lp                     11908  0 
iptable_filter          3872  0 
psmouse                57124  0 
serio_raw               6596  0 
uvcvideo               65260  0 
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
parport                40528  2 ppdev,lp
ip_tables              21200  1 iptable_filter
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_seq_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fglrx                2234552  33 
v4l2_compat_ioctl32    13344  1 videodev
x_tables               25832  1 ip_tables
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
sky2                   55556  0 
usbhid                 43968  0 
video                  23612  0 
output                  3680  1 video
intel_agp              32816  0 
jtee@DaMaschine:~$ cd /usr/srcls
bash: cd: /usr/srcls: No such file or directory
jtee@DaMaschine:~$ cd /usr/src
jtee@DaMaschine:/usr/src$ ls
fglrx-8.660
linux-headers-2.6.31-14
linux-headers-2.6.31-14-generic
rtl8192se_linux_2.6.0010.1012.2009_64bit.tar.gz
rtl8192se_linux_2.6.0010.1020.2009_64bit
jtee@DaMaschine:/usr/src$ rtl8192se_linux_2.6.0010.1020.2009_64bit
rtl8192se_linux_2.6.0010.1020.2009_64bit: command not found
jtee@DaMaschine:/usr/src$ cd rtl8192se_linux_2.6.0010.1020.2009_64bit
jtee@DaMaschine:/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit$ ls
firmware     RadioPower.sh                wlan0dhcp
HAL          readme.txt                   wlan0down
ieee80211    release_note                 wlan0up
ifcfg-wlan0  runwpa                       wpa1.conf
Makefile     wireless-rtl-ac-dc-power.sh  wpa_supplicant-0.5.10.tar.gz
jtee@DaMaschine:/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit$ sudo make clean
[sudo] password for jtee: 
make[1]: Betrete Verzeichnis '/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Verlasse Verzeichnis '/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192'
make[1]: Betrete Verzeichnis '/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit/ieee80211'
rm -fr *.mod.c *.mod *.o .*.cmd *.mod.* *.ko *.o *~
rm -rf .tmp_versions
rm -rf Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Verlasse Verzeichnis '/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit/ieee80211'
jtee@DaMaschine:/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit$ make
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/rtl_core.o
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from include/linux/device.h:22,
                 from include/linux/pci.h:53,
                 from /usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/rtl_core.c:46:
include/linux/mmzone.h:18:26: error: linux/bounds.h: No such file or directory
include/linux/mmzone.h:251:5: warning: "MAX_NR_ZONES" is not defined
include/linux/mmzone.h:253:7: warning: "MAX_NR_ZONES" is not defined
include/linux/mmzone.h:255:7: warning: "MAX_NR_ZONES" is not defined
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from include/linux/device.h:22,
                 from include/linux/pci.h:53,
                 from /usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/rtl_core.c:46:
include/linux/mmzone.h:288: error: ‘MAX_NR_ZONES’ undeclared here (not in a function)
In file included from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/pci.h:4,
                 from include/linux/pci.h:1112,
                 from /usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/rtl_core.c:46:
include/linux/mm.h:444:63: warning: "NR_PAGEFLAGS" is not defined
include/linux/mm.h:492:62: warning: "NR_PAGEFLAGS" is not defined
/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/rtl_core.c:8319: fatal error: opening dependency file /usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/.rtl_core.o.d: Permission denied
compilation terminated.
make[2]: *** [/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/rtl_core.o] Fehler 1
make[1]: *** [_module_/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.31-14-generic'
make: *** [all] Fehler 2
jtee@DaMaschine:/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit$ sudo make install
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/rtl_core.o
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from include/linux/device.h:22,
                 from include/linux/pci.h:53,
                 from /usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/rtl_core.c:46:
include/linux/mmzone.h:18:26: error: linux/bounds.h: No such file or directory
include/linux/mmzone.h:251:5: warning: "MAX_NR_ZONES" is not defined
include/linux/mmzone.h:253:7: warning: "MAX_NR_ZONES" is not defined
include/linux/mmzone.h:255:7: warning: "MAX_NR_ZONES" is not defined
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from include/linux/device.h:22,
                 from include/linux/pci.h:53,
                 from /usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/rtl_core.c:46:
include/linux/mmzone.h:288: error: ‘MAX_NR_ZONES’ undeclared here (not in a function)
In file included from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/pci.h:4,
                 from include/linux/pci.h:1112,
                 from /usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/rtl_core.c:46:
include/linux/mm.h:444:63: warning: "NR_PAGEFLAGS" is not defined
include/linux/mm.h:492:62: warning: "NR_PAGEFLAGS" is not defined
make[2]: *** [/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192/rtl_core.o] Fehler 1
make[1]: *** [_module_/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.31-14-generic'
make: *** [all] Fehler 2
jtee@DaMaschine:/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit$ ls
firmware     RadioPower.sh                wlan0dhcp
HAL          readme.txt                   wlan0down
ieee80211    release_note                 wlan0up
ifcfg-wlan0  runwpa                       wpa1.conf
Makefile     wireless-rtl-ac-dc-power.sh  wpa_supplicant-0.5.10.tar.gz
jtee@DaMaschine:/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit$ lsmod |grep r8192se_pci
jtee@DaMaschine:/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jtee@DaMaschine:/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit$ lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_atihdmi     4320  1 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
joydev                 13088  0 
snd_hwdep               9352  1 snd_hda_codec
snd_seq_dummy           3460  0 
snd_pcm_oss            44704  0 
snd_seq_oss            33440  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lp                     11908  0 
iptable_filter          3872  0 
psmouse                57124  0 
serio_raw               6596  0 
uvcvideo               65260  0 
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
parport                40528  2 ppdev,lp
ip_tables              21200  1 iptable_filter
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_seq_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fglrx                2234552  33 
v4l2_compat_ioctl32    13344  1 videodev
x_tables               25832  1 ip_tables
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
sky2                   55556  0 
usbhid                 43968  0 
video                  23612  0 
output                  3680  1 video
intel_agp              32816  0 
jtee@DaMaschine:/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit$ lsmod |grep r8192se_pci
jtee@DaMaschine:/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit$ lsmod |grep r8192se_pci
jtee@DaMaschine:/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit$ sudo modprobe r8192se_pci
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module r8192se_pci not found.
jtee@DaMaschine:/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit$ cd HAL
jtee@DaMaschine:/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL$ ls
rtl8192
jtee@DaMaschine:/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL$ cd rtl8192
jtee@DaMaschine:/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192$ ls
authors       r8190P_hwimg.c   r8192E_hw.h     r8192SE_hw.h       r8192S_led.h     r8192S_rtl6052.c   r819xE_phy.c     rtl_cam.h     rtl_eeprom.h   rtl_ps.c
changes       r8190P_hwimg.h   r8192E_hwimg.c  r8192S_firmware.c  r8192S_mp.c      r8192S_rtl6052.h   r819xE_phy.h     rtl_core.c    rtl_ethtool.c  rtl_ps.h
copying       r8190_rtl8256.c  r8192E_hwimg.h  r8192S_firmware.h  r8192S_mp.h      r819xE_cmdpkt.c    r819xE_phyreg.h  rtl_core.h    rtl_mesh.c     rtl_wx.c
license       r8190_rtl8256.h  r8192SE_def.h   r8192S_hwimg.c     r8192S_phy.c     r819xE_cmdpkt.h    rtl8192se.c      rtl_debug.c   rtl_mesh.h     rtl_wx.h
Makefile      r8192E_dm.c      r8192S_Efuse.c  r8192S_hwimg.h     r8192S_phy.h     r819xE_firmware.c  rtl8192se.h      rtl_debug.h   rtl_pm.c
r8190P_def.h  r8192E_dm.h      r8192S_Efuse.h  r8192S_led.c       r8192S_phyreg.h  r819xE_firmware.h  rtl_cam.c        rtl_eeprom.c  rtl_pm.h
jtee@DaMaschine:/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL/rtl8192$ cd ..
jtee@DaMaschine:/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit/HAL$ cd ..
jtee@DaMaschine:/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit$ lsmod |grep r8192se_pci
jtee@DaMaschine:/usr/src/rtl8192se_linux_2.6.0010.1020.2009_64bit$ 

```

---

### Post by northd_tech on 2009-11-24
Hi chulu.  dvlchd3 has some good tips above (but I've got my suspicions that the 8192SE and 8192E might not really be source-compatible).  That "sudo su" command is a good tip though:

[http://forum.novatech.co.uk/showpost.php?p=208588&postcount=12](http://forum.novatech.co.uk/showpost.php?p=208588&postcount=12)

Also see what chili555 did on this thread- that looks the easiest way to/for me:

[http://ubuntuforums.org/showthread.php?t=1329254](http://ubuntuforums.org/showthread.php?t=1329254)

---

### Post by pcrofts on 2009-11-28
I am trying to do the same thing you are. I contacted Realtek and they sent me the driver. I can get it to almost work. It connects but doesn't seem to like my WPA settings. 

I can send you the driver and you can try. Can you let me know if you are successful. There is a readme file in the archive with some basic instructions on how to make and install the driver.

There was a version of wpa_supplicant in the archive I received from realtek but to my understanding it is not required with version 9.10

Best of luck.

---

### Post by northd_tech on 2009-12-04
Hi pcrofts.

Unfortunately, that looks to be the 32-bit sourcecode, and I'm working under 64-bit Karmic 9.10 2.6.31-15-generic kernel and AMD DuoCore CPUs.  I was able to get a module to compile and install using that German page that I linked to on that thread link above.

I am now fairly certain that the Realtek 8192E is a different beast than the 8192SE, and will need different sourcecode (the module names are different, too after compiling).

Edit:  I'd also try building/installing that WPA code contained in that archive that Realtek sent you- that could fix your problem, or there could be some configuration or script issues still.

---

### Post by david3d on 2010-01-08
Check out this bug.  Towards the bottom is a version of the driver that works for both 32bit and 64bit.  I've been using it on the 64bit version of Karmic for about 2 months without any problems.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all)

I've been using the driver found in comment #134

---

### Post by jonah1980 on 2011-05-17
Can everyone please report here to get some progress going on this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/730758]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/730758")

---

