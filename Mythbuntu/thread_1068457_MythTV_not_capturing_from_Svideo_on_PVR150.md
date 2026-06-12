---
title: "MythTV not capturing from Svideo on PVR150"
date: 2009-02-12
forum: Mythbuntu
---

### Post by hoyer801 on 2009-02-12
I'm trying to set up MythTV to capture from my DirecTV receiver via the S-Video input on my PVR150. 

Everything works fine outside of mythtv - mplayer /dev/video0 produces a clear video of whatever is on my directv receiver. 

dmesg | grep ivtv looks ok to me - 
> [   15.133629] ivtv:  Start initialization, version 1.4.0
[   15.134145] ivtv0: Initializing card #0
[   15.134151] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   15.134627] ivtv 0000:01:08.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   15.187174] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   15.395673] cx25840 0-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   15.730828] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   15.949038] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   15.949066] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   19.564848] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   19.565029] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   19.565202] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   19.565376] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   19.565557] ivtv0: Registered device radio0 for encoder radio
[   19.565561] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   19.567263] ivtv:  End initialization
[   37.949490] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   38.148157] ivtv0: Encoder revision: 0x02060039


Within mythtv, I can't access Live TV. It simply gives me a black screen and goes back to the main menu. I can schedule a recording, but after it has recorded, I get the error "The file for this recording cannot be found." 

I've tried deleting my card and video source and putting them back in to no avail. 

On the internal setup, I have the PVR150 set up as an MPEG2 card with Svideo1 as the default input. Svideo1 is the only input that recognizes anything on a channel scan (I've tried them all). 

I'm running Mythbuntu 8.10.

If anyone has any suggestions, I would be most appreciative.

---

### Post by ian dobson on 2009-02-13
Hi,

What do you see in your mythbackend.log (/var/log/mythtv)?

I had problems with my PVR-500 (dual PVR-150) not working until I installed newer ivtv modules, see [http://ubuntuforums.org/showthread.php?t=968121](http://ubuntuforums.org/showthread.php?t=968121) .

Regards
Ian Dobson

---

### Post by hoyer801 on 2009-02-13
Thanks for the tip. The problem was plainly spelled out in the mythbackend.log

My livetv and recordings directories were not writeable. A quick chmod and chown and I'm good to go. 

Thanks.

---

### Post by ian dobson on 2009-02-14
Hi,

then please mark this thread as solved under "thread tools".

Regards
ian dobson

---

