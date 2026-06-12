---
title: "PVR500 Issue"
date: 2009-01-21
forum: Mythbuntu
---

### Post by viking325i on 2009-01-21
Hi,

I've just installed 8.10, and am trying to get my PVR-500 working. However when selecting watch tv, it has a blank screen, then returns to the main menu after a few seconds.

Backend Log

2009-01-22 08:56:36.292 MainServer::HandleAnnounce Playback
2009-01-22 08:56:36.311 adding: mythbuntu as a client (events: 0)
2009-01-22 08:56:36.325 TVRec(1): Changing from None to WatchingLiveTV
2009-01-22 08:56:36.332 TVRec(1): HW Tuner: 1->1
2009-01-22 08:56:37.621 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2009-01-22 08:56:43.234 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-22 08:56:44.193 TVRec(1): Changing from WatchingLiveTV to None
2009-01-22 08:56:48.790 MPEGRec(/dev/video0) Error: select timeout - ivtv driver has stopped responding
2009-01-22 08:56:49.001 Finished recording Unknown: channel 1001
2009-01-22 08:58:58.736 Expiring 0 MBytes for 1001 @ Thu Jan 22 08:56:36 2009 => Unknown







Frontend Log


2009-01-22 08:56:36.257 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2009-01-22 08:56:36.259 Using protocol version 40
2009-01-22 08:56:36.291 TV: Attempting to change from None to WatchingLiveTV
2009-01-22 08:56:36.292 Using protocol version 40
2009-01-22 08:56:44.131 RingBuf(/var/lib/mythtv/recordings/1001_20090122085636.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/recordings/1001_20090122085636.mpg'.
2009-01-22 08:56:44.133 DPMS Deactivated 
2009-01-22 08:56:44.164 New DB connection, total: 3
2009-01-22 08:56:44.164 Connected to database 'mythconverg' at host: localhost
2009-01-22 08:56:44.191 NVP::OpenFile(): Error, file not found: /var/lib/mythtv/recordings/1001_20090122085636.mpg
2009-01-22 08:56:44.191 TV Error: StartPlayer(): NVP is not playing after 20000 msec
2009-01-22 08:56:49.013 TV Error: LiveTV not successfully started
2009-01-22 08:56:49.041 DPMS Reactivated.




Can anyone shed any light on whats going on?

---

### Post by ian dobson on 2009-01-21
Hi,

Have a look here:- [http://ubuntuforums.org/showthread.php?t=968121&highlight=pvr+500](http://ubuntuforums.org/showthread.php?t=968121&highlight=pvr+500) post #6. I had the same problem after upgraded to 8.10.

Regards
Ian Dobson

---

### Post by viking325i on 2009-01-21
> **ian dobson said:**
> Hi,

Have a look here:- [http://ubuntuforums.org/showthread.php?t=968121&highlight=pvr+500](http://ubuntuforums.org/showthread.php?t=968121&highlight=pvr+500) post #6. I had the same problem after upgraded to 8.10.

Regards
Ian Dobson

I did that this morning hoping it would work, maybe I've done something wrong, will have another go

Cheers

---

### Post by ian dobson on 2009-01-21
Hi,

Did you reboot or reload the ivtv drivers before testing again?

Regards
Ian Dobson

---

### Post by viking325i on 2009-01-21
> **ian dobson said:**
> Hi,

Did you reboot or reload the ivtv drivers before testing again?

Regards
Ian Dobson

Rebooted, I cant check til I get home tonight if its worked this time however. Did your tuners come up as Tuner0 or Tuner1 for each card?

---

### Post by kyfehr on 2009-01-21
also, make sure that your recording folder has proper permissions

---

### Post by viking325i on 2009-01-21
Ok, just tested it again, I followed the instructions on post 6, then rebooted, still the same thing?

---

### Post by ian dobson on 2009-01-22
Hi,

What to you see in your syslog? What firmware version is ivtv loading?

dmesg | grep ivtv

On my box I see:-
```

[   12.009017] ivtv: Start initialization, version 1.4.0
[   12.009280] ivtv0: Initializing card 0
[   12.009282] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   12.009485] ivtv 0000:06:08.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   12.064668] ivtv0: Autodetected WinTV PVR 500 (unit #1)
[   12.540382] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   12.672365] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   12.706001] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   12.778916] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   12.810247] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   12.850421] ivtv0: Registered device video1 for encoder MPG (9216 kB)
[   12.850462] ivtv0: Registered device video33 for encoder YUV (2048 kB)
[   12.850500] ivtv0: Registered device vbi1 for encoder VBI (1024 kB)
[   12.850541] ivtv0: Registered device video25 for encoder PCM (320 kB)
[   12.850576] ivtv0: Registered device radio1 for encoder radio
[   12.850578] ivtv0: Initialized card: WinTV PVR 500 (unit #1)
[   12.850628] ivtv1: Initializing card 1
[   12.850630] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   12.852244] ivtv 0000:06:09.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   12.906238] ivtv1: Correcting tveeprom data: no radio present on second unit
[   12.906239] ivtv1: Autodetected WinTV PVR 500 (unit #2)
[   12.912058] cx25840 2-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[   12.931321] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #1)
[   12.936893] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   12.940923] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   12.959722] ivtv1: Registered device video2 for encoder MPG (9216 kB)
[   12.959752] ivtv1: Registered device video34 for encoder YUV (2048 kB)
[   12.959780] ivtv1: Registered device vbi2 for encoder VBI (1024 kB)
[   12.959808] ivtv1: Registered device video26 for encoder PCM (320 kB)
[   12.959809] ivtv1: Initialized card: WinTV PVR 500 (unit #2)
[   12.959830] ivtv: End initialization
[   87.359611] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   87.556161] ivtv0: Encoder revision: 0x02060039
[   92.003658] ivtv1: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   92.200288] ivtv1: Encoder revision: 0x02060039

```

and 

```

dmesg | grep firmware
[   87.264012] firmware: requesting v4l-cx2341x-enc.fw
[   87.359611] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   87.573569] firmware: requesting v4l-cx25840.fw
[   91.060618] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   91.981022] firmware: requesting v4l-cx2341x-enc.fw
[   92.003658] ivtv1: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   92.217996] firmware: requesting v4l-cx25840.fw
[   95.701688] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)

```


Regards
Ian Dobson

---

### Post by viking325i on 2009-01-23
Permissions are:

drwxr-xr-x  6 root   root     63 2008-10-30 18:09 .
drwxr-xr-x 54 root   root   4096 2009-01-21 20:10 ..
drwxrwsr-x  2 mythtv mythtv    6 2008-10-16 18:36 music
drwxrwxr-x  2 mythtv mythtv    6 2008-10-16 18:36 pictures
drwxrwsr-x  2 mythtv mythtv    6 2009-01-24 10:10 recordings
drwxrwxr-x  2 mythtv mythtv    6 2008-10-16 18:36 videos


ivtv

   28.859204] ivtv: Start initialization, version 1.4.0
[   28.859637] ivtv0: Initializing card 0
[   28.859642] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   28.878767] ivtv 0000:03:08.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   28.878782] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   28.932658] ivtv0: Autodetected WinTV PVR 500 (unit #1)
[   29.032911] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   29.271652] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   29.325797] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   29.444638] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   29.460800] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   34.796172] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   34.796550] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   34.796882] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   34.797230] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   34.797570] ivtv0: Registered device radio0 for encoder radio
[   34.797574] ivtv0: Initialized card: WinTV PVR 500 (unit #1)
[   34.797742] ivtv1: Initializing card 1
[   34.797747] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   34.797858] ivtv 0000:03:09.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   34.797870] ivtv1: Unreasonably low latency timer, setting to 64 (was 32)
[   34.851910] ivtv1: Correcting tveeprom data: no radio present on second unit
[   34.851913] ivtv1: Autodetected WinTV PVR 500 (unit #2)
[   34.863346] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[   34.889666] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #1)
[   34.898885] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   34.907836] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   38.508743] ivtv1: Registered device video1 for encoder MPG (4096 kB)
[   38.509167] ivtv1: Registered device video33 for encoder YUV (2048 kB)
[   38.509547] ivtv1: Registered device vbi1 for encoder VBI (1024 kB)
[   38.509917] ivtv1: Registered device video25 for encoder PCM (320 kB)
[   38.509922] ivtv1: Initialized card: WinTV PVR 500 (unit #2)
[   38.511652] ivtv: End initialization
[   58.253341] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   58.452173] ivtv0: Encoder revision: 0x02060039
[   59.639610] ivtv1: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   59.836156] ivtv1: Encoder revision: 0x02060039




[   26.162662] intel_rng: don't want to disable this in firmware setup, and if
[   29.530702] firmware: requesting v4l-cx25840.fw
[   34.724851] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   34.933778] firmware: requesting v4l-cx25840.fw
[   38.437385] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   58.188057] firmware: requesting v4l-cx2341x-enc.fw
[   58.253341] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   59.600036] firmware: requesting v4l-cx2341x-enc.fw
[   59.639610] ivtv1: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)

---

### Post by viking325i on 2009-02-08
Hi, just wondering if anyones spotted any problems in my previous post?

Cheers

---

### Post by ian dobson on 2009-02-08
Hi,

Maybe try downloading the latest ivtv bleeding drivers and try again. The ivtv drivers have been abit broken for about a week or so.

Your dmesg looks OK to me.

Regards
Ian Dobson

---

