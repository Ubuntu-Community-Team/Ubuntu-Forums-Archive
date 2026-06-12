---
title: "LiveTV and recorded TV freeze on playback"
date: 2008-05-26
forum: Mythbuntu
---

### Post by michaelwc on 2008-05-26
Hi,

I get an issue with when playing live and recorded TV.  The stream freezes after about 1/2 second and audion slows and breaks up.  IT has never worked and VideoLAN plays with ony a slight occassional stutter.

Can anyone help?

AMD XP2400
1GB RAM
160GB HDD
ATI RADEON 9550 128MB

Log file clip:

2008-05-26 15:36:59.091 TV: Attempting to change from None to WatchingLiveTV
2008-05-26 15:36:59.093 Using protocol version 40
2008-05-26 15:37:00.942 DPMS Deactivated 
2008-05-26 15:37:00.993 NVP: Disabling Audio, params(-1,2,44100)
2008-05-26 15:37:01.051 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-05-26 15:37:01.051 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2008-05-26 15:37:01.051 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x8399f98) visual(0xa0f3f18) 
                        XJ_depth(24) WxH(1280x1024) bpl(3840)
2008-05-26 15:37:01.051 VideoOutputXv Error: Failed to create X buffers.
libGL error: drmGetMagic failed
libGL error: reverting to (slow) indirect rendering
2008-05-26 15:37:01.446 Couldn't load deinterlace filter 
2008-05-26 15:37:01.459 OSD Theme Dimensions W: 640 H: 480
2008-05-26 15:37:01.932 TV: Changing from None to WatchingLiveTV
greedyhdeint: size changed from 0 x 0 -> 720 x 576
2008-05-26 15:37:01.997 Realtime priority would require SUID as root.
2008-05-26 15:37:02.022 Video timing method: USleep with busy wait
2008-05-26 15:37:06.244 NVP: Prebuffer wait timed out 10 times.
2008-05-26 15:37:06.414 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-05-26 15:37:06.414 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2008-05-26 15:37:06.414 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x8399f98) visual(0xa0f3f18) 
                        XJ_depth(24) WxH(1280x1024) bpl(3840)
2008-05-26 15:37:06.414 VideoOutputXv Error: Failed to create X buffers.
2008-05-26 15:37:06.922 AFD: Opened codec 0x9ffcea0, id(MPEG2VIDEO) type(Video)
2008-05-26 15:37:06.922 AFD: codec MP3 has 2 channels
2008-05-26 15:37:06.922 AFD: Opened codec 0xa856320, id(MP3) type(Audio)
2008-05-26 15:37:06.922 AFD: codec MP3 has 0 channels
2008-05-26 15:37:06.922 AFD: Opened codec 0xa0e0600, id(MP3) type(Audio)
2008-05-26 15:37:06.922 AFD: Opened codec 0xa059b80, id(DVB_SUBTITLE) type(Subtitle)
2008-05-26 15:37:06.958 Opening audio device 'default'. ch 2(2) sr 48000
2008-05-26 15:37:06.959 Opening ALSA audio device 'default'.
2008-05-26 15:37:06.975 NVP: Enabling Audio
2008-05-26 15:37:08.668 WriteAudio: buffer underrun
2008-05-26 15:37:08.774 WriteAudio: buffer underrun
2008-05-26 15:37:08.880 WriteAudio: buffer underrun
2008-05-26 15:37:08.988 WriteAudio: buffer underrun
2008-05-26 15:37:09.198 WriteAudio: buffer underrun
2008-05-26 15:37:09.309 WriteAudio: buffer underrun
2008-05-26 15:37:09.415 WriteAudio: buffer underrun
2008-05-26 15:37:09.525 WriteAudio: buffer underrun
2008-05-26 15:37:09.632 WriteAudio: buffer underrun
2008-05-26 15:37:09.739 WriteAudio: buffer underrun
2008-05-26 15:37:09.844 WriteAudio: buffer underrun
2008-05-26 15:37:09.952 WriteAudio: buffer underrun
2008-05-26 15:37:10.063 WriteAudio: buffer underrun
2008-05-26 15:37:10.167 WriteAudio: buffer underrun
2008-05-26 15:37:10.275 WriteAudio: buffer underrun
2008-05-26 15:37:10.435 TV: Attempting to change from WatchingLiveTV to None
2008-05-26 15:37:11.174 TV: Changing from WatchingLiveTV to None
2008-05-26 15:37:11.256 DPMS Reactivated.

---

### Post by volkswagner on 2008-05-26
Have you tried the various playback profiles?  Frontend>setup>Setup/config>TV settings>playback settings....try the different profiles cpu-, cpu--, etc.

Are you using the restricted drivers?

---

### Post by michaelwc on 2008-05-27
I have tried many variations of the playback profile,
I have tried both restricted and standard drivers.

I get the same results but with VLAN the playback is pretty good, not perfect though. 

Am I missing something with the playback codecs or GPU drivers or is this something restricted to MythTV?  

My motherboard has on board graphics and I will try that next.  

Any other suggestions will be greatfully received.

MichaelWC

---

