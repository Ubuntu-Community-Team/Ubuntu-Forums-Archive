---
title: "Playback using XvMC profiles &quot;not available&quot;?"
date: 2009-11-17
forum: Mythbuntu
---

### Post by sawbuck on 2009-11-17
I have a upgraded to Mythbuntu 9.10 and added Ubuntu desktop.  I have an Hauppauge HVR 1600 capture card set for US OTA (ATSC) and my graphics is EVGA 6200 (NVIDIA) with 185-set drivers.  The H/W was the same for 9.04 where TV and recoreded playback was fine.  In bot cases I've followed the procedures for XvMC outlined here:

    [http://www.mythtv.org/wiki/XvMC#NVIDIA_2](http://www.mythtv.org/wiki/XvMC#NVIDIA_2)

With some help form these forums I did get it all set up working to my satisfaction in 9.04.

Here is my current xorg.conf:

```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "UseEvents"    "1"
    Option    "DPI"    "100x100"
    Option    "NoLogo"    "1"
        Option "XvmcUsesTextures" "false"
        Option "NVAGP" "1"
EndSection

Section "Extensions"
        Option "Composite" "Disabled"
EndSection

```

Now, wtih 9.10, I've set up a playback profile the same as I had in 9.04.  However, now in 9.10, it seems that with any significant scene changing speed I get "smeared" video that has the picture jagged in fine lines about 1/8-1/4 inch vertical heigth.  Watchable but VERY annoying.  With still shots it is OK.

Looking at the mythfrontend log I see this:

```
2009-11-17 07:09:18.352 TV: Attempting to change from None to Watching WatchingPreRecorded
2009-11-17 07:09:18.405 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- begin
2009-11-17 07:09:18.571 Opening audio device 'default'. ch 2(2) sr 48000
2009-11-17 07:09:18.571 Opening ALSA audio device 'default'.
2009-11-17 07:09:18.628 VidOutVDPAU Error: Failed to initialise VDPAU
2009-11-17 07:09:18.648 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
            codec 'NUV MPEG4' makes 'xv-blit,xshm,xlib,' available, using 'xv-blit' instead.
2009-11-17 07:09:18.654 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-11-17 07:09:18.725 OSD Theme Dimensions W: 640 H: 480
2009-11-17 07:09:19.064 Couldn't load deinterlace filter none
2009-11-17 07:09:19.065 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- end ok
2009-11-17 07:09:19.067 TV: Changing from None to Watching WatchingPreRecorded
2009-11-17 07:09:19.068 OpenGLVideoSync()
2009-11-17 07:09:19.081 Realtime priority would require SUID as root.
2009-11-17 07:09:19.128 ScreenSaverX11Private: DPMS Deactivated 1
2009-11-17 07:09:19.134 Video timing method: SGI OpenGL
2009-11-17 07:09:19.539 AO: dropping back audio_buffer_unused
2009-11-17 07:09:19.593 AO: dropping back audio_buffer_unused
2009-11-17 07:09:19.631 AO: dropping back audio_buffer_unused
2009-11-17 07:09:19.704 AO: dropping back audio_buffer_unused
2009-11-17 07:09:19.753 AO: dropping back audio_buffer_unused
2009-11-17 07:09:19.877 AO: dropping back audio_buffer_unused
2009-11-17 07:09:19.965 AO: dropping back audio_buffer_unused
2009-11-17 07:09:19.995 AO: dropping back audio_buffer_unused
2009-11-17 07:09:20.062 AO: dropping back audio_buffer_unused
2009-11-17 07:09:20.123 AO: dropping back audio_buffer_unused
2009-11-17 07:09:20.158 AO: dropping back audio_buffer_unused
2009-11-17 07:09:20.190 AO: dropping back audio_buffer_unused
2009-11-17 07:09:20.285 AO: dropping back audio_buffer_unused
2009-11-17 07:09:20.318 AO: dropping back audio_buffer_unused
2009-11-17 07:09:20.413 AO: dropping back audio_buffer_unused
2009-11-17 07:09:20.475 AO: dropping back audio_buffer_unused
2009-11-17 07:09:26.934 TV: Attempting to change from Watching WatchingPreRecorded to None
2009-11-17 07:09:26.949 ~OpenGLVideoSync() -- closing opengl vsync
2009-11-17 07:09:26.976 TV: Changing from Watching WatchingPreRecorded to None
2009-11-17 07:09:26.976 ScreenSaverX11Private: DPMS Reactivated 1
2009-11-17 07:09:36.301 AudioPulseUtil: Resume Success
2009-11-17 07:09:36.301 Deleting UPnP client...
Error in my_thread_global_end(): 2 threads didn't exit
```

I don't know where the vdpau attempt comes from since I don't have it activated as far as I know.  What is bothersome is the 

```
2009-11-17 07:09:18.648 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
            codec 'NUV MPEG4' makes 'xv-blit,xshm,xlib,' available, using 'xv-blit' instead.
```

statement.  since xvmc-blit pops in as the default rendereer when standard xvmc is selected as the decoder when setting up the profile.

Anyway, I have tried all combinations available for xvmc, diddled with , opendGL vid syncing on/off, and any other option I acan select but can't improve the video.

Is there a patch or something I need to download?  Tried a search here but nothing relevant appeared....

---

### Post by samuelkarush on 2010-04-28
im in the same boat. hd playback puts my 2.8g processor at 90+% 
 please post if you find out why xvmc-blit isnt being found

---

### Post by novellahub on 2010-04-29
Try playing with your "NVAGP" setting.  On one of my SD frontends I have it set to the following:

```
Option "NVAGP" "3"
```

Make sure to reboot or restart gdm when testing.

```
sudo /etc/init.d/gdm restart
```

---

### Post by kulinskit on 2010-10-03
Finally got XvMC working again!  The NVIDIA proprietary driver included with Lucid 10.04 could not do it no matter what I tried, it was v. 195.x.   I was using the "current" driver, which was v 195.x.

I added the repository below to the Synaptic Package Manager, then did upgrade and only selected the NVIDIA v 260.x driver.  Installed automatically, I rebooted, changed the playback profile to always use XvMC, and since then XvMC seems to be working flawlessly.  Here is the deb source I used:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=lucid]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates?field.series_filter=lucid")

I will probably deactivate the repositary now to stick with the driver that is working for me.

---

