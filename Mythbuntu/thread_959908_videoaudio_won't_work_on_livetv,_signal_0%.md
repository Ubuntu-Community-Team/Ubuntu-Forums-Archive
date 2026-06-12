---
title: "video/audio won't work on livetv, signal 0%"
date: 2008-10-26
forum: Mythbuntu
---

### Post by shortyjacobs on 2008-10-26
I'm trying to watch ATSC OTA live tv with an antenna.

Live TV won't work.  I click "Watch TV", and get a single frame, sometimes two or three in a row, of whatever channel I was last on.  I get stutters of audio at the same time.  It says "Signal 0%" and sig/noise ratio of 2.5 ish on each channel.  I know I have good signals on these channels becuase my TV picks them up 90-100% strength.  The system will then sort of hang, where hitting "up" or "down" to change channels does nothing, and you have to hit esc twice to get back to the menu.  

DVD quality is awful too, with video and audio stutters, but it's at least watchable...

Any thoughts?

Specs:
Athlon 64 X2 5200+ dual core, (2.7 ghz each), Gigabyte GA-MA78GM-S2H mobo, 2 gb kingston ram, 2x 500gb WD 7200 HDD, 2x Hauppauge WinTV HVR-1250 tuner cards 

:confused::confused:](*,)](*,)

---

### Post by SiHa on 2008-10-27
Are you just using a passive splitter to split your Aerial signal to the two cards? I believe this card is a dual (Analogue + HD Digital) card? So there's two tuners on each board.

This means that you've probably got 4 tuners hanging off one Aerial.

Can you try diconnecting the Aerial from one card - does it help? If so, a signal booster may be in order.

Not sure about the DVD problem though, doesn't sound connected...

---

### Post by newlinux on 2008-10-27
You might want to play wiht your playback profiles. You're using onboard ATI? Which driver? Some playback settings aren't supported depending on what driver you are using. Look through your frontend logs.

---

### Post by shortyjacobs on 2008-10-30
Definitely not a signal strength problem.  Doesn't matter if I go through a splitter or not, and if I hook one half of the splitter up to my TV directly, I still get 90 - 100 % signal.

I tried the drivers route next.  Uninstalled the "Proprietary ATI driver" and installed catalyst 8.10.  No luck.  

It seemed odd that DVD would play but TV wouldn't, so I figured it might be the tuner cards.  I tried reinstalling the V4L-DVB tree....but no dice.

Frontend log showed this interesting tidbit...
> 2008-10-30 21:24:20.232 TV: Attempting to change from None to WatchingLiveTV
2008-10-30 21:24:20.233 Using protocol version 40
2008-10-30 21:24:21.955 DPMS Deactivated 
2008-10-30 21:24:22.012 New DB connection, total: 3
2008-10-30 21:24:22.013 Connected to database 'mythconverg' at host: localhost
2008-10-30 21:24:22.071 NVP: Disabling Audio, params(-1,2,44100)
2008-10-30 21:24:22.122 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-10-30 21:24:22.122 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2008-10-30 21:24:22.138 VideoOutputXv Error: XCreateImage failed: XJ_disp(0xa7e920) visual(0x9f2bf0) 
                        XJ_depth(16) WxH(1600x1200) bpl(3200)
2008-10-30 21:24:22.139 VideoOutputXv Error: Failed to create X buffers.
2008-10-30 21:24:22.434 Couldn't load deinterlace filter 
2008-10-30 21:24:22.442 OSD Theme Dimensions W: 640 H: 480
2008-10-30 21:24:23.293 TV: Changing from None to WatchingLiveTV
2008-10-30 21:24:23.295 Realtime priority would require SUID as root.
2008-10-30 21:24:23.295 VideoOutputXv Error: GetRefreshRate(): X11 ModeLine query returned zeroes
2008-10-30 21:24:23.358 VideoOutputXv Error: GetRefreshRate(): X11 ModeLine query returned zeroes
2008-10-30 21:24:23.358 Video timing method: USleep with busy wait
2008-10-30 21:24:24.895 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-10-30 21:24:24.895 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2008-10-30 21:24:24.895 VideoOutputXv Error: XCreateImage failed: XJ_disp(0xa7e920) visual(0x9f2bf0) 
                        XJ_depth(16) WxH(1600x1200) bpl(3200)
2008-10-30 21:24:24.896 VideoOutputXv Error: Failed to create X buffers.
2008-10-30 21:24:26.268 AFD: Opened codec 0x7f4a080ac240, id(MPEG2VIDEO) type(Video)
2008-10-30 21:24:26.268 AFD: codec AC3 has 2 channels
2008-10-30 21:24:26.268 AFD: Opened codec 0x7f4a080ab6b0, id(AC3) type(Audio)
2008-10-30 21:24:26.269 AFD: codec AC3 has 1 channels
2008-10-30 21:24:26.269 AFD: Opened codec 0x7f4a080aa560, id(AC3) type(Audio)
2008-10-30 21:24:26.270 Opening audio device 'default'. ch 2(2) sr 48000
2008-10-30 21:24:26.270 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-10-30 21:24:26.356 AudioOutput Warning: Mixer attach error -2: No such file or directory
			Check Mixer Name in Setup: '/dev/mixer'
2008-10-30 21:24:26.359 NVP: Enabling Audio
2008-10-30 21:24:28.326 WriteAudio: buffer underrun
2008-10-30 21:24:28.371 WriteAudio: buffer underrun
2008-10-30 21:24:28.411 WriteAudio: buffer underrun

the bufferunderruns continue for a few hundred lines, (longer, depending on how long I wait for the video to work out of it's funk).

More importantly than the buffer underruns though, I think are the XVideo lines....but I don't know what they mean or how to fix it.  Any ideas?

Thanks much in advance.

---

