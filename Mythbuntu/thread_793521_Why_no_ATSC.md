---
title: "Why no ATSC?"
date: 2008-05-13
forum: Mythbuntu
---

### Post by colinnwn on 2008-05-13
Hi,

I thought there is supposed to be an ATSC option under 'Backend Setup'>'General'>'Locale Settings'>'TV format'.  I only get NTSC and various flavors of PAL.

Can anyone tell me if ATSC should be missing?  Does ATSC only become an option when Myth recognizes a compatible tuner, or is there possibly something not being loaded correctly?  Any thoughts on how I could fix it?

I'm having trouble getting my ATSC tuner recognized.  It does now work as NTSC frame capture, but the picture is choppy (updates about every half second) and isn't good quality.
Thanks.

---

### Post by jlagrone on 2008-05-14
NTSC is the proper setting.  NTSC/PAL are more related to the screen properties (refresh rates, frequencies, and such)

How do you have the capture card setup?  I'm not familiar with your particular card, but your best bet is probably to set it up as a DVB capture device and then scanning for channels using Terrestrial (8-VSB) (This corresponds to ATSC).  

It sounds like you may have already done this, but if it doesn't work you can scan the QAM frequencies (if you are connected to cable) or check [http://www.antennaweb.org](http://www.antennaweb.org) to see if you have an appropriate antenna for your location

---

### Post by rickyble on 2008-05-14
I deleted my response.  I noticed that you had it previously working but it seems to be an upgrade problem.  From the specs it looked like QAM was not supported but it is very confusing.  Good luck

---

### Post by colinnwn on 2008-05-17
Hi jlagrone,

I have no cable, and my antenna is good according to antennaweb.  It also generally works with my 2 digital TVs, though I need to replace my ethernet cabling with shielded cable to stop occasional skips.

I set it up as DVB the first time and it said it couldn't open the input.  I just did it again and was able to scan for channels.  I didn't try scanning for channels before, because in analog it would mess up your TMS/Schedules Direct service settings.  I didn't realize you should scan for digital channels.

Now I am getting digital signals between 40 and 80%.  But watching TV the screen only updates every 10 seconds or so, the picture is frequently pixelated, and the sound cuts in and out at a high frequency like the actors were holding onto jackhammers.  Every 30 seconds or so I will get a few seconds of normal sounds.

Can you point me to a likely cause or troubleshooting guide for this?

Thank you.

---

### Post by volkswagner on 2008-05-17
Open a terminal and check logs in real time. You can then try to watch live tv (leaving the terminal open).  Post the results.

```
tail -f /var/log/mythtv/mythfrontend.log
```

Or you can check logs by,

```
nano /var/log/mythtv/mythfrontend.log
```

```

nano /var/log/mythtv/mythbackend.log
```

---

### Post by colinnwn on 2008-05-19
Hi volkswagner

Thanks for looking at this.  A bunch of things look bad in the frontend log, but I'm not sure what to do to fix them.  Anything you can suggest is appreciated.

Frontend
```

2008-05-18 23:59:33.035 TV: Attempting to change from None to WatchingLiveTV
2008-05-18 23:59:33.036 Using protocol version 40
2008-05-18 23:59:34.130 NVP: Disabling Audio, params(-1,2,44100)
2008-05-18 23:59:34.146 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-05-18 23:59:34.146 VideoOutputXv: Falling back to X11 video output over a network socket.
                              *** May be very slow ***
2008-05-18 23:59:34.146 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x86a24e0) visual(0x83ae158)
                        XJ_depth(16) WxH(800x600) bpl(1600)
2008-05-18 23:59:34.146 VideoOutputXv Error: Failed to create X buffers.
2008-05-18 23:59:34.150 DPMS Deactivated
2008-05-18 23:59:34.232 Couldn't load deinterlace filter
2008-05-18 23:59:34.234 OSD Theme Dimensions W: 640 H: 480
2008-05-18 23:59:34.562 TV: Changing from None to WatchingLiveTV
2008-05-18 23:59:34.564 VideoOutputXv Error: GetRefreshRate(): X11 ModeLine query returned zeroes
2008-05-18 23:59:34.589 VideoOutputXv Error: GetRefreshRate(): X11 ModeLine query returned zeroes
2008-05-18 23:59:34.589 Video timing method: USleep with busy wait
2008-05-18 23:59:34.590 Realtime priority would require SUID as root.
2008-05-18 23:59:37.488 VideoOutputXv Error: XvMC output requested, but is not supported by display.
Xlib:  extension "XVideo-MotionCompensation" missing on display ":0.0".
2008-05-18 23:59:37.499 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
                        codec 'MPEG2' makes 'xv-blit,xshm,opengl,xlib,' available, using 'xv-blit' instead.
2008-05-18 23:59:37.506 VideoOutputXv Error: Could not find suitable XVideo surface.
2008-05-18 23:59:37.506 VideoOutputXv: Falling back to X11 video output over a network socket.
                              *** May be very slow ***
2008-05-18 23:59:37.506 VideoOutputXv Error: XCreateImage failed: XJ_disp(0x86a24e0) visual(0x83ae158)
                        XJ_depth(16) WxH(800x600) bpl(1600)
2008-05-18 23:59:37.506 VideoOutputXv Error: Failed to create X buffers.
2008-05-18 23:59:38.058 AFD: Opened codec 0x83ed640, id(MPEG2VIDEO) type(Video)
2008-05-18 23:59:38.058 AFD: codec AC3 has 6 channels
2008-05-18 23:59:38.061 AFD: Opened codec 0x85a5350, id(AC3) type(Audio)
2008-05-18 23:59:38.069 Opening audio device 'default'. ch 2(2) sr 48000
2008-05-18 23:59:38.069 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-05-18 23:59:38.094 AudioOutput Warning: Mixer attach error -2: No such file or directory
                        Check Mixer Name in Setup: '/dev/mixer'
2008-05-18 23:59:38.095 NVP: Enabling Audio
2008-05-18 23:59:38.506 WriteAudio: buffer underrun
[a bunch of these]
2008-05-18 23:59:39.378 WriteAudio: buffer underrun
2008-05-18 23:59:41.519 NVP: Timed out waiting for free video buffers.
[several of these]
2008-05-18 23:59:45.534 NVP: Timed out waiting for free video buffers.
2008-05-18 23:59:47.138 TV: Attempting to change from WatchingLiveTV to None
2008-05-18 23:59:47.144 WriteAudio: buffer underrun
2008-05-18 23:59:47.303 TV: Changing from WatchingLiveTV to None
2008-05-18 23:59:47.343 DPMS Reactivated.

```

