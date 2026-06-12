---
title: "unstable wireless on Toshiba Satellite L305-S5955"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by duckintheface on 2009-12-28
I have a Toshiba: Satellite L305-S5955 running Ubuntu 9.04 and Firefox 3.0.16 with all updates in place.

I seem to have a  wifi issue. I'm connected for awhile, then can't connect. Sometimes the problem is temporarily improved by resetting the modem. Sometimes it is improved by clicking on the wireless connection icon to restart the connection. But the problem recurs frequently.

There are no problems if I run from ethernet so this is apparently a wifi issue. Any suggestions would be appreciated.

Chipset is the rtl8101e/rlt8102e using the r8169 driver.

---

### Post by duckintheface on 2010-01-04
Any ideas?

---

### Post by duckintheface on 2010-01-07
Guys?  I'm still not feelin' the love.  :D

---

### Post by adam814 on 2010-01-07
Hmm...First things first: The rtl8102e is your ethernet controller, not a wifi card.

Could you post the output of "lspci"?

I have a Satellite A305 series (which may or may not be that similar) and my wireless is an Intel WiFi Link 5100AGN that uses the iwlagn driver.

---

### Post by duckintheface on 2010-01-07
Thanks Adam.  Here is lspci.

me@me-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by adam814 on 2010-01-07
Is your wireless card USB or might you have missed the last line?  There's no wifi chip listed in the output.  On mine there's a good bit more output from lspci.

Try "sudo lshw -C network".  That should hopefully show what card you have whether it's PCI or not.

---

### Post by duckintheface on 2010-01-07
No, what I showed was the entire output. The wifi is built in, not a separate USB card.  Here is lshw -C.

me@me-laptop:~$ sudo lshw -C network
[sudo] password for me: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:f2:df:20
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:24:d2:f1:76:2c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.100 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 7a:84:e9:42:85:63
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
me@me-laptop:~$

---

### Post by adam814 on 2010-01-07
Ok, looks like you have an RTL 8192 series wifi chipset.  I've seen quite a few forum threads about getting them to work, some of them with ndiswrapper, some without.

Are you using ndiswrapper?  If so make sure you're using XP drivers, not Vista/7 drivers.  Also make sure they're for the right architecture (32 vs. 64-bit).

In either case check "dmesg" for messages about the wireless.  It might give you a hint as to why it's dropping.

---

### Post by duckintheface on 2010-01-07
I get the same dmesg over and over as follows:

[543203.693637] wlan0: associated
[543322.686262] wlan0: deauthenticated
[543323.684025] wlan0: direct probe to AP 00:13:10:9f:47:c9 try 1
[543323.685637] wlan0 direct probe responded
[543323.685640] wlan0: authenticate with AP 00:13:10:9f:47:c9
[543323.687383] wlan0: authenticated
[543323.687386] wlan0: associate with AP 00:13:10:9f:47:c9
[543323.689514] wlan0: RX ReassocResp from 00:13:10:9f:47:c9 (capab=0x401 status=0 aid=3)

[543323.689517] wlan0: associated
[543442.690030] wlan0: deauthenticated
[543443.688025] wlan0: direct probe to AP 00:13:10:9f:47:c9 try 1
[543443.689652] wlan0 direct probe responded
[543443.689654] wlan0: authenticate with AP 00:13:10:9f:47:c9
[543443.692698] wlan0: authenticated
[543443.692702] wlan0: associate with AP 00:13:10:9f:47:c9
[543443.695404] wlan0: RX ReassocResp from 00:13:10:9f:47:c9 (capab=0x401 status=0 aid=3)

[543443.695406] wlan0: associated
[543562.690194] wlan0: deauthenticated
[543563.688023] wlan0: direct probe to AP 00:13:10:9f:47:c9 try 1
[543563.689671] wlan0 direct probe responded
[543563.689675] wlan0: authenticate with AP 00:13:10:9f:47:c9
[543563.691422] wlan0: authenticated
[543563.691427] wlan0: associate with AP 00:13:10:9f:47:c9
[543563.693545] wlan0: RX ReassocResp from 00:13:10:9f:47:c9 (capab=0x401 status=0 aid=3)

[543563.693548] wlan0: associated
me@me-laptop:~$ 

I am using Ubuntu unmodified so I have not done anything with wrappers.  Don't really understand how that works.  

You say I have RTL 8192 wifi chip.  How can you tell?  I don't see any mention of that in lshw -C network.

---

### Post by adam814 on 2010-01-07
It's a bit of an assumption on my part really.  I took the MAC address which is listed for your network card and did a lookup on the vendor.  It comes back as Askey Computer.  I then googled Askey Computer and the first half of your MAC address (the vendor section), which turns up a lot of posts on this forum, linuxquestions.org, etc.  Most are of people with wireless difficulties with an RTL8192 chip of some sort(apparently the 8192E and 8192SE are different somehow).

Ndiswrapper is a utility that lets you use Windows XP network drivers in Linux.  It effectively "wraps" the NDIS driver and allows it to be accessed as if it were a Linux driver.  The downside is in practice it's glitchy and doesn't have all the features a native Linux driver would.

I suspect you may need to update your firmware for the wireless card.  You're not using ndiswrapper for it, so the question is which driver you are using.  Post the output from "lsmod" and I'll see if I can pick out which one it is.

---

### Post by duckintheface on 2010-01-07
me@me-laptop:~$ lsmod
Module                  Size  Used by
usblp                  20224  0 
i915                   65540  2 
drm                    96296  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
arc4                    9856  2 
ecb                    10752  2 
snd_hda_intel         435636  5 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_hda_intel,snd_pcm_oss
rtl8187                53376  0 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
mac80211              217208  1 rtl8187
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
eeprom_93cx6           10240  1 rtl8187
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                61972  0 
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
intel_agp              34108  1 
serio_raw              13316  0 
pcspkr                 10496  0 
cfg80211               38032  2 rtl8187,mac80211
video                  25360  0 
agpgart                42696  3 drm,intel_agp
snd                    62628  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
output                 11008  1 video
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
me@me-laptop:~$

---

### Post by adam814 on 2010-01-08
Ok, you're using the rtl8187 driver.  You might try installing an updated version of it from here:
[http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

---

### Post by Nazareth_patrice on 2010-01-16
I have a Toshiba laptop U500, with rtl8191 wifi interface working with Ubuntu 9.10. First, I can't use my wireless connection, the laptop does not see it. So, I went to Realtek site, I load rl8192 driver for linux, and I done just they writed on the 'Read me' document (with make and make file), and it works now ! If you want more explanation, write at [email]pballet@spectro.ujf-grenoble.fr[/email].

---

