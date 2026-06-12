---
title: "Default Video Player stutters - VLC is OK"
date: 2008-07-15
forum: Mythbuntu
---

### Post by balserodeluxe on 2008-07-15
Hello everybody. I have managed so far to build my Mythbuntu box and work through various issues but this one got me bad.

If I put on Live TV or try to play a recording, the image is refreshed every second (maybe 2!) or so. Now, if I play the same recording in VLC, it works fine, so I figured it is not the encoding but the playback. I don't mind which player it is, if it works and can be manipulated easily with the remote.

I tried to set the player to default to VLC without success, I used the command below on the Video Player config page:

vlc file://%s vlc:quit

Any suggestions?

---

### Post by ian dobson on 2008-07-15
Hi,

When you use the default player,what do you see in the frontend log file (directory /var/log/mythv)?

Are you running a combined frontend/backend?
What hardware are you running on?
What drivers are you using for the graphic card.
What's the CPU load like when watching video (use top from the terminal prompt).

Regards
Ian Dobson

---

### Post by mrand on 2008-07-15
> **balserodeluxe said:**
> Hello everybody. I have managed so far to build my Mythbuntu box and work through various issues but this one got me bad.

If I put on Live TV or try to play a recording, the image is refreshed every second (maybe 2!) or so. Now, if I play the same recording in VLC, it works fine, so I figured it is not the encoding but the playback. I don't mind which player it is, if it works and can be manipulated easily with the remote.

I tried to set the player to default to VLC without success, I used the command below on the Video Player config page:

vlc file://%s vlc:quit

Any suggestions?
And most importantly, what mythtv playback profile are you using?

[INDENT]Marc[/INDENT]

---

### Post by balserodeluxe on 2008-07-15
Ian,

I am using a combined Backend/Frontend. Hardware is pretty basic, I am using a PVR 150 card with analog content (NOT HD!!, This should work!).

I will get you the CPU load.

I am posting the logfile below, but, Cannot this be solved just using VLC as the default? I am ok with that but could not get it to default!

Myth TV Frontend Log:

2008-07-15 12:57:12.930 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/ui.xml
2008-07-15 12:57:14.221 AFD: Opened codec 0x849bd40, id(MPEG2VIDEO) type(Video)
2008-07-15 12:57:14.221 AFD: codec MP2 has 2 channels
2008-07-15 12:57:14.221 AFD: Opened codec 0x83566b0, id(MP2) type(Audio)
2008-07-15 12:57:14.369 TV: Attempting to change from None to WatchingPreRecorded
2008-07-15 12:57:14.389 DPMS Deactivated 
2008-07-15 12:57:14.643 VideoOutputXv Error: XvMC output requested, but is not supported by display.
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
2008-07-15 12:57:14.645 AFD: Opened codec 0x849bd40, id(MPEG2VIDEO) type(Video)
2008-07-15 12:57:14.646 AFD: codec MP2 has 2 channels
2008-07-15 12:57:14.646 AFD: Opened codec 0x834fbc0, id(MP2) type(Audio)
2008-07-15 12:57:14.651 Opening audio device 'default'. ch 2(2) sr 48000
2008-07-15 12:57:14.651 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-07-15 12:57:14.658 AudioOutput Warning: Mixer attach error -2: No such file or directory
			Check Mixer Name in Setup: '/dev/mixer'
2008-07-15 12:57:14.774 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
			codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2008-07-15 12:57:14.780 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-07-15 12:57:14.780 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2008-07-15 12:57:14.780 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x8412f00) visual(0x8402310) 
                        XJ_depth(16) WxH(800x595) bpl(1600)
2008-07-15 12:57:14.781 VideoOutputXv Error: Failed to create X buffers.
2008-07-15 12:57:14.967 Couldn't load deinterlace filter 
2008-07-15 12:57:14.970 OSD Theme Dimensions W: 640 H: 480
2008-07-15 12:57:15.449 TV: Changing from None to WatchingPreRecorded
2008-07-15 12:57:15.451 VideoOutputXv Error: GetRefreshRate(): X11 ModeLine query returned zeroes
2008-07-15 12:57:15.456 FilterManager: failed to load filter 'none', no such filter exists
2008-07-15 12:57:15.456 Couldn't load deinterlace filter none
2008-07-15 12:57:15.482 Realtime priority would require SUID as root.
2008-07-15 12:57:15.589 VideoOutputXv Error: GetRefreshRate(): X11 ModeLine query returned zeroes
2008-07-15 12:57:15.589 Video timing method: RTC
2008-07-15 12:57:29.697 TV: Attempting to change from WatchingPreRecorded to None
2008-07-15 12:57:29.784 TV: Changing from WatchingPreRecorded to None
2008-07-15 12:57:29.811 DPMS Reactivated.
2008-07-15 12:57:29.973 AFD: Opened codec 0x83566b0, id(MPEG2VIDEO) type(Video)
2008-07-15 12:57:29.974 AFD: codec MP2 has 2 channels
2008-07-15 12:57:29.974 AFD: Opened codec 0x834fbc0, id(MP2) type(Audio)
2008-07-15 12:57:30.528 AFD: Opened codec 0x834fbc0, id(MPEG2VIDEO) type(Video)
2008-07-15 12:57:30.529 AFD: codec MP2 has 2 channels
2008-07-15 12:57:30.529 AFD: Opened codec 0x83566b0, id(MP2) type(Audio)
2008-07-15 12:57:30.860 [mpeg2video @ 0xb734fb88]invalid cbp at 17 8
2008-07-15 12:57:30.861 [mpeg2video @ 0xb734fb88]Warning MVs not available

---

### Post by balserodeluxe on 2008-07-17
Hardware is a 2.66 GHz with 1Gig of RAM.

I am using the 'SLIM' Playback Profile

If I look at the "System Monitor"'s Resource tab, CPU usage during playback is 100%. That kinda throws me off as I am typing this at the same time!

One user advises me that VLC cannot be used for Live TV and Recordings. These are my actual pain points.

---

### Post by balserodeluxe on 2008-08-11
any suggestions on how to get this going smoothly on a 2.66 GHz machine??

---

### Post by newlinux on 2008-08-11
something is definitely wrong if your CPU is at 100% using the internal player. And you can't use VLC for recordings or LiveTV, only for mythvideo. The setting you are changing for default player only apply to mythtvideo. I have played back HD streams with a P4 2.6 Ghz with a geforce MX 440 so you shouldn't have any problems with analog. What vid card are you using?

I'm pretty sure your problem is the playback profile. It looks like SLIM one is trying to use XvMC which you shouldn't need and isn't properly configured on your system anyway. Try using some of the other built in ones and see if they work. Then you can tweak if you like...

---