Backend
```

2008-05-18 23:59:36.145 Preview Error: Preview process not ok.
                        fileinfo(/var/lib/mythtv/recordings/1051_20080518235933.mpg.png) exists: 0 readable: 0 size: 0
2008-05-18 23:59:47.189 TVRec(1): Changing from WatchingLiveTV to None
2008-05-18 23:59:47.265 Finished recording Unknown: channel 1051
2008-05-19 00:00:04.932 Expiring 0 MBytes for 1051 @ Sun May 18 23:58:27 2008 => Unknown
2008-05-19 00:00:04.934 Expiring 52 MBytes for 1051 @ Sun May 18 23:58:28 2008 => Unknown
2008-05-19 00:00:04.942 Expiring 0 MBytes for 1051 @ Sun May 18 23:59:33 2008 => Unknown
2008-05-19 00:00:04.950 Expiring 21 MBytes for 1051 @ Sun May 18 23:59:34 2008 => Unknown
2008-05-19 00:06:04.966 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-19 00:21:05.004 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-19 00:27:52.748 MainServer::HandleAnnounce Playback
2008-05-19 00:27:52.750 adding: myth-1 as a client (events: 0)
2008-05-19 00:27:52.752 TVRec(1): Changing from None to WatchingLiveTV
2008-05-19 00:27:52.759 TVRec(1): HW Tuner: 1->1
2008-05-19 00:27:53.827 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-05-19 00:27:54.128 Finished recording Unknown: channel 1051
2008-05-19 00:27:55.205 Finished recording Unknown: channel 1051
2008-05-19 00:27:55.342 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-05-19 00:27:55.841 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-19 00:27:55.849 Empty LocalHostName.
2008-05-19 00:27:55.849 Using localhost value of myth-1
2008-05-19 00:27:55.876 New DB connection, total: 1
2008-05-19 00:27:55.892 Connected to database 'mythconverg' at host: localhost
2008-05-19 00:27:55.896 Closing DB connection named 'DBManager0'
2008-05-19 00:27:55.899 Connected to database 'mythconverg' at host: localhost
2008-05-19 00:27:55.905 New DB connection, total: 2
2008-05-19 00:27:55.906 Connected to database 'mythconverg' at host: localhost
2008-05-19 00:27:55.914 Current Schema Version: 1214
2008-05-19 00:27:55.947 Preview Error: Previewer file '/var/lib/mythtv/recordings/1051_20080519002752.mpg' is not valid.
2008-05-19 00:27:55.950 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/1051_20080519002752.mpg'
2008-05-19 00:27:55.967 Preview Error: Preview process not ok.
                        fileinfo(/var/lib/mythtv/recordings/1051_20080519002752.mpg.png) exists: 0 readable: 0 size: 0
2008-05-19 00:28:25.736 TVRec(1): Changing from WatchingLiveTV to None
2008-05-19 00:28:25.800 Finished recording Unknown: channel 1051


```

---

### Post by volkswagner on 2008-05-19
WOW!  LOOKS LIKE MY LOGS!  What versions are you running?  Mythbuntu 7.10, 8.04, amd64, x86? Just checked back I see you are running 8.04 x86.

My problems I attribute to sound mostly.  I am using Alsa, mythbuntu 7.10AMD64 with all updates including mythtv .21.  


How is your sound connected?  What are your settings in frontend, general settings page 3(relates to sound)?  Using Alsa or pulseAudio?

