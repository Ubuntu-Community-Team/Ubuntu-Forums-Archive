---
title: "New user - no channels and other issues"
date: 2016-01-16
forum: Mythbuntu
---

### Post by nmw01223 on 2016-01-16
I'm an experienced PC user and s/w developer - but Windows, not Linux.

I've had a PVR successfully running on Windows 7 for some time now using Argus TV / Kodi and 2x 292e triplestick tuners from a TV aerial picking up Sandy Heath transmitter (near Cambridge, UK), but decided I'd like to build a standalone box for this, and after looking at the options, picked MythBuntu. The hardware I'm using is slightly old now but still reasonably good - AMD 2.6GHz dual core CPU, 4GB RAM, 250GB SSD, nVidia GE8400GS display adapter, TP-Link Wireless adapter, and the 'screen' is a Sony Bravia TV via HDMI - it supports various resolutions including 720p and 1080i.

I downloaded the 14.04 64 bit ISO and installed it reformatting the SSD completely. Installation went fine, wireless detected OK, screen selected 720p/60 resolution. I following the instructions in the MythBuntu quick start guide.

However .... not got much to work. All sorts of problems, no doubt 95% caused by my lack of knowledge of Linux / Myth TV, but serious show stoppers to me anyway. So, any help on any of the following points would be appreciated.

1. Linux problem - screen overflow. As soon as I exited the Myth TV front end, the desktop showing overflowed all 4 sides. After a lot of looking around the only way I found to fix this was in the nVidia X server settings to have an underscan of 70. But - as soon as I reboot, it is gone again and has to be redone. There is an option to save settings, but I am not at all sure what file and where to save the settings to.

2. Fonts. As installed, all the forms used in dialogues and title bars were huge. I went into settings > appearance > fonts and found the font to be Ubuntu 10. Changed it to Ubuntu 5 and it all looked better. Then - back to Ubuntu 10, and it is still OK. Very strange.

3. MythTVbackend setup mouse. As soon as I get into MythTV backend setup, the mouse disappears. I think it is still there as somertimes I can see it and it will scroll some lines occasionally, but basically most of the time it is invisible. Are you supposed to be able to use a mouse in the backend setup? If so how does one get it visible?

4. No channels found in scan. The above are irritating, and I'd like to sort them, but this is fatal. I am intending to get EIT from transmission, not a guide provider. I know reading what others do this is unusual, but I am in the UK, and the guide is excellent for 7-8 days ahead, and it is what I do on the Windows system, and it works excellently. So in video source I created a source named T-EIT with the listing grabber set to transmitted guide only (EIT). In general / locale settings TV format is PAL, VBI format PAL teletext. The frequency table floored me a bit and I've tried europe-west (someone else's guide said use this) and try-all. So in Video source I left the channel frequency table as default. In input connections I set each detected DVB adapter /dev/dvb/adapter0[and 1]/frontend0 to the T-EIT video source, and scanned for channels. Nothing found. Yet I know the adapters and aerial signal are good. It doesn't come up with any errors, it scans lots of channels, just never finds a signal.

As I say, 1-3 are annoying, 4 is fatal. What am I doing wrong? Please advise.

---

### Post by khPWXxF on 2016-01-17
I'll comment on 3 & 4.
In backend setup just use the cursor keys.  No need to use mouse.
I found the guides by Gary Parker to be very good when I first started with Mythtv.
I do not have 292e's myself but I have seen articles in forums suggesting that switching between SD and HD is troublesome.  There is work ongoing with that device eg
[https://forum.mythtv.org/viewtopic.php?f=3&t=458](https://forum.mythtv.org/viewtopic.php?f=3&t=458)

Have you googled  'Mythtv forum' and 'Mythtv forum gossamer' and lurked?
Phil

---

### Post by nmw01223 on 2016-02-01
Thanks for your reply. Some of these are now solved:
- Channels, caused by the need to place a firmware file dvd-demod-si2168-02.fw (or dvd-demod-si2168-b40-01.fw depending on the kernel) in /lib/firmware for the 292e. However - no dvb/t2 HD channels. This appears to be due to a tuner / driver / MythTV incompatibility that will not be fixed until the release of 0.28.
- Mouse, take your point, don't use it.
- Fonts, the screen is set for 96dpi, by changing that to 95 then back to 96, it all fixes itself - strange
 - Overscan, sorted for nVidia, see [http://ubuntuforums.org/showthread.php?t=2311819](http://ubuntuforums.org/showthread.php?t=2311819)
- Getting idle shutdown and EIT transmission scanning  both to work, seems fixed now
- With a HDHomeRun tuner directly connected, working out how to delay  the start of the backend until the tuner has an IP address (see [http://ubuntuforums.org/showthread.php?t=2312665](http://ubuntuforums.org/showthread.php?t=2312665))
- Upstart problem causing shutdown issue, see [http://ubuntuforums.org/showthread.php?t=2312006](http://ubuntuforums.org/showthread.php?t=2312006)

Other problems that now exist are:
 - The above DVB/T2 HD issue, fixed but not released, may be in 0.27.7, failing that 0.28. Note that HDHomeRun is OK, this relates to USB and other tuners using the driver in the kernel, but that do not auto-switch.

---

