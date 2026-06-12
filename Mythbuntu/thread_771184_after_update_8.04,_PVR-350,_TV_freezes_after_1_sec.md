---
title: "after update 8.04, PVR-350, TV freezes after 1 second"
date: 2008-04-27
forum: Mythbuntu
---

### Post by nanofuzzy1 on 2008-04-27
Hi all,

I updated to 8.04 and the Live-TV freezes now after about one second. I can go back to menue with ESC so the frontend doesnt crash. The mythfrontend log says:

VideoOutputXv: Desired video renderer 'ivtv' not available.
			codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2008-04-27 22:07:25.428 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-04-27 22:07:25.429 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2008-04-27 22:07:25.429 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x9e90b348) visual(0x9e90c0f8) 
                        XJ_depth(24) WxH(1280x1024) bpl(3840)
2008-04-27 22:07:25.429 VideoOutputXv Error: Failed to create X buffers.
libGL error: drmGetMagic failed
libGL error: reverting to (slow) indirect rendering
2008-04-27 22:07:25.726 Couldn't load deinterlace filter 
2008-04-27 22:07:25.732 OSD Theme Dimensions W: 640 H: 480
2008-04-27 22:07:26.048 TV: Changing from None to WatchingLiveTV
2008-04-27 22:07:26.051 Realtime priority would require SUID as root.
2008-04-27 22:07:26.053 FilterManager: failed to load filter 'none', no such filter exists
2008-04-27 22:07:26.053 Couldn't load deinterlace filter none
2008-04-27 22:07:26.150 Video timing method: USleep with busy wait
2008-04-27 22:07:26.235 WriteAudio: buffer underrun
2008-04-27 22:07:29.500 WriteAudio: buffer underrun
and so on...

 dmesg|grep -i ivtv 
gives:
  32.015367] ivtv:  Start initialization, version 1.1.0
[   34.738086] ivtv0: Initializing card #0
[   34.738095] ivtv0: Autodetected Hauppauge card (cx23415 based)
[   34.738853] ivtv0: YUV filter table not found in firmware.
[   34.801985] ivtv0: Autodetected Hauppauge WinTV PVR-350
[   34.852591] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   35.111883] saa7115 1-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   35.279655] saa7127 1-0044: saa7127 found @ 0x88 (ivtv i2c driver #0)
[   35.294919] msp3400 1-0040: MSP4418G-A2 found @ 0x80 (ivtv i2c driver #0)
[   35.305678] ivtv0: Registered device video1 for encoder MPG (4096 kB)
[   35.305714] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   35.305750] ivtv0: Registered device vbi1 for encoder VBI (1024 kB)
[   35.305785] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   35.305819] ivtv0: Registered device radio0 for encoder radio
[   35.305856] ivtv0: Registered device video16 for decoder MPG (1024 kB)
[   35.305894] ivtv0: Registered device vbi8 for decoder VBI (64 kB)
[   35.305927] ivtv0: Registered device vbi16 for decoder VOUT
[   35.305961] ivtv0: Registered device video48 for decoder YUV (1024 kB)
[   35.305964] ivtv0: Initialized card #0: Hauppauge WinTV PVR-350
[   35.306010] ivtv:  End initialization
[   46.200120] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   46.234269] ivtv0: Loaded v4l-cx2341x-dec.fw firmware (262144 bytes)
[   46.433111] ivtv0: Encoder revision: 0x02060039
[   46.433258] ivtv0: Decoder revision: 0x02020023
[   46.498732] ivtv0: Loaded v4l-cx2341x-init.mpg firmware (155648 bytes)

the ivtv driver seems to work properly.

Why can't the backend find it?

I switched to CPU--. No success.

please help,

thanks a lot.

---

### Post by nanofuzzy1 on 2008-04-28
I found the problem or at least a solution: I just had to deactivate the non-free video hardware driver.

Now, I can watch live TV. 

But the frontend still can't find the ivtv driver. This is odd.

---

### Post by Mateo on 2008-04-28
same problem here, i'm not using mythtv though.  with mplayer, the videos freeze after about a second.  it's doesn't appear to be a problem with the video directly, because i was able to play the video perfectly fine on my video streamer.

---

