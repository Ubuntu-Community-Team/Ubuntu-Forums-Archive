---
title: "Hauppage PVR 150 works oknly on MythTv?"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by AthlonMDK on 2007-04-29
I got a PVR 150 tv card. Problem is that i cannot configure mythtv.

I followed this guide:

[https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O)

But i always get this problem:

Access denied for user: 'mythtv@localhost'

tried to solve via this guide:

[https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting)

still same issue.

What i am wondering is there another tv tuner app that works with the PVR 150. 

Also because i find it redicule to have to run a mysql server only to watch tv..

btw card is ok:
cat /dev/video0 > test.capture gives a snow image. seems ok

dmesg output card, card is dectected ok:
> 
[   14.744000] ivtv:  ==================== START INIT IVTV ====================
[   14.744000] ivtv:  version 0.10.1 (tagged release) loading
[   14.744000] ivtv:  Linux version: 2.6.20-15-generic SMP mod_unload 586 
[   14.744000] ivtv:  In case of problems please include the debug info between
[   14.744000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   14.744000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   14.744000] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   14.744000] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   14.744000] ACPI: PCI Interrupt 0000:03:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 21
[   14.756000] nvidia: module license 'NVIDIA' taints kernel.
[   15.008000] ACPI: PCI Interrupt Link [APC7] enabled at IRQ 16
[   15.008000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [APC7] -> GSI 16 (level, low) -> IRQ 21
[   15.008000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   15.024000] hdb: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   15.024000] Uniform CD-ROM driver Revision: 3.20
[   15.408000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   15.624000] ivtv0: Encoder revision: 0x02050032
[   15.624000] ivtv0: Recommended firmware version is 0x02060039.
[   15.684000] tveeprom 2-0050: Hauppauge model 26559, rev F089, serial# 9336837
[   15.684000] tveeprom 2-0050: tuner model is TCL MFPE05 2 (idx 89, type 38)
[   15.684000] tveeprom 2-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
[   15.684000] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[   15.684000] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[   15.684000] tveeprom 2-0050: has radio, has no IR receiver, has no IR transmitter
[   15.684000] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   15.704000] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   15.704000] tda9887 2-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   15.708000] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   15.740000] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   20.536000] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   20.656000] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   20.720000] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   20.720000] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   20.720000] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   20.720000] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   20.720000] ivtv0: Registered device radio0 for encoder radio
[   20.720000] tuner 2-0061: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))


Tried TVTIME but get error:
> could not open capture device /dev/video0

Zapping Hangs when going to preferences

XawTV does not even start: 
> X error failed on request: XF86DGANoDirectVideoMode

Can someone please help me to watch tv without having a mysql server to run

---

### Post by NerdTv on 2007-05-26
I know it has been a while since you posted but I have a PVR150 and I use **VLC** to watch tv and the **at** command to record( every once and a while) They both work great.

VLC 

at    [http://ubuntuforums.org/showthread.php?t=431793]("http://ubuntuforums.org/showthread.php?t=431793")

Open VLC > File> Capture Device> PVR  then select you video device... I made a button I added to the top panel with this command    ** vlc pvr:// :pvr-device="/dev/video0" ** So it will automaticly open VLC with my PVR

The only problem I had was to change channels you have to use the command    **ivtv-tune -c**  ***CHANNEL#***
But since I had a Hauppauge remote i used lircd and irexec with a nifty python script called ivtv-channel.py to change channels... So far everything works great... I am working on getting an on screen display to work so i can *see* what channel # that i am on.

---

### Post by fenian on 2007-05-26
You can use mplayer

> sudo apt-get install mplayer

to watch tv open a termial  run...

> mplayer /dev/video0

to change channels open another terminal and run

> ivtv-tune -c # -d /dev/video0

replace # with the chael you want to watch.

---

