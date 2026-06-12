---
title: "Pangolin hangs when connecting to Realtek RTL 8185 chipset adapter"
date: 2012-08-01
forum: Networking &amp; Wireless
---

### Post by JoseArmandoJeronymo on 2012-08-01
Hello!

I’m trying to make a sort of home theater from an older box (Pentium 2600 MHz, 512 MB RAM) running Lubuntu and with the following OS version as given by

$ cat /etc/lsb-release; uname -a:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux AsdrubalDesArts 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:46:35 UTC 2012 i686 i686 i386 GNU/Linux

This box has always been connected to a wired network without any problems. To avoid laying cables around the house I bought a wireless adapter from Brazilian maker Intelbras. Once installed and the driver installed, the adapter worked fine in the Windows XP partition that the box originally had but hang when I tried to boot with the Ubuntu 10.04 partition.

I made a fresh install of Lubuntu 12.04 erasing all previous HD content and it hang at boot as well. Then I tested the adapter on my production box currently with Precise and it too hang.

Both boxes booted fine when the adapter board was removed. Abandoning tests on the production machine, at some point I deleted network-manager from the Lubuntu one and installed wicd instead. The Lubunu box then booted without problems and the wicd GUI interface showed the wired network, but though the adapter was securely installed its LED was neither on nor blinking and the interface warned of no wireless connection. 

Searching for a solution, I run through several steps as follows.

First I got the PCI device list with vendor/chipset information from

$ lspci -nn:
```

00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [8086:2560] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 03)
00:1d.0 USB controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 82)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 02)
01:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
01:09.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

```

The last but one line shows the chipset to be 8185. I then googled the Linux kernel database in cateee.net/lkddb/ as "10ec:8185" site:cateee.net/lkddb/ which informed the driver/module for chipset 8185 to be rtl8180.

At that stage, from iwconfig, the system did not recognize a wireless card:

~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

This was expected as the rtl8180 module did not appear to be loaded:

~$ lsmod

```

Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39553  1 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
snd_intel8x0           33455  1 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
ppdev                  12849  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  9 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87213  0 
serio_raw              13027  0 
soundcore              14635  1 snd
shpchp                 32325  0 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
joydev                 17393  0 
i915                  414668  2 
parport_pc             32114  1 
drm_kms_helper         45466  1 i915
mac_hid                13077  0 
drm                   197692  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
8139too                23283  0 
8139cp                 22633  0 
floppy                 60310  0 
usbhid                 41906  0 
hid                    77367  1 usbhid

```

I used modprobe to load the module:

~$ sudo modprobe rtl8180

~$ lsmod

```

Module                  Size  Used by
arc4                   12473  2 
rtl8180                35880  0 
mac80211              436455  1 rtl8180
eeprom_93cx6           12653  1 rtl8180
cfg80211              178679  2 rtl8180,mac80211
nls_utf8               12493  1 
isofs                  39553  1 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
snd_intel8x0           33455  1 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
ppdev                  12849  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  9 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87213  0 
serio_raw              13027  0 
soundcore              14635  1 snd
shpchp                 32325  0 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
joydev                 17393  0 
i915                  414668  2 
parport_pc             32114  1 
drm_kms_helper         45466  1 i915
mac_hid                13077  0 
drm                   197692  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
8139too                23283  0 
8139cp                 22633  0 
floppy                 60310  0 
usbhid                 41906  0 
hid                    77367  1 usbhid

```

The rtl8180 module appears in the third line of the above output however not used by any device. Nevertheless, iwconfig now detected the wireless card and caleds it wlan0:

~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: on
          
eth0      no wireless extensions.

At this point I opened wicd GUI and set wlan0 to be the default wireless interface (eth0 being the default wired one, which was operational all this time).

wicd did then manage to detect my wireless router (HOMENET) and another one, which I assume to be my next door neighbour’s. However, when I tried to connect to the wireless network the computer again hungs. The moment of hanging is not constant and In one occasion the wicd status bar showed:

wicd HOMENET: Putting interface down

It should add that I tried the above both with and without compat-wireless for kernel 3 installed (linux-backports-modules-cw-3.3-3.2.0-23-generic) with roughly the same results (wicd took a bit longer to hang with compat-wireless).

As far as I understand this, the driver has been loaded and the card recognized and got functional enough to figure out the networks on the environment. However an attempt to connect causes a crash. This is syslog output preceeding a crash:

```

Jul 31 12:39:59 AsdrubalDesArts kernel: [ 2331.059776] cfg80211: Calling CRDA to update world regulatory domain
Jul 31 12:39:59 AsdrubalDesArts kernel: [ 2331.072568] cfg80211: World regulatory domain updated:
Jul 31 12:39:59 AsdrubalDesArts kernel: [ 2331.072575] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul 31 12:39:59 AsdrubalDesArts kernel: [ 2331.072580] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 31 12:39:59 AsdrubalDesArts kernel: [ 2331.072584] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 31 12:39:59 AsdrubalDesArts kernel: [ 2331.072587] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 31 12:39:59 AsdrubalDesArts kernel: [ 2331.072591] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 31 12:39:59 AsdrubalDesArts kernel: [ 2331.072595] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 31 12:39:59 AsdrubalDesArts kernel: [ 2331.144987] rtl8180 0000:01:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.266947] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.266954] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.266958] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.266962] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.266965] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.266969] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.266972] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.266976] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.266980] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.266984] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.266987] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.266991] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.266994] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.266998] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.267002] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.267006] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.267009] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.267013] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.267016] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.267020] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.267023] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.267027] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.267031] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.267035] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.267038] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.267042] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.267046] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.267050] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.300836] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Jul 31 12:40:00 AsdrubalDesArts kernel: [ 2331.304558] ieee80211 phy0: hwaddr 001a3f7c9ba8, RTL8185vD + rtl8225z2

```

BTW, I have also tried to install the windows driver vith nsiwrapper but could never manage to compile the latter. Anyway, I believe the driver/module is installed.


I’m probably missing something simple here. Help and suggestions would be most welcome.

Thanks in advance,

J A J

---

