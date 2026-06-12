---
title: "Video Quality for TerraTec Cinergy TStick RC HD"
date: 2013-01-09
forum: Multimedia Software
---

### Post by didli on 2013-01-09
Hi to you all !
I'm trying to get TV from a TerraTec Cinergy TStick RC HD.
lsusb :
```
Bus 001 Device 002: ID 0ccd:00d3 TerraTec Electronic GmbH
```
dmesg | grep dvb :
```
[   11.337323] usb 1-1: dvb_usb_v2: found a 'TerraTec Cinergy T Stick RC (Rev. 3)' in warm state
[   11.342839] usbcore: registered new interface driver dvb_usb_rtl28xxu
[   11.408680] usb 1-1: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[   11.589814] usb 1-1: dvb_usb_v2: schedule remote query interval to 400 msecs
[   11.602223] usb 1-1: dvb_usb_v2: 'TerraTec Cinergy T Stick RC (Rev. 3)' successfully initialized and connected

```
Everything seems fine just connecting the stick. 
Scans works mostly pretty well, although I have a lot of warnings doing so
w_scan -c FR -X > channels.conf :
```
490000: (time: 00:27) (time: 00:28) signal ok:
	QAM_AUTO f = 490000 kHz I999B8C999D999T999G999Y999
undefined coderate HP
	new transponder:
	   (QAM_64   f = 4294967 kHz I999B8C999D0T8G8Y0) 0x405A
```
But when I tried kaffeine or me-tv, quality is amazingly bad, worst I had with a TV card. A lot of glitches, corrupt lines, I can't hear a sound : Exactly as if my signal was super low ... while I'm connected to my home TV antenna !
Did someone experience the same problems ? Is there a fix ior a method to solved this ?
Thank you for your help !

---

### Post by didli on 2013-01-09
Now it's getting interesting : as I was trying to finely tune my DVB-T card, my wifi usb card disconnected (AWUS036H with rtl8187 chipset).
And Tadaaaa !
Superb TV quality incoming !!! All channels, even HD ones.
It seems there's some conflict between my usb wifi and usb TV.
Some further investigation is needed.

---

