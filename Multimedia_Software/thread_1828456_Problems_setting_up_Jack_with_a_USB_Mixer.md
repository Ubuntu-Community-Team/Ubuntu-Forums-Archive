---
title: "Problems setting up Jack with a USB Mixer"
date: 2011-08-18
forum: Multimedia Software
---

### Post by IndigentToad on 2011-08-18
So let be start this off by letting you know I'm not really 100% up to speed on Ubuntu. I'm a recent convert from Vista, so bare with me...

I'm setting up a small home recording system for my daughter. Using a Toshiba Satellite laptop w/ Natty Narwhal. Using Ardour as my DAW and Jack is the audio server. My mixing board is a Alesis Multimix 4 USB. 

Problem is - I have no sound - in or out.

I've played with the settings and read some of the other forum posts, but I'm lost. Here's my settings:

[ 8195.622165] USB Mass Storage support registered.
[ 8196.622613] scsi 2:0:0:0: Direct-Access     RIM      BlackBerry SD    0003 PQ: 0 ANSI: 4 CCS
[ 8196.623827] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 8196.630276] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 8381.508204] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 8381.508215] cfg80211: Restoring regulatory settings
[ 8381.508225] cfg80211: Calling CRDA to update world regulatory domain
[ 8382.268677] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 8382.268688] cfg80211: World regulatory domain updated:
[ 8382.268691] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 8382.268696] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8382.268700] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 8382.268705] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 8382.268709] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8382.268713] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8382.909748] wlan0: authenticate with 00:1f:90:df:c3:9e (try 1)
[ 8382.911809] wlan0: authenticated
[ 8382.911905] wlan0: associate with 00:1f:90:df:c3:9e (try 1)
[ 8382.913931] wlan0: RX AssocResp from 00:1f:90:df:c3:9e (capab=0x411 status=0 aid=3)
[ 8382.913940] wlan0: associated

Bus 005 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 08bb:2900 Texas Instruments Japan PCM2900 Audio Codec
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0fca:8004 Research In Motion, Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with ALC202 at irq 17
1 [default        ]: USB-Audio - USB Audio CODEC 
                      Burr-Brown from TI               USB Audio CODEC  at usb-0000:00:1d.1-1, full s

 0 snd_intel8x0
 1 snd_usb_audio


Any help would be greatly appreciated!

`toad

---

