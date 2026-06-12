---
title: "New EfficientPC Isis video freezes"
date: 2008-10-18
forum: Mythbuntu
---

### Post by dualboot on 2008-10-18
Hi all,
I've just received a shiny new machine from EfficientPC pre-loaded with Mythbuntu 8.04.  [http://efficientpc.co.uk/desktops/flexible/isis/](http://efficientpc.co.uk/desktops/flexible/isis/)  to the basic spec I added a NovaT-500 and upped the disk to 1TB.

After initial config via VGA, turning on the proprietary driver enabled the HDMI interface of the ATI RadeonTM 1250.  

But when I go into 'Watch TV' the picture starts but freezes after a second.  No sound either.

A bit of research pointed me to look in the mythfrontend.log file where I see the following messages which seem to be pertinent.(I hope its OK to past such a lot in...)

2008-10-18 11:40:47.824 TV: Attempting to change from None to WatchingLiveTV
2008-10-18 11:40:47.858 Using protocol version 40
2008-10-18 11:40:49.843 NVP: Disabling Audio, params(-1,2,44100)
2008-10-18 11:40:49.854 DPMS Deactivated 
2008-10-18 11:40:49.992 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-10-18 11:40:49.993 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2008-10-18 11:40:49.993 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x89ccc00) visual(0x893e860) 
                        XJ_depth(24) WxH(1920x1080) bpl(5760)
2008-10-18 11:40:49.993 VideoOutputXv Error: Failed to create X buffers.
libGL error: drmGetMagic failed
libGL error: reverting to (slow) indirect rendering
2008-10-18 11:40:50.572 Couldn't load deinterlace filter 
2008-10-18 11:40:50.588 OSD Theme Dimensions W: 640 H: 480
2008-10-18 11:40:51.270 TV: Changing from None to WatchingLiveTV
2008-10-18 11:40:51.273 The realtime priority setting is not enabled.
2008-10-18 11:40:51.460 Video timing method: USleep with busy wait
2008-10-18 11:40:54.915 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-10-18 11:40:54.915 VideoOutputXv: Falling back to X11 video output over a network socket.
			      *** May be very slow ***
2008-10-18 11:40:54.916 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x89ccc00) visual(0x893e860) 
                        XJ_depth(24) WxH(1920x1080) bpl(5760)
2008-10-18 11:40:54.916 VideoOutputXv Error: Failed to create X buffers.
2008-10-18 11:40:55.039 NVP: Prebuffer wait timed out 10 times.
2008-10-18 11:40:55.777 AFD: Opened codec 0xa0145b80, id(MPEG2VIDEO) type(Video)
2008-10-18 11:40:55.778 AFD: codec MP3 has 2 channels
2008-10-18 11:40:55.778 AFD: Opened codec 0x99c87280, id(MP3) type(Audio)
2008-10-18 11:40:55.778 AFD: Opened codec 0xa5ed86e0, id(DVB_SUBTITLE) type(Subtitle)
2008-10-18 11:40:55.778 AFD: codec MP3 has 0 channels
2008-10-18 11:40:55.778 AFD: Opened codec 0xa01215e0, id(MP3) type(Audio)
2008-10-18 11:40:55.850 Opening audio device 'default'. ch 2(2) sr 48000
2008-10-18 11:40:55.850 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-10-18 11:40:55.907 AudioOutput Warning: Mixer attach error -2: No such file or directory
			Check Mixer Name in Setup: '/dev/mixer'
2008-10-18 11:40:55.908 NVP: Enabling Audio
2008-10-18 11:40:57.812 WriteAudio: buffer underrun
2008-10-18 11:40:57.940 WriteAudio: buffer underrun
2008-10-18 11:40:58.073 WriteAudio: buffer underrun
2008-10-18 11:40:58.226 WriteAudio: buffer underrun
2008-10-18 11:40:58.357 WriteAudio: buffer underrun
2008-10-18 11:40:58.499 WriteAudio: buffer underrun
2008-10-18 11:40:58.627 WriteAudio: buffer underrun
2008-10-18 11:40:58.756 WriteAudio: buffer underrun
2008-10-18 11:40:58.840 WriteAudio: buffer underrun
2008-10-18 11:40:58.893 WriteAudio: buffer underrun
2008-10-18 11:40:58.944 WriteAudio: buffer underrun
2008-10-18 11:40:58.995 WriteAudio: buffer underrun
2008-10-18 11:40:59.046 WriteAudio: buffer underrun
2008-10-18 11:40:59.103 WriteAudio: buffer underrun
2008-10-18 11:40:59.158 WriteAudio: buffer underrun
2008-10-18 11:40:59.263 WriteAudio: buffer underrun
2008-10-18 11:40:59.314 WriteAudio: buffer underrun
2008-10-18 11:40:59.338 TV: Attempting to change from WatchingLiveTV to None
2008-10-18 11:40:59.611 TV: Changing from WatchingLiveTV to None
2008-10-18 11:40:59.639 DPMS Reactivated.

