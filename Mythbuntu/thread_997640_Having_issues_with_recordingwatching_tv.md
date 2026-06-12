---
title: "Having issues with recording/watching tv"
date: 2008-11-30
forum: Mythbuntu
---

### Post by patrick0605 on 2008-11-30
I just did a fresh install of Mythbuntu on my new setup.  If it helps I've got a Foxconn mobo w/ the AMD 780G onboard video, an AMD 4850e cpu, 1 gig of Kingston HyperX, and a Seagate 500G hdd.

I ran through all the settings menus a few times, but I don't see anything that looks out of place, though I'm really new to this so I could be over looking something.  My listings work, when I set the box to turn to a channel when Watch TV is selected, and Myth with change the tuner to this channel, so I know that the box and the pc are communicating.  

The problem happens when I try to watch tv, the screen will stay black and hang there unless it hit the esc key.  I also tried to record a show just to see if that worked.  It showed up in my recordings list, but when I try to play it says that the file does not exist.

I'm really new to this, so are there any logs that I should look for to post up here to let you guys assist me better?

Thanks in advance.

---

### Post by ahood on 2008-11-30
What TV tuner card is installed in the system?

> I also tried to record a show just to see if that worked. It showed up in my recordings list, but when I try to play it says that the file does not exist.

This suggests that the video signal (cable or satellite) isn't reaching or recognized by the system.

---

### Post by jonta on 2008-11-30
I am having the same issue with a black screen when trying to watch tv.

Linux htpc 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux
WinTV-PVR-150MCE, PCI-card

ivtv:
```
[    9.199389] ivtv:  Start initialization, version 1.4.0
[    9.199510] ivtv0: Initializing card #0
[    9.199512] ivtv0: Autodetected Hauppauge card (cx23416 based)
[    9.200049] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 19
[    9.200057] ivtv 0000:01:05.0: PCI INT A -> Link[LNKB] -> GSI 19 (level, low) -> IRQ 19
[    9.252291] tveeprom 0-0050: Hauppauge model 25019, rev C560, serial# 10640871
[    9.252294] tveeprom 0-0050: tuner model is LG S001D MK3 (idx 60, type 38)
[    9.252296] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
[    9.252298] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[    9.252300] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[    9.252302] tveeprom 0-0050: has radio
[    9.252303] ivtv0: Autodetected Hauppauge WinTV PVR-150
[    9.501915] cx25840 0-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[    9.558592] HDA Intel 0000:00:09.0: power state changed by ACPI to D0
[    9.558951] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[    9.558955] HDA Intel 0000:00:09.0: PCI INT A -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[    9.558977] HDA Intel 0000:00:09.0: setting latency timer to 64
[    9.590828] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[    9.609293] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[    9.623775] tda9887 0-0043: creating new instance
[    9.623778] tda9887 0-0043: tda988[5/6/7] found
[    9.628403] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[    9.628424] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[    9.652869] tuner-simple 0-0061: creating new instance
[    9.652872] tuner-simple 0-0061: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[    9.669480] firmware: requesting v4l-cx25840.fw
[   13.108236] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   13.177482] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   13.177519] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   13.177555] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   13.177594] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   13.177630] ivtv0: Registered device radio0 for encoder radio
[   13.177632] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   13.177667] ivtv:  End initialization
```

cat /dev/video0 > test.mpg
mplayer test.mpg
shows a picture with static

xawt:
```
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.27-9-generic)
looking for available devices
port 355-386
    type : Xvideo, image scaler
    name : NV17 Video Texture

port 387-418
    type : Xvideo, image scaler
    name : NV05 Video Blitter

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : Hauppauge WinTV PVR-150
    flags:  capture tuner
```

Trying to watch tv with xawtv, only black picture
Tvtime:
```
videoinput: Card failed to allocate capture buffers: Invalid argument
ivtv: Invalid argument
cannot open capture device /dev/video0

```
Mythtv:
```
2008-11-29 17:48:28.778 TVRec(1): Changing from None to WatchingLiveTV
2008-11-29 17:48:28.801 TVRec(1): HW Tuner: 1->1
2008-11-29 17:48:29.929 NVR(/dev/video0): Unknown video codec.  Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles.  Assuming RTjpeg for now.
2008-11-29 17:48:29.955 NVR(/dev/video0) Error: Unknown audio codec
2008-11-29 17:48:29.993 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
cannot open vbi device
2008-11-29 17:48:29.994 NVR(/dev/video0): Won't work with the streaming interface, falling back
2008-11-29 17:48:30.133 NVR(/dev/video0) Error: Can't open vbi device: '/dev/vbi'
VIDIOCGMBUF:: Invalid argument
2008-11-29 17:49:00.240 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-11-29 17:49:10.000 TVRec(1): Changing from WatchingLiveTV to None
2008-11-29 17:49:10.035 Finished recording Unknown: channel 2057
2008-11-29 17:50:00.272 Expiring 0 MBytes for 2057 @ Sat Nov 29 17:48:28 2008 => Unknown
2008-11-29 18:04:21.623 Using runtime prefix = /usr


```

---

### Post by patrick0605 on 2008-11-30
> **ahood said:**
> What TV tuner card is installed in the system?



This suggests that the video signal (cable or satellite) isn't reaching or recognized by the system.


I'm using firewire for video.  When I switch to live TV the channel on my box will change, which leads me to believe that the mythbox and the STB are communicating just something isn't set properly.

---

### Post by patrick0605 on 2008-12-02
I'm getting closer here.

When I click the Live TV button, the box will change to the first channel, and the OSD will display, but I cannot get a lock on a channel.  I'm using a local news channel BTW.

The OSD says 100% signal | (L_ _) Partial Lock.

When I go into manage recordings, after "watching live tv" the channel will show up as being recorded, but again the file is empty.

I updated the directories where myth records to, and made sure that root and mythtv users both have read/write privileges for these folders.

Anyone else have any ideas?

---

### Post by ahood on 2008-12-03
Have you checked the permission settings of the LiveTV directory as reported at the bottom of the thread below?

[**[COLOR="Sienna"]Black Screen when hitting "Watch TV" on Mythbuntu 8.04[/COLOR]**](http://ubuntuforums.org/showthread.php?t=865365)

---

### Post by patrick0605 on 2008-12-03
> **ahood said:**
> Have you checked the permission settings of the LiveTV directory as reported at the bottom of the thread below?

[**[COLOR="Sienna"]Black Screen when hitting "Watch TV" on Mythbuntu 8.04[/COLOR]**](http://ubuntuforums.org/showthread.php?t=865365)

No, but I'll have to look into that.  Thank you.

I decided to try my luck tonight, so I set Myth to record two shows for me, just to see what would happen.  To my surprise, it worked!!

Ok, now the bad part, I'm using a Foxconn mobo with ATI 3200 HD built in graphics and a realtec something or other sound card.  My hopes was that audio would be sent over the HDMI cable, but alas it is not.  

There is sound there, I used the SMB network share to stream it to my XP machine, and there is audio, but I don't feel like streaming a recording every time I want to watch it, especially when they are 4+ GBs each.

I've been trying to find a solution, but it seems like there is little audio via HDMI support currently.  Does anyone have any tips?

---

