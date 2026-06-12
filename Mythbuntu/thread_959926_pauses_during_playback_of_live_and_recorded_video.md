---
title: "pauses during playback of live and recorded video"
date: 2008-10-26
forum: Mythbuntu
---

### Post by thalon on 2008-10-26
Hello all,
I have installed Mythbuntu 8.04 onto a new secondary backend.  It is pausing every 3 seconds or so, for a half second at a time, when playing anything.  This includes LiveTV, recorded programs, and even a DVD in its own drive.  I have run the 'top' command in a console window during playback, and the CPU is only 60% used so I don't think my hardware is lacking.  The system has 512MB of RAM which is plenty of RAM in my primary backend, never had any issues like this with playback there.  I believe the graphics card I used in this system is an ATI x1600, so that should be fine.

What else am I missing?

---

### Post by ian dobson on 2008-10-27
Hi,

What graphic card driver have you installed/are using?
What playback profile are you using? CPU--,CPU-,CPU+ etc.

Do you see any messages in the frontend log (/var/log/frontend.log)

Regards
Ian Dobson

---

### Post by thalon on 2008-10-27
I need some help determining what driver is in use.  I think I enabled the proprietary drivers in the Myth backend setup, but I have no idea if it's actually using them or not.  Is there a command I can run and report the output?

I had set the playback profile to High Quality, which is where I want it (of course :) ).  I tried setting it to Normal and to CPU--, both resulted in practically frozen video playback (1 frame every 2 sec or so) but the audio was continuous except for a very slight cutout at about the same 3 second frequency.  

I think your third question will shine some light on my problem for you, but I still don't know what to do about it..  here's a snippet of my /var/log/mythtv/mythfrontend.log:

```

2008-10-27 13:41:14.803 TV: Changing from None to WatchingPreRecorded
2008-10-27 13:41:14.805 TV: Attempting to change from WatchingPreRecorded to None
2008-10-27 13:41:14.808 TV: Changing from WatchingPreRecorded to None
2008-10-27 13:41:15.840 DPMS Deactivated
2008-10-27 13:41:15.841 DPMS Reactivated.
2008-10-27 13:43:20.228 XMLParse::LoadTheme using /usr/share/mythtv/themes/neon-wide/ui.xml
2008-10-27 13:43:22.030 TV: Attempting to change from None to WatchingPreRecorded
2008-10-27 13:43:22.235 DPMS Deactivated
2008-10-27 13:43:22.341 AFD: Opened codec 0x83ecb60, id(MPEG2VIDEO) type(Video)
2008-10-27 13:43:22.341 AFD: codec AC3 has 2 channels
2008-10-27 13:43:22.342 AFD: Opened codec 0x82dd000, id(AC3) type(Audio)
2008-10-27 13:43:22.764 AFD: Opened codec 0x82de580, id(MPEG2VIDEO) type(Video)
2008-10-27 13:43:22.764 AFD: codec AC3 has 2 channels
2008-10-27 13:43:22.765 AFD: Opened codec 0x8308e00, id(AC3) type(Audio)
2008-10-27 13:43:22.769 Opening audio device 'spdif'. ch 2(2) sr 48000
2008-10-27 13:43:22.769 Opening ALSA audio device 'spdif'.
2008-10-27 13:43:22.867 Opening audio device 'spdif'. ch 2(2) sr 48000
2008-10-27 13:43:22.867 Opening ALSA audio device 'spdif'.
2008-10-27 13:43:23.049 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-10-27 13:43:23.050 VideoOutputXv: Falling back to X11 video output over a network socket.
                              *** May be very slow ***
2008-10-27 13:43:23.051 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x845e3a8) visual(0x845e8e8)
                        XJ_depth(24) WxH(1024x768) bpl(3072)
2008-10-27 13:43:23.051 VideoOutputXv Error: Failed to create X buffers.
2008-10-27 13:43:23.683 Couldn't load deinterlace filter
2008-10-27 13:43:23.692 OSD Theme Dimensions W: 640 H: 480
2008-10-27 13:43:24.667 TV: Changing from None to WatchingPreRecorded
2008-10-27 13:43:24.669 The realtime priority setting is not enabled.
greedyhdeint: size changed from 0 x 0 -> 528 x 480
2008-10-27 13:43:24.890 Video timing method: USleep with busy wait
2008-10-27 13:43:26.220 NVP: Prebuffer wait timed out 10 times.
2008-10-27 13:43:27.551 NVP: Prebuffer wait timed out 10 times.
2008-10-27 13:43:28.881 NVP: Prebuffer wait timed out 10 times.
2008-10-27 13:43:30.212 NVP: Prebuffer wait timed out 10 times.
2008-10-27 13:43:31.542 NVP: Prebuffer wait timed out 10 times.
2008-10-27 13:43:32.872 NVP: Prebuffer wait timed out 10 times.
2008-10-27 13:43:34.203 NVP: Prebuffer wait timed out 10 times.
2008-10-27 13:43:35.533 NVP: Prebuffer wait timed out 10 times.
2008-10-27 13:43:36.863 NVP: Prebuffer wait timed out 10 times.

```