I guess I can get help from EfficientPC on Monday, but I am keen to get it sorted :confused:

Any help or tips would be greatly appeciated.

---

### Post by dualboot on 2008-10-18
I've manage to go from frozen video to jerky video with 95pc CPU to Xorg.  This progress was made by changing the Audio Output device to ALSA:digital   I didn't get any sound still through the HDMI but at least its progress.  

I can't do any more testing today - kids have revolted at being kept off the Wii all day ](*,)

Does anyone have a known working setup for a Radeon 1250 running on HDMI ?  Are there any good guides to tuning the video performance ?  The options in the TV playback setting seem to be infinite ! (I'm guessing only one will give a decent picture)

Still no sound or remote either.

---

### Post by eightace on 2008-11-04
Hi - I have exactly the same problem as you with an ISIS machine and the same TV card. Have you find a solution? Try asking Dale via MSN or on the efficientpc support board:
[https://answers.launchpad.net/efficientpc/](https://answers.launchpad.net/efficientpc/)

It is frustrating as I cannot watch TV never mind record it - considering asking for a refund....:-({|=

---

### Post by root.veg on 2008-11-04
I initially had similar problems to you guys - I recently got an Isis system delivered with 8.04 and a Hauppauge Nova-T 500 Dual. At first, using 8.04 and the Open Source drivers, video wouldn't work, it was more like a slide-show. I couldn't get 3D acceleration to work in order to play games. The proprietary driver supplied with the install didn't work either. *However* when I got the latest driver directly from [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-10-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-10-x86.x86_64.run) and installed that, I at least got working video, although the 3D acceleration didn't cope with playing Warsow.

This may not be the answer you're after, but I did a fresh install of Mythbuntu 8.10 64-bit, and the open-source driver works perfectly out-of-the-box for me, so I haven't bothered installing the proprietary driver. (NB I haven't got an HDMI capable TV yet so I haven't been able to test whether the open source driver works OK using the HDMI output). Incidentally, 3D acceleration works fine too - I've been playing Warsow and Vegastrike with very smooth graphics, it's beautiful.

Don't suppose either of you guys has had trouble scanning for channels, have you?:

[http://ubuntuforums.org/showthread.php?p=6102633#post6102633](http://ubuntuforums.org/showthread.php?p=6102633#post6102633)

The point of me buying this thing was that I wouldn't have to set anything up :-)

---

### Post by eightace on 2008-11-04
> **root.veg said:**
> I initially had similar problems to you guys - I recently got an Isis system delivered with 8.04 and a Hauppauge Nova-T 500 Dual. At first, using 8.04 and the Open Source drivers, video wouldn't work, it was more like a slide-show. I couldn't get 3D acceleration to work in order to play games. The proprietary driver supplied with the install didn't work either. *However* when I got the latest driver directly from [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-10-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-10-x86.x86_64.run) and installed that, I at least got working video, although the 3D acceleration didn't cope with playing Warsow.

This may not be the answer you're after, but I did a fresh install of Mythbuntu 8.10 64-bit, and the open-source driver works perfectly out-of-the-box for me, so I haven't bothered installing the proprietary driver. (NB I haven't got an HDMI capable TV yet so I haven't been able to test whether the open source driver works OK using the HDMI output). Incidentally, 3D acceleration works fine too - I've been playing Warsow and Vegastrike with very smooth graphics, it's beautiful.

Don't suppose either of you guys has had trouble scanning for channels, have you?:

[http://ubuntuforums.org/showthread.php?p=6102633#post6102633](http://ubuntuforums.org/showthread.php?p=6102633#post6102633)

The point of me buying this thing was that I wouldn't have to set anything up :-)

I echo your sentiments - my system was supposed to be "wife-friendly" and was to avoid getting Sky HD but I am not able to get things running despite everything...

---

### Post by root.veg on 2008-11-04
I considered making a fuss to Dale at EfficientPC, but frankly I judged it was probably less hassle to make it work myself than send it back or whatever. Think I'm nearly there, anyway...

---