I don't think I can be much help.  I would search for 5.1 sound, digital sound, multichannel, etc.

---

### Post by colinnwn on 2008-05-20
I didn't change any configs, so I think I am using Alsa but it turns out it wasn't the problem.

It was that VESA display driver was too slow.  I had to find and compile SiS native video drivers.  [http://ubuntuforums.org/showthread.php?t=615094&highlight=M671&page=8](http://ubuntuforums.org/showthread.php?t=615094&highlight=M671&page=8)
It now has good smooth picture and sound (though quiet, I need to figure out how to turn it up).

I have one remaining possibily related problem.  I recorded some over the air digital TV shows, so they are pure MPEG-2 streams never transcoded when I was using the VESA display driver. They played with VESA but the screen would only update once every several seconds. When I play them with the SiS driver in full screen mode all I see is horizontal stripes. But when they automatically preview in the 'select recordings to watch' screen, they play completely normal.  Anyone know why this is and how I can fix full screen mode?

FYI people, unless you have good Linux foo, **_do not expect to use SiS integrated video systems_**.  SiS developed 2d and 3d drivers for Linux, but they refuse to release them to anyone but their "customers."  ECS claims SiS never gave them Linux drivers.  One of the developers has released the 2d drivers outside of the official channel, but not the 3d ones.  I'd encourage you to just not support SiS products.

Thanks All.

---

### Post by jlagrone on 2008-05-20
I had some vertical lines using a laptop to test frontend capabilities at one point.  It really looked like the scanning was out of whack (ie one pass would put everything in the right place and the next would shift everything up slightly or something like that)

If you are experiencing something similar, there is a setting for video scan or something like that.  There is one somewhere in all of the playback settings and I don't remember where and my machine isn't cooperating with me at the moment.  There is also the option to change it when you are watching a program (press m if you are using a keyboard and scroll down).  On mine, the default auto detect wasn't working.  I believe progressive worked for me, but try them all to see if it makes a difference.  Hope that helps.

---

### Post by colinnwn on 2008-05-22
Thanks for the thought jlagrone.

I tried progressive, interlaced normal, and interlaced reversed, and there was no change to the picture.  It continued to look striped and very slightly diagonal falling from left to right in full screen mode.  It also won't play as an asx stream.  Still downloading the nuv file to see if that will play.

Yet in preview mode the picture is beautiful.  If this wasn't the case I would just assume it was a corrupt file.  Does anyone know what plays the previews, mplayer?  Does the same thing play full screen?  Anyone else have ideas on what is wrong?

---

### Post by Trollslayer on 2008-05-23
> **colinnwn said:**
> Hi jlagrone,

I have no cable, and my antenna is good according to antennaweb.  It also generally works with my 2 digital TVs, though I need to replace my ethernet cabling with shielded cable to stop occasional skips.

I set it up as DVB the first time and it said it couldn't open the input.  I just did it again and was able to scan for channels.  I didn't try scanning for channels before, because in analog it would mess up your TMS/Schedules Direct service settings.  I didn't realize you should scan for digital channels.

Now I am getting digital signals between 40 and 80%.  But watching TV the screen only updates every 10 seconds or so, the picture is frequently pixelated, and the sound cuts in and out at a high frequency like the actors were holding onto jackhammers.  Every 30 seconds or so I will get a few seconds of normal sounds.

Can you point me to a likely cause or troubleshooting guide for this?

Thank you.

The pixelating is called 'marco blocking' and indicates your digital signal is dropping out.
The 40-80% fluctuation is updated slowly so there could be brief dips well below this. Remember that an aerial that worked for analogue signals may not work well for digitial signals and the digitial signals may be coming from a different transmitter, this happens sometimes in the UK and you need to realign the aerial.
Hope this is of help.
BTW, QAM is cable only in the US.

---

### Post by colinnwn on 2008-05-23
Hi Trollslayer,

I resolved that part of my problem, it may have been partly environmental conditions, but I got a big improvement in picture and sound smoothness when I switched from VESA display driver to a natively compiled SiS driver.  The macro blocking has almost completely stopped.  Now my problem is I get normal picture and sound for about 1 second, then freezes 1 sec, then normal 1 sec.  This goes endlessly on.  Most recordings do this, but every once in a while, a recording will play normally the whole way through.

In the frontend log I get "NVP prebuffering pause".  I have researched many hours for the cause and solution but there seems to be no consisitent answer and nothing I have tried helped.  I tried PCI latency, disabling XvMC, disabling OpenGL, and a few other things I can't remember right now.  I'm pretty much out of ideas.

You are right about the signals, fortunately I aligned my rooftop antenna to the transmitters, and it is well within adequate size per antennaweb.org.  My 2 digital TVs receiving the same digital signal have occasional hiccups, but they are cheap Maxent and Olevia TVs and do much better at staying locked and recovering gracefully than my Dvico/Myth combo.

Thanks for reading through this long post.  If you have other thoughts I'd appreciate it.

---