And it just keeps on going and going repeating the timeout error.  I see a message in there about defaulting back to connecting to X via a network socket, does that have to do with the video driver not working right?  Where do I get an appropriate video driver for this?

And for the future, what text editor should I install?  I had to open up a terminal window and use vi to copy/paste the above log.  This is silly, Mythbuntu doesn't seem to come with a GUI text editor.  Apt-get works just fine so just let me know which package to get.  Thanks!

If somehow in this process we figure out how to get the resolution up any higher than 640x480 I'd be doubly grateful.  :)

---

### Post by newlinux on 2008-10-27
looks like whatever driver you are using doesn't support XV, so you need to modify your playback profile to not use xv for deinterlacing.

I have use ubuntu (gnome)+mythtv installs so I'm not sure what editors come by default with mythbuntu (xfce), but most people in ubuntu probably use gedit or kubuntu users probably like kate. I use nano commandline and gedit gui.

You can look in /var/log/Xorg.0.log to see what driver X is using (and errors that may be happening in the X session).

i never use ATI in linux so this is probably the most help I can give... 

BTW, the playback profile are just samples, what settings are high quality on one machine may be different on another. All of my frontends use different playback profile settings.
good luck.

---

### Post by ian dobson on 2008-10-27
Hi,

If you go to the terminal and then type:-

sudo lspci

you'll see a list of the hardware installed. Look for something like:-

01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]

Regards
Ian Dobson

---

### Post by thalon on 2008-10-28
Okay I determined that it's trying to use the FireGL video driver (fglrx) and not the radeon driver.  I went into Mythbuntu Controle Centre (that's how it's spelled on my menu) --> Proprietary Drivers button --> Ubuntu Display Configuration Utility section --> Launch Xorg Config --> Graphics Card tab.  That's where it has fglrx selected.  When I click on fglrx and select radeon instead, even if I click ok to the child window it never changes from fglrx in the Graphics Card tab of the Screen and Graphics Preferences window.  I think that's my root problem there.

Can anyone help me (and whoever else might find this thread with the same problem) find an alternate way of selecting the video driver for Xorg, specifically in Mythbuntu?  Maybe this needs to be submitted as a bug to the Mythtv and/or Mythbuntu team.

By the way, here's my lspci output:

```
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
01:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)
02:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

---

### Post by thalon on 2008-11-02
I didn't intend for my giving thanks to newlinux above to indicate this problem was solved...  this is sorta a bump with an update.

The proprietary drivers being enabled is what was causing me to not be able to change the video driver in the Screen and Graphics Preferences window.  Once I disabled the proprietary ATI driver in Mythbuntu Control Centre, it let me change to the radeon driver without a hitch.

I tried creating a new playback profile and selecting almost all of the different renderers one by one including directx, direct3d, opengl, etc.  None of them gave any better performance than what I've already reported.  Is the 'radeon' driver simply incompatible with MythTV?

---

