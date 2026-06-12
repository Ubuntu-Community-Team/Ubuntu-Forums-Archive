---
title: "BC43XX install on a laptop without internet."
date: 2011-05-23
forum: Networking &amp; Wireless
---

### Post by rrdavis on 2011-05-23
Hi,

I have a dell inspiron 8600 with a ethernet card that does not work anymore so the only chance I have to make this laptop connect and be useful is to use the onboard wireless card.

I have a BCM4306 rev 2 card that I tried to setup using this link:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

I performed the b43 no internet access section.  there were no issues until I hit section 4:

[B]Step 4.

Under the desktop menu System > Administration > Hardware/Additional Drivers, the b43 drivers can be activated for use.[/B]

The b43 drivers can not be activated.  It is not even listed in there!

Here are some outputs:

lspci

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

lsmod

Module                  Size  Used by
b43legacy             127415  0 
b43                   296610  0 
ssb                    45942  2 b43legacy,b43
mac80211              257001  2 b43legacy,b43
cfg80211              156212  3 b43legacy,b43,mac80211
nls_utf8               12493  1 
isofs                  39571  1 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
radeon                896428  3 
arc4                   12473  2 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
pcmcia                 39671  0 
ttm                    65184  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 radeon
joydev                 17322  0 
drm                   180037  5 radeon,ttm,drm_kms_helper
yenta_socket           27230  0 
snd_timer              28659  2 snd_pcm,snd_seq
ppdev                  12849  0 
pcmcia_rsrc            18292  1 yenta_socket
binfmt_misc            13213  1 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
irda                  185091  0 
dcdbas                 14054  0 
psmouse                73312  0 
soundcore              12600  1 snd
parport_pc             32111  1 
i2c_algo_bit           13184  1 radeon
video                  18951  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
shpchp                 32345  0 
serio_raw              12990  0 
crc_ccitt              12595  1 irda
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core


What should  I do next?
I saw this in the doc:

Note: On Ubuntu 11.04 installing the 'firmware-b43-installer' package takes care of the downloading and installation of the b43 driver.

but I don't think I can use that since I don't have internet.

Thanks for any help you can provide.

Ryan

---

### Post by mikewhatever on 2011-05-23
The module is installed and loaded, if you can't see wireless networks around you, try rebooting.
```
b43legacy 127415 0
b43 296610 0 
```

---

### Post by rrdavis on 2011-05-24
Thanks for your quick reply.  It indeed was working already. I hadn't tried double clicking on the wireless icon in the panel.

Thanks!

Ryan

---

