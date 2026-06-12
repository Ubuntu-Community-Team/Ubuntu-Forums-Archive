---
title: "Analog Channel Scans"
date: 2011-12-19
forum: Mythbuntu
---

### Post by jlp_engineer on 2011-12-19
I have a backend loaded with Mythbuntu 11.04 (cannot get 11.10 to boot)with 3 PVR-150's and a pcHDTV HD-5500.  I have attempted to scan for channels on the PVR-150's, but I have not gotten any channel locks.  It just flies through all the channels without giving any errors.  I have found some information that seems to indicate that analog channel scanner function in MythTV is broken, and has been since version 0.21.  I checked the bug reports and found one for the analog channel scanner, and it was unclear whether it was fixed, or just closed.  Seems as there was little concern about it getting fixed.  I am guessing this was the case since we were all supposed to be digital starting back in 2008.  Well, my local cable provider is still broadcasting 54 channels in analog, and only 5 are available as unencrypted digital.  I even contacted them and asked them if they were planning to switch over to all digital, and their reply was that they were leaving things as-is for the foreseeable future, due to the equipment investment they currently have in their infrastructure. 

Is there any plans to fix the analog channel scanner?  If not, are the clear instructions that I can find on how to setup the analog channels without being able to scan them into my setup?  

Thanks in advance to anyone willing to shed some light on this issue.

---

### Post by nickrout on 2011-12-19
> **jlp_engineer said:**
> I have a backend loaded with Mythbuntu 11.04 (cannot get 11.10 to boot)with 3 PVR-150's and a pcHDTV HD-5500.  I have attempted to scan for channels on the PVR-150's, but I have not gotten any channel locks.  It just flies through all the channels without giving any errors.  I have found some information that seems to indicate that analog channel scanner function in MythTV is broken, and has been since version 0.21.  I checked the bug reports and found one for the analog channel scanner, and it was unclear whether it was fixed, or just closed.  Seems as there was little concern about it getting fixed.  I am guessing this was the case since we were all supposed to be digital starting back in 2008.  Well, my local cable provider is still broadcasting 54 channels in analog, and only 5 are available as unencrypted digital.  I even contacted them and asked them if they were planning to switch over to all digital, and their reply was that they were leaving things as-is for the foreseeable future, due to the equipment investment they currently have in their infrastructure. 

Is there any plans to fix the analog channel scanner?  If not, are the clear instructions that I can find on how to setup the analog channels without being able to scan them into my setup?  

Thanks in advance to anyone willing to shed some light on this issue.

Update to latest 0.24-fixes via mythbuntu-repos and try again.

---

### Post by Senkoboy on 2011-12-19
>  have found some information that seems to indicate that analog channel scanner function in MythTV is broken, and has been since version 0.21



I have a PVR 150 in Myth .23, channel scanner works great.  How do you have your PVR-150 cards set up in the backend?

---

### Post by Senkoboy on 2011-12-19
Make sure the PVR-150 cards are set up as IVTV MPEG-2 encoders in the back end under card type.

---

### Post by klc5555 on 2011-12-19
It's been a couple of years since I used a 150, but that sounds pretty much like how it used to scan: flies through with no locks and no errors. But what do you have leftover in the Channel Editor under your analog Video Source? If you have something like "UNNAMED:CHANNEL 2" though "UNNAMED:CHANNEL 99" then from your PVR 150's perspective, the scan was a success. If you've got them, these "unnamed channels" are tuned to the correct analog frequencies for their channel numbers. What you then do is (for your 45 live analog channels) is edit in each channel's name, call sign, and xmltv-id number (for Schedules Direct information). Leftover "unnamed" channels are deleted.

You can edit in the extra information for each good channel in Channel Editor and delete the leftover channels. Or, you can bring up each channel in Live TV, and the "e" key brings up the on-screen edit menu. From here, the name, callsign, and xmltv id can be typed in. Then move on to the next channel in Live TV. Later, leftover "unnamed" stations are deleted en masse in Channel Editor.

If no "unnamed" channels are to be found in Channel Editor for your analog Video Source, individual analog channels may easily be added in the Channel Editor with no scan whatever. Use "Add Channel". Fill in it's channel number, a unique callsign, a name, and the channel's xmltvid number (for Schedules Direct) in page 1 of the form. Along about p. 3, where it asks for "frequency or channel", you put in the channel number (again). And that's about it.

You may have trouble with analog channel 5 and 6 --I always did, because RF interference from my power supplies always wiped out those particular frequencies. So I hope the stations on analog channels 5 and 6 are also available in digital.

---

### Post by nickrout on 2011-12-19
Well i would have assumed it is obvious that an analogue channel has no in stream information on channel names. 

Digital of course does have this information, it is part of the DVB standard.

---

### Post by jlp_engineer on 2011-12-19
Senkoboy,

I have the PVR-150's set as:

Card type: IVTV MPEG-2 encoder Card

Video Device: /dev/video0

Probed Info:        Hauppauge WinTV PVR-150 [ivtv]

Default Input: Tuner 1

Channels still scan through in about 5 seconds.  This process used to take at least a few minutes when I was running Mythbuntu 8.04.

---

### Post by nickrout on 2011-12-19
Now for the really obvious question, which I seem to have to ask in every damned thread:

What do your logs say?

---

### Post by klc5555 on 2011-12-19
> **nickrout said:**
> Well i would have assumed it is obvious that an analogue channel has no in stream information on channel names. 

Digital of course does have this information, it is part of the DVB standard.

True, but so what? The point here is that, unlike DVB, analog doesn't require scanning for Mythtv. If the OP can't get analog scanning to work in his backend setup for the PVR 150, it doesn't matter. He can set it up anyway.

---

### Post by nickrout on 2011-12-19
> **klc5555 said:**
> True, but so what? The point here is that, unlike DVB, analog doesn't require scanning for Mythtv. If the OP can't get analog scanning to work in his backend setup for the PVR 150, it doesn't matter. He can set it up anyway.

Sorry I was agreeing with you. Just trying to say that what you are saying is logical and pretty obvious when you think about it.

Of course US and Canadian subscribers have Schedules Direct to match channel numbers to actual broadcasters, simplifying the whole caboodle.

Anyway, sounds like OP is not getting any results at all, given the speed his scan is going through at.

---

### Post by klc5555 on 2011-12-20
Sorry for a bit of testiness. We do agree. I was just a bit surprised on an initial reading of the thread, since what the OP is reporting as a problem, I found to be the normal behavior for a PVR 150 scan in the years leading up to the US digital Anschluss of 2009, ie. the 15-second scan with no locks. Myth 0.19-ish to about 0.21. 

The only question was whether the card would leave "placeholders" for channels 2-99 in the Channel Editor (the "UNKNOWN"s), in which case you edit the forms that actually correspond to real stations and delete the rest, or whether nothing at all is left in the Channel Editor, in which case you use Add Channel to add the ones that correspond with real stations. Either way, the PVR 150 and Mythtv already know where to tune for the traditional analogs --no scan+locks are necessary. 

Alternatively, since the OP ought to have 2 Video Sources set up, one digital Video Source for his 5 DVB stations and one analog Video Source, and this one analog Video Source should be bound both to the PVR 150(s) and to the analog half of the pchdtv-hd5500, the OP could just as easily do his analog scan from the analog side of the pchdtv-hd5500, if he really insists on doing an analog scan and he suspects a pvr 150 issue. It's the same analog tuning data.

---

### Post by jlp_engineer on 2011-12-20
> **nickrout said:**
> Now for the really obvious question, which I seem to have to ask in every damned thread:

What do your logs say?

Here is the relevant portion of the backend log just after an analog scan attempt on the PVR-150 at /dev/video0:

011-12-20 00:11:06.815 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 00:26:06.894 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 00:41:06.984 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 00:56:07.074 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 01:11:07.156 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 01:26:07.239 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 01:41:07.325 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 01:56:07.410 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 02:11:07.489 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 02:26:07.571 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 02:41:07.656 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 02:56:07.734 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 03:11:07.824 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 03:26:07.910 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 03:41:07.993 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 03:56:08.073 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 04:11:08.159 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 04:26:08.264 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 04:41:08.346 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 04:56:08.432 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 05:11:08.517 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 05:26:08.595 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 05:41:08.667 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 05:56:08.745 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 06:11:08.830 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 06:26:08.913 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 06:41:08.995 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 06:56:09.081 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 07:11:09.168 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 07:26:09.260 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 07:41:09.330 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 07:56:09.420 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 08:11:09.521 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 08:26:09.599 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 08:41:09.680 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 08:56:09.761 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 09:11:09.845 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 09:26:09.931 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 09:41:10.020 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 09:56:10.102 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 10:11:10.190 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 10:26:10.260 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 10:41:10.352 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 10:56:10.429 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 11:11:10.513 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 11:26:10.595 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 11:41:10.678 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 11:56:10.757 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 12:11:10.840 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 12:26:10.918 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 12:41:11.005 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 12:56:11.083 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 13:11:11.165 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 13:26:11.253 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 13:41:11.338 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 13:56:11.425 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 14:11:11.519 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 14:26:11.605 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 14:41:11.698 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 14:56:11.778 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 15:11:11.861 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 15:26:11.941 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 15:41:12.026 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 15:56:12.106 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 16:11:12.184 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 16:26:12.275 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 16:41:12.388 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 16:56:12.476 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 17:11:12.560 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 17:26:12.646 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 17:41:12.731 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 17:56:12.812 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 18:11:12.900 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 18:26:12.987 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 18:41:13.078 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 18:56:13.149 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 19:11:13.222 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 19:26:13.295 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 19:41:13.375 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 19:48:33.448 mythbackend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-12-20 19:48:33.505 Using runtime prefix = /usr
2011-12-20 19:48:33.548 Using configuration directory = /home/mythtv/.mythtv
2011-12-20 19:48:33.582 Empty LocalHostName.
2011-12-20 19:48:33.623 Using localhost value of MYTHBE
2011-12-20 19:48:33.681 New DB connection, total: 1
2011-12-20 19:48:33.727 Connected to database 'mythconverg' at host: localhost
2011-12-20 19:48:33.773 Closing DB connection named 'DBManager0'
2011-12-20 19:48:33.808 Connected to database 'mythconverg' at host: localhost
2011-12-20 19:48:33.851 Current locale EN_US
2011-12-20 19:48:33.891 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-12-20 19:48:33.945 Current MythTV Schema Version (DBSchemaVer): 1264
2011-12-20 19:48:33.990 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-12-20 19:48:34.033 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2011-12-20 19:48:34.069 MythBackend: Starting up as the master server.
2011-12-20 19:48:34.111 New DB connection, total: 2
2011-12-20 19:48:34.153 Connected to database 'mythconverg' at host: localhost
2011-12-20 19:48:34.195 New DB connection, total: 3
2011-12-20 19:48:34.228 Connected to database 'mythconverg' at host: localhost
2011-12-20 19:48:34.408 format_to_mode() does not recognize V4L1
2011-12-20 19:48:34.634 format_to_mode() does not recognize V4L1
2011-12-20 19:48:34.844 format_to_mode() does not recognize V4L1
2011-12-20 19:48:34.881 Channel(/dev/video4) Error: GetCurrentChannelNum(1): Failed to find Channel
2011-12-20 19:48:34.920 Channel(/dev/video4)::TuneTo(1): Error, failed to find channel.
2011-12-20 19:48:35.104 DVBChan(4:/dev/dvb/adapter0/frontend0) Error: SetChannelByString(1): Failed to initialize multiplex options
2011-12-20 19:48:35.302 DVBChan(5:/dev/dvb/adapter0/frontend0) Error: SetChannelByString(1): Failed to initialize multiplex options
2011-12-20 19:48:35.486 DVBChan(6:/dev/dvb/adapter1/frontend0) Error: SetChannelByString(1): Failed to initialize multiplex options
2011-12-20 19:48:35.679 DVBChan(7:/dev/dvb/adapter1/frontend0) Error: SetChannelByString(1): Failed to initialize multiplex options
2011-12-20 19:48:35.714 New DB scheduler connection
2011-12-20 19:48:35.755 Connected to database 'mythconverg' at host: localhost
2011-12-20 19:48:35.801 Main::Registering HttpStatus Extension
2011-12-20 19:48:35.839 Enabled verbose msgs:  important general
2011-12-20 19:48:35.879 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-12-20 19:48:38.806 Reschedule requested for id -1.
2011-12-20 19:48:38.917 Scheduled 0 items in 0.1 = 0.05 match + 0.07 place
2011-12-20 19:48:38.955 Seem to be woken up by USER

I am not to concerned about the DVB errors.  I will be researching and fixing those later, unless you may know what they are all about.

---

### Post by nickrout on 2011-12-20
Exactly what version of mythtv are you running? 

```
dpkg -i mythtv-backend
mythbackend --version
```

---

### Post by jlp_engineer on 2011-12-20
> **nickrout said:**
> Exactly what version of mythtv are you running? 

```
dpkg -i mythtv-backend
mythbackend --version
```

When I type "sudo dpkg -i mythtv-backend", I get:

dpkg: error processing mythtv-backend (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mythtv-backend

When I type "mythbackend --version", I get:

Please attach all output as a file in bug reports.
MythTV Version   : v0.24-243-g9ba3ece
MythTV Branch    : fixes/0.24
Network Protocol : 63
Library API      : 0.24.20101129-1
QT Version       : 4.7.2
Options compiled in:
 linux debug using_alsa using_oss using_pulse using_pulseoutput using_backend using_bindings_perl using_bindings_python using_dvb using_firewire using_frontend using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l2 using_x11 using_xrandr using_xv using_bindings_perl using_bindings_python using_mythtranscode using_opengl using_vdpau using_ffmpeg_threads using_live using_mheg

Seems that I am already running the 0.24 fixes branch, as one of your previous posts would suggest.  Thank you for your interest in my issue.  I am learning something with every post I read.

---

### Post by jlp_engineer on 2011-12-20
> **klc5555 said:**
> Alternatively, since the OP ought to have 2 Video Sources set up, one digital Video Source for his 5 DVB stations and one analog Video Source, and this one analog Video Source should be bound both to the PVR 150(s) and to the analog half of the pchdtv-hd5500, the OP could just as easily do his analog scan from the analog side of the pchdtv-hd5500, if he really insists on doing an analog scan and he suspects a pvr 150 issue. It's the same analog tuning data.

I configured the analog half of the pcHDTV HD-5500 (Analog V4L capture card, /dev/video1), and it does exactly the same thing as the PVR-150's.  No channel locks, and the process starts at 5%, and never goes any higher, and is completed in several seconds.  At least the digital tuner scans are coming up with some encrypted and some non-conflicting (whatever that means) MPEG channels.

---

### Post by nickrout on 2011-12-21
> **jlp_engineer said:**
> When I type "sudo dpkg -i mythtv-backend", I get:

dpkg: error processing mythtv-backend (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mythtv-backend

When I type "mythbackend --version", I get:

Please attach all output as a file in bug reports.
MythTV Version   : v0.24-243-g9ba3ece
MythTV Branch    : fixes/0.24
Network Protocol : 63
Library API      : 0.24.20101129-1
QT Version       : 4.7.2
Options compiled in:
 linux debug using_alsa using_oss using_pulse using_pulseoutput using_backend using_bindings_perl using_bindings_python using_dvb using_firewire using_frontend using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l2 using_x11 using_xrandr using_xv using_bindings_perl using_bindings_python using_mythtranscode using_opengl using_vdpau using_ffmpeg_threads using_live using_mheg

Seems that I am already running the 0.24 fixes branch, as one of your previous posts would suggest.  Thank you for your interest in my issue.  I am learning something with every post I read.

mea culpa, dpkg -i should be mythtv -l (lower case L).

I recall that there was a problem with one version of mythbuntu and analogue because of a mismatch between kernel options (v4l1 was dropped) and mythtv (still trying to compile with v4l1 support). I think it was 11.04 but I am not 100% sure.

An update to the latest mythtv fixed it, because the compile options were changed to remove the need for v4l1 support in the kernel.

I am not sure if this bug affects you, but you can only improve things by updating to the latest 0.24.1-fixes (note the .1)

In short go to [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos) and follow the instructions. 

quick version:

```
wget http://www.mythbuntu.org/files/mythbuntu-repos.deb
sudo dpkg -i mythbuntu-repos.deb
```

when asked, choose to activate the repo and update to 0.24.x or 0.24.1

```
sudo apt-get update
sudo apt-get upgrade
```

Reboot for the hell of it and try again :)

---

### Post by klc5555 on 2011-12-21
> **jlp_engineer said:**
> I configured the analog half of the pcHDTV HD-5500 (Analog V4L capture card, /dev/video1), and it does exactly the same thing as the PVR-150's.  No channel locks, and the process starts at 5%, and never goes any higher, and is completed in several seconds.  At least the digital tuner scans are coming up with some encrypted and some non-conflicting (whatever that means) MPEG channels.

So likely it's either just analog scanning, or it's the V4L1 kernel support glitch that nickrout suspects. But it also almost sounds like you may have put the digital and the analog tuners on the same Video Source. If this were the case, it would be unworkable.

Anyway, are you able to add an analog channel manually to your analog Video Source in Channel Editor? (Lacking any configured analog channels, mythtv is trying to tune your pvr150 to ch. 1, which doesn't exist.) Try adding one analog channel in Channel Editor and restart the backend. If you can get livetv through it, then the problem is just analog scanning, and you're in business. Just repeat the channel-adding process in Channel Editor for each of your analog channels (except probably 5 and 6, which power supply RF interference will likely render unusable). From my own experience, adding the entire old Comcast run from channel 2 through 96 including xmltvids in Channel Editor used to take about an hour and a half.

If, of course, you can't add a single working analog channel manually, then your problem is not simple scanning and you can eliminate this theory.

---

### Post by jlp_engineer on 2011-12-21
I began the whole process by loading the default option of Master Backend / Frontend. I decided to remove the Frontend, and make this system just a backend server, since I had purchased a Zotac MAG to use as a frontend.  Thinking that removing the frontend, and also installing Freevo to experiment with (I have since removed Freevo), I may have messed things up to the point where MythTV is not acting like it is supposed to.  

I am loading Mythbuntu 11.04, since 11.10 will not boot on my system.  It halts and locks up my system at:

[c1533b7e] ? Kernel_thread_helper +0x6/0x10

I will see where I am after the updates have loaded and I have installed the firmware for my ATi HDTV Wonder card, which I have not gotten to work, but may also be playing a part in this.  I will also make sure that I install the digital listing source and the analog listing source on the appropriate tuners.  I will see if the stock version of MythTV included with 11.04 has the issue, or if it is only when I update it.  I would try updating the kernel for the V4L bug, but as I indicated above, 11.10 locks up my system.

Thanks to both of you (nickrout & klc5555).  I will be back to post my progress.

---

### Post by nickrout on 2011-12-21
> **jlp_engineer said:**
> I began the whole process by loading the default option of Master Backend / Frontend. I decided to remove the Frontend, and make this system just a backend server, since I had purchased a Zotac MAG to use as a frontend.  Thinking that removing the frontend, and also installing Freevo to experiment with (I have since removed Freevo), I may have messed things up to the point where MythTV is not acting like it is supposed to.  

I am loading Mythbuntu 11.04, since 11.10 will not boot on my system.  It halts and locks up my system at:

[c1533b7e] ? Kernel_thread_helper +0x6/0x10

I will see where I am after the updates have loaded and I have installed the firmware for my ATi HDTV Wonder card, which I have not gotten to work, but may also be playing a part in this.  I will also make sure that I install the digital listing source and the analog listing source on the appropriate tuners.  I will see if the stock version of MythTV included with 11.04 has the issue, or if it is only when I update it.  I would try updating the kernel for the V4L bug, but as I indicated above, 11.10 locks up my system.

Thanks to both of you (nickrout & klc5555).  I will be back to post my progress.

The v4l bug is not fixed by updating the kernel, it is fixed by updating mythtv to the latest version. You are not running the latest version. Yours is 0.24 from November 2010. Mine is 0.24.1 from December 2011.

---

### Post by jlp_engineer on 2011-12-24
> **klc5555 said:**
> So likely it's either just analog scanning, or it's the V4L1 kernel support glitch that nickrout suspects. But it also almost sounds like you may have put the digital and the analog tuners on the same Video Source. If this were the case, it would be unworkable. 

I checked, and I am not sure if there was some mix up there or not, so I just started over (format/reload), making certain that I had created the correct channel lineup on ScheduleDirect, with the analog channels in one, and the digital channels in the other.  I then went into the channel editor and made sure that at least 2 - 83 were correct.  With the digital channels in there, however, the editor has a mind blowing 900 channels.  Only about half a dozen or so are unencrypted and useful. I also noticed then when the digital tuners got done with their scans, I had a bunch of channels inserted into the channels, like 80-460, and 80-471, etc.  Is this what I should expect from the digital side?

Attempting to tune any of the analog channels results in snow, so at least there is that...it's a beginning.  But all the digital channels are crystal clear and with no distortion or stuttering.  Once in a while, when I switch inputs to one of the other analog tuners, and then change a channel, I get a black screen and then MythTV puts me back at the main menu with the error "Error opening jump program file buffer". :(


> **klc5555 said:**
> Anyway, are you able to add an analog channel manually to your analog Video Source in Channel Editor? (Lacking any configured analog channels, mythtv is trying to tune your pvr150 to ch. 1, which doesn't exist.) Try adding one analog channel in Channel Editor and restart the backend. If you can get livetv through it, then the problem is just analog scanning, and you're in business. Just repeat the channel-adding process in Channel Editor for each of your analog channels (except probably 5 and 6, which power supply RF interference will likely render unusable). From my own experience, adding the entire old Comcast run from channel 2 through 96 including xmltvids in Channel Editor used to take about an hour and a half.

If, of course, you can't add a single working analog channel manually, then your problem is not simple scanning and you can eliminate this theory.

Well, I didn't need to any of them manually, as pulled the channels down from SchedulesDirect, and they all looked good.  I made sure that each lineup profile was set to the correct channel in the channel editor as well.  All the analog channels were assigned with the analog profile, and the digital channels with the digital profile.  Although, with the funky channel numbering that the digital tuner scans are giving me, I am not sure the channel lineup in the editor for the digital channels does all that much good.:confused:

Any other ideas?

---

### Post by jlp_engineer on 2011-12-24
> **nickrout said:**
> The v4l bug is not fixed by updating the kernel, it is fixed by updating mythtv to the latest version. You are not running the latest version. Yours is 0.24 from November 2010. Mine is 0.24.1 from December 2011.

OK, I am running version 0.24.1 now, as the following version check tells me:

Please attach all output as a file in bug reports.
MythTV Version   : v0.24.1-112-g40f3bae
MythTV Branch    : fixes/0.24
Network Protocol : 63
Library API      : 0.24.20110505-1
QT Version       : 4.7.2
Options compiled in:
 linux profile using_alsa using_oss using_pulse using_pulseoutput using_backend using_bindings_perl using_bindings_python using_crystalhd using_dvb using_firewire using_frontend using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_bindings_perl using_bindings_python using_mythtranscode using_opengl using_vdpau using_ffmpeg_threads using_live using_mheg

Any attempt at an analog channel scan on the PVR-150's or the analog side of the HD-5500 results super quick channel scans.  When I run the frontend and try to tune any analog channels, it results in either snow, or a blank screen. The blank screen is often followed several seconds later by the error "Error opening jump program file buffer".  Running the frontend and tuning any of the unencrypted digital channels works perfectly.   

Also, when I am configuring the tuners, I get many different video devices, and it is difficult to determine if I am selecting the right ones.  In the Capture Card setup, when I select IVTV MPEG-2 encoder card, /dev/video0, /dev/video1, /dev/video4, as well as video24, video25, video28, video32, video33, and video36.  They all show up as "Hauppauge WinTV PVR-150" cards.  Under the Analog V4L selection, I also get /dev/video2 and /dev/video3 for the analog sides of the ATi HDTV Wonder and the pcHDTV HD5500 cards.  I have been using the single digit numbers for the tuner configurations.  Is this correct?  What are the double digit video devices for?

The last few pages of the backend log:

2011-12-24 15:07:58.141 RecBase(1:/dev/video0): GetKeyframePositions(16,9223372036854775807,#1) out of 2
2011-12-24 15:07:58.342 RecBase(1:/dev/video0): GetKeyframePositions(16,9223372036854775807,#1) out of 2
2011-12-24 15:08:34.604 Expiring 13 MB for 2980 at 2011-12-24T15:05:05 => Unknown
2011-12-24 15:08:34.652 Expiring 0 MB for 2918 at 2011-12-24T15:05:45 => Unknown
2011-12-24 15:08:34.694 Expiring 13 MB for 2918 at 2011-12-24T15:05:47 => Unknown
2011-12-24 15:08:34.736 Expiring 0 MB for 2675 at 2011-12-24T15:06:29 => Unknown
2011-12-24 15:08:55.130 TVRec(1): HW Tuner: 1->1
2011-12-24 15:08:55.370 LoadFromScheduler(): Error, called from backend.
2011-12-24 15:08:55.375 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2011-12-24 15:08:55.425 Finished recording Unknown: channel 1024
2011-12-24 15:08:55.660 MainServer::ANN Monitor
2011-12-24 15:08:55.699 adding: MYTHBE as a client (events: 0)
2011-12-24 15:08:55.721 Finished recording Unknown: channel 1035
2011-12-24 15:08:55.743 MainServer::ANN Monitor
2011-12-24 15:08:55.790 LoadFromScheduler(): Error, called from backend.
2011-12-24 15:08:55.796 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2011-12-24 15:08:55.826 adding: MYTHBE as a client (events: 1)
2011-12-24 15:08:55.872 recording already exists...
2011-12-24 15:08:56.002 Finished recording Unknown: channel 1035
2011-12-24 15:08:58.104 RecBase(1:/dev/video0): GetKeyframePositions(16,9223372036854775807,#0) out of 2
Error in my_thread_global_end(): 1 threads didn't exit
2011-12-24 15:09:27.050 TVRec(1): HW Tuner: 1->1
2011-12-24 15:09:27.278 LoadFromScheduler(): Error, called from backend.
2011-12-24 15:09:27.283 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2011-12-24 15:09:27.335 Finished recording Unknown: channel 1035
2011-12-24 15:09:27.565 MainServer::ANN Monitor
2011-12-24 15:09:27.601 adding: MYTHBE as a client (events: 0)
2011-12-24 15:09:27.615 Finished recording Unknown: channel 1030
2011-12-24 15:09:27.644 MainServer::ANN Monitor
2011-12-24 15:09:27.691 LoadFromScheduler(): Error, called from backend.
2011-12-24 15:09:27.694 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2011-12-24 15:09:27.727 adding: MYTHBE as a client (events: 1)
2011-12-24 15:09:27.778 recording already exists...
2011-12-24 15:09:27.924 Finished recording Unknown: channel 1030
2011-12-24 15:09:30.033 RecBase(1:/dev/video0): GetKeyframePositions(16,9223372036854775807,#0) out of 2
Error in my_thread_global_end(): 1 threads didn't exit
2011-12-24 15:09:38.061 TVRec(1): HW Tuner: 1->1
2011-12-24 15:09:38.310 LoadFromScheduler(): Error, called from backend.
2011-12-24 15:09:38.315 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2011-12-24 15:09:38.365 Finished recording Unknown: channel 1030
2011-12-24 15:09:38.599 MainServer::ANN Monitor
2011-12-24 15:09:38.631 adding: MYTHBE as a client (events: 0)
2011-12-24 15:09:38.659 Finished recording Unknown: channel 1027
2011-12-24 15:09:38.666 MainServer::ANN Monitor
2011-12-24 15:09:38.732 adding: MYTHBE as a client (events: 1)
2011-12-24 15:09:38.709 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2011-12-24 15:09:38.704 LoadFromScheduler(): Error, called from backend.
2011-12-24 15:09:38.854 recording already exists...
2011-12-24 15:09:38.907 Finished recording Unknown: channel 1027
2011-12-24 15:09:40.814 RecBase(1:/dev/video0): GetKeyframePositions(1,9223372036854775807,#2) out of 3
2011-12-24 15:09:40.930 RecBase(1:/dev/video0): GetKeyframePositions(1,9223372036854775807,#2) out of 3
2011-12-24 15:09:46.619 TVRec(1): HW Tuner: 1->1
2011-12-24 15:09:46.826 LoadFromScheduler(): Error, called from backend.
2011-12-24 15:09:46.831 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2011-12-24 15:09:46.884 Finished recording Unknown: channel 1027
2011-12-24 15:09:47.142 Finished recording Unknown: channel 1023
2011-12-24 15:09:47.150 MainServer::ANN Monitor
2011-12-24 15:09:47.226 adding: MYTHBE as a client (events: 0)
2011-12-24 15:09:47.194 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2011-12-24 15:09:47.188 LoadFromScheduler(): Error, called from backend.
2011-12-24 15:09:47.313 MainServer::ANN Monitor
2011-12-24 15:09:47.370 Finished recording Unknown: channel 1023
2011-12-24 15:09:47.393 adding: MYTHBE as a client (events: 1)
Error in my_thread_global_end(): 1 threads didn't exit
2011-12-24 15:09:50.344 DevRdB(/dev/video0) Error: Poll giving up
2011-12-24 15:09:50.379 MPEGRec(/dev/video0) Error: Device error detected
2011-12-24 15:09:53.479 DevRdB(/dev/video0) Error: Poll giving up
2011-12-24 15:09:53.526 MPEGRec(/dev/video0) Error: Device error detected
2011-12-24 15:09:56.622 DevRdB(/dev/video0) Error: Poll giving up
2011-12-24 15:09:56.659 MPEGRec(/dev/video0) Error: Device error detected
2011-12-24 15:09:57.538 TVRec(1): Changing from WatchingLiveTV to None
2011-12-24 15:09:59.754 DevRdB(/dev/video0) Error: Poll giving up
2011-12-24 15:09:59.802 MPEGRec(/dev/video0) Error: Device error detected
2011-12-24 15:10:04.538 MainServer::ANN Playback
2011-12-24 15:10:04.589 adding: MYTHBE as a client (events: 0)
2011-12-24 15:10:04.636 ERROR: Master backend tried to connect back to itself!
2011-12-24 15:10:04.690 MainServer::ANN Playback
2011-12-24 15:10:04.748 adding: MYTHBE as a client (events: 0)
2011-12-24 15:10:34.790 Expiring 131 MB for 2675 at 2011-12-24T15:06:31 => Unknown
2011-12-24 15:10:34.837 Expiring 0 MB for 1024 at 2011-12-24T15:07:55 => Unknown
2011-12-24 15:10:34.871 Expiring 33 MB for 1024 at 2011-12-24T15:07:56 => Unknown
2011-12-24 15:10:34.904 Expiring 14 MB for 1035 at 2011-12-24T15:08:56 => Unknown
2011-12-24 15:12:34.958 Expiring 0 MB for 1035 at 2011-12-24T15:08:55 => Unknown
2011-12-24 15:12:34.996 Expiring 0 MB for 1030 at 2011-12-24T15:09:27 => Unknown
2011-12-24 15:12:35.029 Expiring 6 MB for 1030 at 2011-12-24T15:09:28 => Unknown
2011-12-24 15:12:35.063 Expiring 0 MB for 1027 at 2011-12-24T15:09:38 => Unknown
2011-12-24 15:12:35.096 Expiring 4 MB for 1027 at 2011-12-24T15:09:39 => Unknown
2011-12-24 15:12:35.130 Expiring 0 MB for 1023 at 2011-12-24T15:09:46 => Unknown
2011-12-24 15:14:35.171 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min

The last several pages of the frontend log:

2011-12-24 15:04:23.039 Player(1), Error: Unknown recorder error, exiting decoder
2011-12-24 15:04:23.088 OSD: Base theme size: 1280x720
2011-12-24 15:04:23.088 OSD: Scaling factors: 0.4125x0.666667
2011-12-24 15:04:23.104 TV: Attempting to change from WatchingLiveTV to None
2011-12-24 15:04:23.105 MythUIHelper, Error: LoadScaleImage(uparrow_alt.png)Unable to find image file
2011-12-24 15:04:23.105 MythUIHelper, Error: LoadScaleImage(downarrow_alt.png)Unable to find image file
2011-12-24 15:04:23.115 MythPainter: 7 images not yet de-allocated.
2011-12-24 15:04:23.361 TV: Changing from WatchingLiveTV to None
2011-12-24 15:04:23.427 TV: Attempting to change from None to WatchingLiveTV
2011-12-24 15:04:23.427 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-12-24 15:04:23.428 Using protocol version 63
2011-12-24 15:04:23.584 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-12-24 15:04:23.585 Using protocol version 63
2011-12-24 15:04:23.656 Spawning LiveTV Recorder -- begin
2011-12-24 15:04:23.847 Spawning LiveTV Recorder -- end
2011-12-24 15:04:23.855 We have a playbackURL(/var/lib/mythtv/livetv/2930_20111224150423.mpg) & cardtype(DUMMY)
2011-12-24 15:04:23.856 We have a RingBuffer
2011-12-24 15:04:23.857 TV Error: LiveTV not successfully started
2011-12-24 15:04:26.613 TV: Attempting to change from None to WatchingLiveTV
2011-12-24 15:04:26.613 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-12-24 15:04:26.614 Using protocol version 63
2011-12-24 15:04:26.738 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-12-24 15:04:26.738 Using protocol version 63
2011-12-24 15:04:26.817 Spawning LiveTV Recorder -- begin
2011-12-24 15:04:27.016 Spawning LiveTV Recorder -- end
2011-12-24 15:04:27.023 We have a playbackURL(/var/lib/mythtv/livetv/2930_20111224150426.mpg) & cardtype(DUMMY)
2011-12-24 15:04:27.023 We have a RingBuffer
2011-12-24 15:04:27.151 ALSA, Error: snd_pcm_open("default"): No such file or directory
2011-12-24 15:04:27.165 VideoOutputXv: XVideo Adaptor Name: 'Radeon Textured Video'
2011-12-24 15:04:27.218 OSD: Base theme size: 1280x720
2011-12-24 15:04:27.218 OSD: Scaling factors: 0.5625x0.8
2011-12-24 15:04:27.259 OSD: Base theme size: 1280x720
2011-12-24 15:04:27.259 OSD: Scaling factors: 0.5625x0.8
2011-12-24 15:04:27.289 Player(2): Video timing method: DRM
2011-12-24 15:04:27.304 TV: Changing from None to WatchingLiveTV
2011-12-24 15:04:27.304 TV: State is LiveTV & mctx == ctx
2011-12-24 15:04:27.306 TV: UpdateOSDInput done
2011-12-24 15:04:27.306 TV: UpdateLCD done
2011-12-24 15:04:27.306 TV: ITVRestart done
2011-12-24 15:04:27.385 VideoOutput: Created YV12 OSD.
2011-12-24 15:04:28.997 VideoOutputXv: XVideo Adaptor Name: 'Radeon Textured Video'
2011-12-24 15:04:29.031 OSD: Base theme size: 1280x720
2011-12-24 15:04:29.031 OSD: Scaling factors: 0.4125x0.666667
2011-12-24 15:04:29.073 AFD: Opened codec 0xad6a7ce0, id(MPEG2VIDEO) type(Video)
2011-12-24 15:04:29.074 AFD: codec AC3 has 2 channels
2011-12-24 15:04:29.074 AFD: Opened codec 0xad691560, id(AC3) type(Audio)
2011-12-24 15:04:29.074 AFD: codec AC3 has 2 channels
2011-12-24 15:04:29.075 AFD: Opened codec 0xad6af8c0, id(AC3) type(Audio)
2011-12-24 15:04:29.253 ALSA, Error: snd_pcm_open("default"): No such file or directory
2011-12-24 15:04:29.253 AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2011-12-24 15:04:29.254 ALSA, Error: snd_pcm_open("default"): No such file or directory
2011-12-24 15:04:29.254 AudioOutput Error: Aborting reconfigure
2011-12-24 15:04:29.254 AudioPlayer: Disabling Audio, reason is: Aborting reconfigure
2011-12-24 15:04:29.307 AFD: Resetting byte context eof (livetv 1 was eof 0)
2011-12-24 15:04:29.581 VideoOutput: Created YV12 OSD.
2011-12-24 15:04:33.155 OSD: Base theme size: 1280x720
2011-12-24 15:04:33.155 OSD: Scaling factors: 0.4125x0.666667
2011-12-24 15:04:33.171 MythUIHelper, Error: LoadScaleImage(uparrow_alt.png)Unable to find image file
2011-12-24 15:04:33.175 MythUIHelper, Error: LoadScaleImage(downarrow_alt.png)Unable to find image file
2011-12-24 15:04:38.190 TV: OSDDialogEvent: result 3 text Schedule action DIALOG_MENU_SCHEDULE_0
2011-12-24 15:04:39.504 TV: OSDDialogEvent: result 0 text Program Guide action GUIDE
2011-12-24 15:04:39.538 pause_active: 0
2011-12-24 15:04:51.586 OSD: Base theme size: 1280x720
2011-12-24 15:04:51.586 OSD: Scaling factors: 0.608594x0.436111
2011-12-24 15:05:03.072 OSD: Base theme size: 1280x720
2011-12-24 15:05:03.072 OSD: Scaling factors: 0.308594x0.5
2011-12-24 15:05:05.608 RingBuf(/var/lib/mythtv/livetv/2980_20111224150505.mpg) Warning: Not starting read ahead thread, already running
2011-12-24 15:05:06.655 OSD: Base theme size: 1280x720
2011-12-24 15:05:06.655 OSD: Scaling factors: 0.421094x0.5
2011-12-24 15:05:06.711 AFD: Opened codec 0x9f5d250, id(MPEG2VIDEO) type(Video)
2011-12-24 15:05:06.711 AFD: codec AC3 has 2 channels
2011-12-24 15:05:06.711 AFD: Opened codec 0x9ce6100, id(AC3) type(Audio)
2011-12-24 15:05:06.712 AFD: codec AC3 has 2 channels
2011-12-24 15:05:06.712 AFD: Opened codec 0x9f6eb20, id(AC3) type(Audio)
2011-12-24 15:05:06.885 ALSA, Error: snd_pcm_open("default"): No such file or directory
2011-12-24 15:05:06.885 AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2011-12-24 15:05:06.885 ALSA, Error: snd_pcm_open("default"): No such file or directory
2011-12-24 15:05:06.885 AudioOutput Error: Aborting reconfigure
2011-12-24 15:05:06.885 AudioPlayer: Disabling Audio, reason is: Aborting reconfigure
2011-12-24 15:05:06.975 AFD: Resetting byte context eof (livetv 1 was eof 0)
2011-12-24 15:05:07.223 VideoOutput: Created YV12 OSD.
2011-12-24 15:05:19.952 OSD: Base theme size: 1280x720
2011-12-24 15:05:19.952 OSD: Scaling factors: 0.421094x0.5
2011-12-24 15:05:19.988 MythUIHelper, Error: LoadScaleImage(uparrow_alt.png)Unable to find image file
2011-12-24 15:05:19.992 MythUIHelper, Error: LoadScaleImage(downarrow_alt.png)Unable to find image file
2011-12-24 15:05:23.737 TV: OSDDialogEvent: result 3 text Navigate action DIALOG_MENU_NAVIGATE_0
2011-12-24 15:05:25.304 TV: OSDDialogEvent: result -1 text NAVIGATE action DIALOG_MENU_MAIN_0
2011-12-24 15:05:27.352 TV: OSDDialogEvent: result 4 text Schedule action DIALOG_MENU_SCHEDULE_0
2011-12-24 15:05:28.352 TV: OSDDialogEvent: result 0 text Program Guide action GUIDE
2011-12-24 15:05:28.385 pause_active: 0
2011-12-24 15:05:47.704 RingBuf(/var/lib/mythtv/livetv/2918_20111224150547.mpg) Warning: Not starting read ahead thread, already running
2011-12-24 15:05:48.751 AFD: Opened codec 0x9f5d250, id(MPEG2VIDEO) type(Video)
2011-12-24 15:05:48.751 AFD: codec AC3 has 2 channels
2011-12-24 15:05:48.752 AFD: Opened codec 0x9ce6100, id(AC3) type(Audio)
2011-12-24 15:05:48.752 AFD: codec AC3 has 2 channels
2011-12-24 15:05:48.753 AFD: Opened codec 0x9f93dc0, id(AC3) type(Audio)
2011-12-24 15:05:49.116 ALSA, Error: snd_pcm_open("default"): No such file or directory
2011-12-24 15:05:49.116 AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2011-12-24 15:05:49.116 ALSA, Error: snd_pcm_open("default"): No such file or directory
2011-12-24 15:05:49.116 AudioOutput Error: Aborting reconfigure
2011-12-24 15:05:49.116 AudioPlayer: Disabling Audio, reason is: Aborting reconfigure
2011-12-24 15:05:49.177 AFD: Resetting byte context eof (livetv 1 was eof 0)
2011-12-24 15:05:49.334 OSD: Base theme size: 1280x720
2011-12-24 15:05:49.335 OSD: Scaling factors: 0.5625x0.666667
2011-12-24 15:05:58.502 OSD: Base theme size: 1280x720
2011-12-24 15:05:58.503 OSD: Scaling factors: 0.5625x0.666667
2011-12-24 15:05:58.522 MythUIHelper, Error: LoadScaleImage(uparrow_alt.png)Unable to find image file
2011-12-24 15:05:58.524 MythUIHelper, Error: LoadScaleImage(downarrow_alt.png)Unable to find image file
2011-12-24 15:06:01.236 TV: OSDDialogEvent: result 3 text Navigate action DIALOG_MENU_NAVIGATE_0
2011-12-24 15:06:02.436 TV: OSDDialogEvent: result -1 text NAVIGATE action DIALOG_MENU_MAIN_0
2011-12-24 15:06:04.902 TV: OSDDialogEvent: result 4 text Schedule action DIALOG_MENU_SCHEDULE_0
2011-12-24 15:06:06.083 TV: OSDDialogEvent: result 0 text Program Guide action GUIDE
2011-12-24 15:06:06.117 pause_active: 0
2011-12-24 15:06:31.689 RingBuf(/var/lib/mythtv/livetv/2675_20111224150631.mpg) Warning: Not starting read ahead thread, already running
2011-12-24 15:06:34.334 OSD: Base theme size: 1280x720
2011-12-24 15:06:34.334 OSD: Scaling factors: 1.5x1.5
2011-12-24 15:06:34.405 AFD: Opened codec 0xaa9e5ba0, id(MPEG2VIDEO) type(Video)
2011-12-24 15:06:34.405 AFD: codec AC3 has 2 channels
2011-12-24 15:06:34.406 AFD: Opened codec 0xab8ed880, id(AC3) type(Audio)
2011-12-24 15:06:34.948 ALSA, Error: snd_pcm_open("default"): No such file or directory
2011-12-24 15:06:34.948 AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2011-12-24 15:06:34.949 ALSA, Error: snd_pcm_open("default"): No such file or directory
2011-12-24 15:06:34.949 AudioOutput Error: Aborting reconfigure
2011-12-24 15:06:34.949 AudioPlayer: Disabling Audio, reason is: Aborting reconfigure
2011-12-24 15:06:35.006 AFD: Resetting byte context eof (livetv 1 was eof 0)
2011-12-24 15:06:35.119 Player(2): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAUULLL
2011-12-24 15:06:35.136 Player(2): Waited 100ms for video buffers LLAAAAAAAAAAAAAAAAAAAAAAAAUUuLU
2011-12-24 15:06:35.367 VideoOutput: Created YV12 OSD.
2011-12-24 15:07:14.397 OSD: Base theme size: 1280x720
2011-12-24 15:07:14.398 OSD: Scaling factors: 1.5x1.5
2011-12-24 15:07:14.442 MythUIHelper, Error: LoadScaleImage(uparrow_alt.png)Unable to find image file
2011-12-24 15:07:14.447 MythUIHelper, Error: LoadScaleImage(downarrow_alt.png)Unable to find image file
2011-12-24 15:07:20.514 TV: OSDDialogEvent: result 3 text Schedule action DIALOG_MENU_SCHEDULE_0
2011-12-24 15:07:21.664 TV: OSDDialogEvent: result 0 text Program Guide action GUIDE
2011-12-24 15:07:21.714 pause_active: 0
2011-12-24 15:07:55.119 MythPainter: 11 images not yet de-allocated.
2011-12-24 15:07:55.462 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-12-24 15:07:55.463 Using protocol version 63
2011-12-24 15:07:56.035 ALSA, Error: snd_pcm_open("default"): No such file or directory
2011-12-24 15:07:56.049 VideoOutputXv: XVideo Adaptor Name: 'Radeon Textured Video'
2011-12-24 15:07:56.110 OSD: Base theme size: 1280x720
2011-12-24 15:07:56.110 OSD: Scaling factors: 0.5625x0.8
2011-12-24 15:07:56.154 OSD: Base theme size: 1280x720
2011-12-24 15:07:56.154 OSD: Scaling factors: 0.5625x0.8
2011-12-24 15:07:56.179 Player(2): Video timing method: DRM
2011-12-24 15:07:57.925 VideoOutputXv: XVideo Adaptor Name: 'Radeon Textured Video'
2011-12-24 15:07:57.958 OSD: Base theme size: 1280x720
2011-12-24 15:07:57.958 OSD: Scaling factors: 0.375x0.666667
2011-12-24 15:07:58.000 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-12-24 15:07:58.000 AFD: Opened codec 0xaa9dfba0, id(MPEG2VIDEO) type(Video)
2011-12-24 15:07:58.000 AFD: codec MP2 has 2 channels
2011-12-24 15:07:58.000 AFD: Opened codec 0xb22f3ae0, id(MP2) type(Audio)
2011-12-24 15:07:58.138 ALSA, Error: snd_pcm_open("default"): No such file or directory
2011-12-24 15:07:58.138 AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2011-12-24 15:07:58.139 ALSA, Error: snd_pcm_open("default"): No such file or directory
2011-12-24 15:07:58.139 AudioOutput Error: Aborting reconfigure
2011-12-24 15:07:58.139 AudioPlayer: Disabling Audio, reason is: Aborting reconfigure
2011-12-24 15:07:58.220 AFD: Resetting byte context eof (livetv 1 was eof 0)
2011-12-24 15:07:58.386 [mpeg2video @ 0x3ca5b40]warning: first frame is no keyframe
2011-12-24 15:07:58.389 [mpeg2video @ 0x3ca5b40]warning: first frame is no keyframe
2011-12-24 15:07:58.464 VideoOutput: Created YV12 OSD.
2011-12-24 15:08:06.578 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-12-24 15:08:18.777 BrowseDispInfo()
2011-12-24 15:08:18.777 BrowseStart()
2011-12-24 15:08:18.786 browsechanid: 1024 -> 1023
2011-12-24 15:08:24.843 BrowseEnd()
2011-12-24 15:08:25.610 OSD: Base theme size: 1280x720
2011-12-24 15:08:25.610 OSD: Scaling factors: 0.375x0.666667
2011-12-24 15:08:25.626 MythUIHelper, Error: LoadScaleImage(uparrow_alt.png)Unable to find image file
2011-12-24 15:08:25.630 MythUIHelper, Error: LoadScaleImage(downarrow_alt.png)Unable to find image file
2011-12-24 15:08:33.345 TV: OSDDialogEvent: result 4 text Schedule action DIALOG_MENU_SCHEDULE_0
2011-12-24 15:08:38.578 TV: OSDDialogEvent: result 0 text Program Guide action GUIDE
2011-12-24 15:08:38.611 pause_active: 0
2011-12-24 15:08:56.414 RingBuf(/var/lib/mythtv/livetv/1035_20111224150856.mpg) Warning: Not starting read ahead thread, already running
2011-12-24 15:08:57.730 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.730 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.731 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.731 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.731 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.731 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.732 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.732 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.732 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.732 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.733 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.733 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.733 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.733 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.734 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.741 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-12-24 15:08:57.742 AFD: Opened codec 0x9e5fd70, id(MPEG2VIDEO) type(Video)
2011-12-24 15:08:57.742 AFD: codec MP2 has 2 channels
2011-12-24 15:08:57.742 AFD: Opened codec 0x9f84470, id(MP2) type(Audio)
2011-12-24 15:08:57.881 ALSA, Error: snd_pcm_open("default"): No such file or directory
2011-12-24 15:08:57.881 AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2011-12-24 15:08:57.882 ALSA, Error: snd_pcm_open("default"): No such file or directory
2011-12-24 15:08:57.882 AudioOutput Error: Aborting reconfigure
2011-12-24 15:08:57.882 AudioPlayer: Disabling Audio, reason is: Aborting reconfigure
2011-12-24 15:08:57.890 AFD: Resetting byte context eof (livetv 1 was eof 0)
2011-12-24 15:08:57.964 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.964 AFD Error: Unknown decoding error
2011-12-24 15:08:57.965 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.965 AFD Error: Unknown decoding error
2011-12-24 15:08:57.966 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.966 AFD Error: Unknown decoding error
2011-12-24 15:08:57.966 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.966 AFD Error: Unknown decoding error
2011-12-24 15:08:57.966 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.966 AFD Error: Unknown decoding error
2011-12-24 15:08:57.966 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.967 AFD Error: Unknown decoding error
2011-12-24 15:08:57.967 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.967 AFD Error: Unknown decoding error
2011-12-24 15:08:57.967 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.967 AFD Error: Unknown decoding error
2011-12-24 15:08:57.967 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.967 AFD Error: Unknown decoding error
2011-12-24 15:08:57.967 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.967 AFD Error: Unknown decoding error
2011-12-24 15:08:57.967 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.967 AFD Error: Unknown decoding error
2011-12-24 15:08:57.967 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.967 AFD Error: Unknown decoding error
2011-12-24 15:08:57.967 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.968 AFD Error: Unknown decoding error
2011-12-24 15:08:57.968 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.968 AFD Error: Unknown decoding error
2011-12-24 15:08:57.968 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:08:57.968 AFD Error: Unknown decoding error
2011-12-24 15:08:57.970 [mpeg2video @ 0x3ca5b40]warning: first frame is no keyframe
2011-12-24 15:08:57.972 [mpeg2video @ 0x3ca5b40]warning: first frame is no keyframe
2011-12-24 15:09:21.258 BrowseDispInfo()
2011-12-24 15:09:21.258 BrowseStart()
2011-12-24 15:09:21.265 browsechanid: 1035 -> 1034
2011-12-24 15:09:22.841 BrowseDispInfo()
2011-12-24 15:09:22.841 BrowseStart()
2011-12-24 15:09:22.848 browsechanid: 1034 -> 1033
2011-12-24 15:09:24.107 BrowseDispInfo()
2011-12-24 15:09:24.108 BrowseStart()
2011-12-24 15:09:24.114 browsechanid: 1033 -> 1032
2011-12-24 15:09:25.207 BrowseDispInfo()
2011-12-24 15:09:25.207 BrowseStart()
2011-12-24 15:09:25.214 browsechanid: 1032 -> 1031
2011-12-24 15:09:26.124 BrowseDispInfo()
2011-12-24 15:09:26.124 BrowseStart()
2011-12-24 15:09:26.133 browsechanid: 1031 -> 1030
2011-12-24 15:09:26.858 BrowseEnd()
2011-12-24 15:09:28.342 RingBuf(/var/lib/mythtv/livetv/1030_20111224150928.mpg) Warning: Not starting read ahead thread, already running
2011-12-24 15:09:29.412 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.412 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.412 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.412 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.413 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.413 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.413 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.413 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.414 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.414 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.414 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.414 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.415 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.415 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.415 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.580 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-12-24 15:09:29.580 AFD: Opened codec 0x9f510e0, id(MPEG2VIDEO) type(Video)
2011-12-24 15:09:29.580 AFD: codec MP2 has 2 channels
2011-12-24 15:09:29.580 AFD: Opened codec 0x9f33620, id(MP2) type(Audio)
2011-12-24 15:09:29.804 ALSA, Error: snd_pcm_open("default"): No such file or directory
2011-12-24 15:09:29.804 AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2011-12-24 15:09:29.805 ALSA, Error: snd_pcm_open("default"): No such file or directory
2011-12-24 15:09:29.805 AudioOutput Error: Aborting reconfigure
2011-12-24 15:09:29.805 AudioPlayer: Disabling Audio, reason is: Aborting reconfigure
2011-12-24 15:09:29.814 AFD: Resetting byte context eof (livetv 1 was eof 0)
2011-12-24 15:09:29.892 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.892 AFD Error: Unknown decoding error
2011-12-24 15:09:29.892 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.893 AFD Error: Unknown decoding error
2011-12-24 15:09:29.893 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.893 AFD Error: Unknown decoding error
2011-12-24 15:09:29.893 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.893 AFD Error: Unknown decoding error
2011-12-24 15:09:29.893 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.893 AFD Error: Unknown decoding error
2011-12-24 15:09:29.893 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.893 AFD Error: Unknown decoding error
2011-12-24 15:09:29.893 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.893 AFD Error: Unknown decoding error
2011-12-24 15:09:29.893 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.893 AFD Error: Unknown decoding error
2011-12-24 15:09:29.893 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.894 AFD Error: Unknown decoding error
2011-12-24 15:09:29.894 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.894 AFD Error: Unknown decoding error
2011-12-24 15:09:29.894 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.894 AFD Error: Unknown decoding error
2011-12-24 15:09:29.894 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.894 AFD Error: Unknown decoding error
2011-12-24 15:09:29.894 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.894 AFD Error: Unknown decoding error
2011-12-24 15:09:29.894 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.894 AFD Error: Unknown decoding error
2011-12-24 15:09:29.894 [mpeg2video @ 0x3ca5b40]mpeg_decode_postinit() failure
2011-12-24 15:09:29.894 AFD Error: Unknown decoding error
2011-12-24 15:09:29.897 [mpeg2video @ 0x3ca5b40]warning: first frame is no keyframe
2011-12-24 15:09:29.900 [mpeg2video @ 0x3ca5b40]warning: first frame is no keyframe
2011-12-24 15:09:29.994 Player(2): Waited 100ms for video buffers AUAAAAAUAAUAUAAUAAAAAAAAAAuAAAL
2011-12-24 15:09:33.424 BrowseDispInfo()
2011-12-24 15:09:33.424 BrowseStart()
2011-12-24 15:09:33.431 browsechanid: 1030 -> 1029
2011-12-24 15:09:34.590 BrowseDispInfo()
2011-12-24 15:09:34.590 BrowseStart()
2011-12-24 15:09:34.597 browsechanid: 1029 -> 1028
2011-12-24 15:09:35.324 BrowseDispInfo()
2011-12-24 15:09:35.324 BrowseStart()
2011-12-24 15:09:35.330 browsechanid: 1028 -> 1027
2011-12-24 15:09:37.857 BrowseEnd()
2011-12-24 15:09:38.049 [mpeg2video @ 0x3ca5b40]ac-tex damaged at 1 27
2011-12-24 15:09:38.049 [mpeg2video @ 0x3ca5b40]ac-tex damaged at 26 25
2011-12-24 15:09:38.050 [mpeg2video @ 0x3ca5b40]Warning MVs not available
2011-12-24 15:09:39.319 RingBuf(/var/lib/mythtv/livetv/1027_20111224150939.mpg) Warning: Not starting read ahead thread, already running
2011-12-24 15:09:39.838 [mpeg2video @ 0x3ca5b40]Warning MVs not available
2011-12-24 15:09:40.502 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-12-24 15:09:40.502 AFD: Opened codec 0x9faac40, id(MPEG2VIDEO) type(Video)
2011-12-24 15:09:40.502 AFD: codec MP2 has 2 channels
2011-12-24 15:09:40.502 AFD: Opened codec 0x9df63d0, id(MP2) type(Audio)
2011-12-24 15:09:40.812 ALSA, Error: snd_pcm_open("default"): No such file or directory
2011-12-24 15:09:40.812 AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2011-12-24 15:09:40.813 ALSA, Error: snd_pcm_open("default"): No such file or directory
2011-12-24 15:09:40.813 AudioOutput Error: Aborting reconfigure
2011-12-24 15:09:40.813 AudioPlayer: Disabling Audio, reason is: Aborting reconfigure
2011-12-24 15:09:40.859 AFD: Resetting byte context eof (livetv 1 was eof 0)
2011-12-24 15:09:40.984 [mpeg2video @ 0x3ca5b40]Warning MVs not available
2011-12-24 15:09:40.986 [mpeg2video @ 0x3ca5b40]warning: first frame is no keyframe
2011-12-24 15:09:40.988 [mpeg2video @ 0x3ca5b40]warning: first frame is no keyframe
2011-12-24 15:09:42.907 BrowseDispInfo()
2011-12-24 15:09:42.907 BrowseStart()
2011-12-24 15:09:42.916 browsechanid: 1027 -> 1026
2011-12-24 15:09:43.540 BrowseDispInfo()
2011-12-24 15:09:43.540 BrowseStart()
2011-12-24 15:09:43.547 browsechanid: 1026 -> 1025
2011-12-24 15:09:43.873 BrowseDispInfo()
2011-12-24 15:09:43.873 BrowseStart()
2011-12-24 15:09:43.883 browsechanid: 1025 -> 1024
2011-12-24 15:09:44.307 BrowseDispInfo()
2011-12-24 15:09:44.307 BrowseStart()
2011-12-24 15:09:44.316 browsechanid: 1024 -> 1023
2011-12-24 15:09:46.306 BrowseEnd()
2011-12-24 15:09:57.471 RingBuf(/var/lib/mythtv/livetv/1023_20111224150947.mpg) Error: OpenFile(): File too small (0B).
2011-12-24 15:09:57.471 Player(2), Error: JumpToProgram's OpenFile failed (card type: MPEG).
2011-12-24 15:09:57.471 
LiveTVChain has 11 entries
     DVB: 2675 (15:06:31 to 15:07:55) discontinuous
   DUMMY: 1024 (15:07:55 to 15:07:56) discontinuous
    MPEG: 1024 (15:07:56 to 15:08:55) discontinuous
   DUMMY: 1035 (15:08:55 to 15:08:55) discontinuous
    MPEG: 1035 (15:08:56 to 15:09:27) discontinuous
   DUMMY: 1030 (15:09:27 to 15:09:27) discontinuous
    MPEG: 1030 (15:09:28 to 15:09:38) discontinuous
   DUMMY: 1027 (15:09:38 to 15:09:38) discontinuous
    MPEG: 1027 (15:09:39 to 15:09:46) discontinuous
   DUMMY: 1023 (15:09:46 to 15:09:47) discontinuous
*   MPEG: 1023 (15:09:47 to 15:30:00) discontinuous

2011-12-24 15:09:57.471 Player(2), Error: Unknown recorder error, exiting decoder
2011-12-24 15:09:57.527 TV: Attempting to change from WatchingLiveTV to None
2011-12-24 15:09:57.535 MythPainter: 10 images not yet de-allocated.
2011-12-24 15:10:04.536 MythSocket(ffffffffaa9b0398:40): readStringList: Error, timed out after 7000 ms.
2011-12-24 15:10:04.537 RemoteEncoder::SendReceiveStringList(): No response.
2011-12-24 15:10:04.537 TV: Changing from WatchingLiveTV to None
2011-12-24 15:10:04.537 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-12-24 15:10:04.538 Using protocol version 63
2011-12-24 15:10:04.689 TV: Attempting to change from None to WatchingLiveTV
2011-12-24 15:10:04.689 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-12-24 15:10:04.690 Using protocol version 63
2011-12-24 15:10:04.799 Spawning LiveTV Recorder -- begin
2011-12-24 15:10:11.801 MythSocket(9e17700:30): readStringList: Error, timed out after 7000 ms.
2011-12-24 15:10:11.802 RemoteEncoder::SendReceiveStringList(): No response.
2011-12-24 15:10:11.802 Spawning LiveTV Recorder -- end
2011-12-24 15:10:11.802 GetEntryAt(-1) failed.
2011-12-24 15:10:11.802 It appears that your backend may be misconfigured.  Check your backend logs to determine whether your capture cards, lineups, channels, or storage configuration are reporting errors.  This issue is commonly caused by failing to complete all setup steps properly.  You may wish to review the documentation for mythtv-setup.
2011-12-24 15:10:11.803 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
2011-12-24 15:10:11.803 TV Error: HandleStateChange(): LiveTV not successfully started
2011-12-24 15:10:11.803 We have a RingBuffer
2011-12-24 15:10:11.803 TV Error: Invalid Remote Encoder
2011-12-24 15:10:11.803 TV Error: LiveTV not successfully started
2011-12-24 15:10:49.249 Deleting UPnP client...
Error in my_thread_global_end(): 2 threads didn't exit

My apologies for such a long post.:shock:  Pay no attention to the ALSA errors, as I have not sound card in this system.  I intend to use it as a backend server ONLY at some point.  

I am hopeful that you or someone can help me make sense of what is happening and suggest a course of action.  It is really great to see how much one stranger is willing to help another.  I hope to be able to contribute as much back to this forum as you have to me with your suggestions.

Thank you!

---

### Post by klc5555 on 2011-12-24
Your analog devices will be correctly set up on the single-digit /dev/videoX numbers. Your pvr 150s will be set up as MPEG2 encoders. Your pchdtv-hd5500 will be set up as a V4l analog. I don't know what the analog side of a ATi HDTV Wonder is set up as --it's not a device I've ever used.

Now forget about trying to do an analog scan. Stay in your backend setup. You must have set up a separate Video Source in Video Sources just to handle analog. In Input Connections you must have bound this analog Video Source to each of your analog tuner inputs if you were intending to try to scan with them. 

So now in your Channel Editor in the backend setup try to manually add a channel to this analog Video Source, as described in two or three previous posts. Exit the backend setup, start the backend, start the frontend, and see whether you can start the one single channel you have added in LiveTV. If this one channel is tunable, you be able to add the remainder of your analog channels the same way in the backend setup in the Channel Editor.

---

### Post by jlp_engineer on 2011-12-24
> **klc5555 said:**
> Your analog devices will be correctly set up on the single-digit /dev/videoX numbers. Your pvr 150s will be set up as MPEG2 encoders. Your pchdtv-hd5500 will be set up as a V4l analog. I don't know what the analog side of a ATi HDTV Wonder is set up as --it's not a device I've ever used.

It is a V4L device, but I do not plan on using it, as it does not have built-in MPEG encoder, and therefore would be a drain on my limited CPU resources (P4 3.2GHz).  I may use the analog tuner on the HD-5500 as a backup if all the PVR-150's are busy, but if the analog tuner on the ATi or the pcHDTV card does not work, it would be of little consequence...unless I cannot get the PVR-150's to work.

> **klc5555 said:**
> Now forget about trying to do an analog scan. Stay in your backend setup. You must have set up a separate Video Source in Video Sources just to handle analog. In Input Connections you must have bound this analog Video Source to each of your analog tuner inputs if you were intending to try to scan with them. 

Yes, I have separate sources defined for analog and digital.  I have bound the analog source to the analog tuners, and the digital source to the digital tuners.  My analog source on SD has channels 2 - 83 listed, and my digital source has channels 305 - 846, of which I have only about a dozen active, as I believe the rest are encrypted.

> **klc5555 said:**
> So now in your Channel Editor in the backend setup try to manually add a channel to this analog Video Source, as described in two or three previous posts. Exit the backend setup, start the backend, start the frontend, and see whether you can start the one single channel you have added in LiveTV. If this one channel is tunable, you be able to add the remainder of your analog channels the same way in the backend setup in the Channel Editor.

I did as you suggested, and added three channels, 2, 42, and 83.  Channel 2 is our local Fox affiliate, 42 is SciFi, and 83 is the TVGuide channel.  I added them as 4A, 4B, and 4C, and set the video source as analog for each.  I put the channel number in the second page, and then set all the sliders for the video settings at their mid-range setting.  They were all slid to the extreme left, with the exception of the fine tuning slider.  Where should these all be set?  How do you know if the fine tuning slider should be changed?

Saved them all and went to the front-end.  One of the analog channels was up as default (probably from a previous attempt), but the video was choppy and distorted (but a big step up from "snow").  I switched to a different tuner, and voila...I had video!  I tried the channels I added, and each was perfect.  I tried the same channels on the other analog tuner, and got choppy video again, but it eventually settled down and gave me a good image.  However, when I tried one of the channels that I added manually, I got a blank screen and got some error about it dropping the video frames too many times.  I tried again, and got the "Error opening jump program file buffer".  Also, one of my tuners seems to be MIA.  I will go back through the setup, delete all the capture cards, and add them back in.

Does this mean I have a bad tuner, or is my setup still suspect?  I can post any logs you wish to see.  Thank you for your patience.

---

### Post by klc5555 on 2011-12-25
The sliders will set themselves in this context. So no need to worry over them. 

Since all analog tuners will be using the same analog Video Source with the same analog channel information, to add/configure channels pick the tuner that works best and go with it. That way you'll be limiting yourself to only one set of problems at a time. MIA tuner(s) can be dealt with separately. Add as many analog channels as you care to. If you prefer, name, callsign, the number you add them as (if you don't like 4A, 4B, and 4C), and xmltvid can all be added/edited later from the frontend for each channel from livetv.

The mythtv wiki page for the antique PVR 150 card is here: [http://www.mythtv.org/wiki/Hauppauge_PVR-150](http://www.mythtv.org/wiki/Hauppauge_PVR-150)  The PVR 150 cards can be a bit persicketty about which PCI slots they sit in. The 5500 is not so much. The main problem with using 4 different analog tuners in a board with 4 separate PCI slots is that on every reboot linux/mythtv is likely going to get confused about which /dev/videoX goes with which tuner and scramble them. Mythtv will try to open one of the ivtv PVR 150s as an analog 5500, or the reverse, and of course the card won't be able to be opened. Loading the cards to the same /dev/videoX device nodes consistently at boot will be done either with setting up udev rules for the cards, or by loading the differing card drivers with correct params set in a .conf file added under /etc/modprobe.d  It frequently takes a bit of tinkering to get the /dev/videoX load to be consistent. And, each device the system finds will be assigned a /dev/videoX number when the driver loads at boot, whether you intend to configure the device  or not.

Mythtv's wikipage for udev is here: [http://www.mythtv.org/wiki/Device_Filenames_and_udev](http://www.mythtv.org/wiki/Device_Filenames_and_udev) There are also numerous threads to be consulted in this forum where other users have set up udev rules for tuner cards.

Using modprobe params make driver load consistent is older and less talked about. For example, a PVR 150 will on one boot load at video0, bigfooting the other cards, but next time they may load up at video2 and video3. Setting up, say, cardinfo.conf under /etc/modprobe.d  with the line in it:
```
options ivtv ivtv_first_minor=2
``` will keep the PVR150s loading at /dev/video2 and later, while the 5500 and the other card fight it out for /dev/video0 and /dev/video1 Perhaps one less thing to configure.

---

### Post by nickrout on 2011-12-29
> **jlp_engineer said:**
> 

Also, when I am configuring the tuners, I get many different video devices, and it is difficult to determine if I am selecting the right ones.  In the Capture Card setup, when I select IVTV MPEG-2 encoder card, /dev/video0, /dev/video1, /dev/video4, as well as video24, video25, video28, video32, video33, and video36.  They all show up as "Hauppauge WinTV PVR-150" cards.  Under the Analog V4L selection, I also get /dev/video2 and /dev/video3 for the analog sides of the ATi HDTV Wonder and the pcHDTV HD5500 cards.  I have been using the single digit numbers for the tuner configurations.  Is this correct?  What are the double digit video devices for?

For the record, the device nodes are documented here:

[http://www.mythtv.org/wiki/Hauppauge_PVR-500#Check_video_devices](http://www.mythtv.org/wiki/Hauppauge_PVR-500#Check_video_devices)

The only one you need to bother with is the single digit device number.

---

### Post by jlp_engineer on 2011-12-29
> **klc5555 said:**
> Since all analog tuners will be using the same analog Video Source with the same analog channel information, to add/configure channels pick the tuner that works best and go with it. That way you'll be limiting yourself to only one set of problems at a time. MIA tuner(s) can be dealt with separately. Add as many analog channels as you care to. If you prefer, name, callsign, the number you add them as (if you don't like 4A, 4B, and 4C), and xmltvid can all be added/edited later from the frontend for each channel from livetv.

OK, I took the three PVR-150's that I have, and placed them alone in one system. I should explain that this system is an 875 based P4 board that happens to have five PCI slots in it.  I had it loaded with these same three tuners running Mythbuntu 8.10 for years with absolutely no issues.  I loaded a fresh copy of Mythbuntu 11.04 on this system (to avoid any prior config issues), and configured the three tuners, video0, video1, and video2, and loaded only the analog channels for the listings/video_source.  When I brought up the frontend, I could tune 2 - 13 on all the tuners, but nothing above that.  I then found a few areas in the general backend setup where the frequency tables were mentioned, and changed them to us-cable, and then all the channels worked without a problem.  

So, if I use the channel editor, and leave the pre-populated information that resulted from a failed analog channel scan (I know I don't have to, but I am lazy :)), then all I need to do is delete the channels that do not exist for me.  Then after I am done, allow mythfilldatabase to run and load all the guide data - right?  How does the guide data match up with what is in the channel editor?  Is this the XMLTV ID or the channel number?  If it is by XMLTV ID, then why is this blank in the channel editor?

> **klc5555 said:**
> The mythtv wiki page for the antique PVR 150 card is here: [http://www.mythtv.org/wiki/Hauppauge_PVR-150](http://www.mythtv.org/wiki/Hauppauge_PVR-150)  The PVR 150 cards can be a bit persicketty about which PCI slots they sit in. The 5500 is not so much. The main problem with using 4 different analog tuners in a board with 4 separate PCI slots is that on every reboot linux/mythtv is likely going to get confused about which /dev/videoX goes with which tuner and scramble them. Mythtv will try to open one of the ivtv PVR 150s as an analog 5500, or the reverse, and of course the card won't be able to be opened. Loading the cards to the same /dev/videoX device nodes consistently at boot will be done either with setting up udev rules for the cards, or by loading the differing card drivers with correct params set in a .conf file added under /etc/modprobe.d  It frequently takes a bit of tinkering to get the /dev/videoX load to be consistent. And, each device the system finds will be assigned a /dev/videoX number when the driver loads at boot, whether you intend to configure the device  or not.

I know the PVR-150's are antiques, but then, strictly speaking, so am I. :lolflag: But seriously, they are one of only a few analog tuners that seem to be well supported in Linux that have on board MPEG2 encoders, which work nicely with my underpowered system.  The only problem I would have moving up to a more powerful server, is that on most boards, you lose multiple PCI slots in favor of PCIe.  Besides, I got the 875 based board and case for a little over 100 bucks 4 years ago, so I think I did alright.  On a possibly related note, prior to the frequency table change I mentioned above, I would often get the error "Video frame buffering failed too many times" and get bumped back out to the main menu.  Do you think that the cable frequency table change may have resolved that issue, or do you think it is due to the latency issues on the PVR-150's and that I might still see it again?

> **klc5555 said:**
> Mythtv's wikipage for udev is here: [http://www.mythtv.org/wiki/Device_Filenames_and_udev](http://www.mythtv.org/wiki/Device_Filenames_and_udev) There are also numerous threads to be consulted in this forum where other users have set up udev rules for tuner cards.

Since the PVR-150's seem to be happy when they are by themselves, I will most likely keep them that way.  I will then try the three digital tuners in a slave (or primary and put the other as slave) backend and see if they can co-exist with each other.  What do you think?

> **klc5555 said:**
> Using modprobe params make driver load consistent is older and less talked about. For example, a PVR 150 will on one boot load at video0, bigfooting the other cards, but next time they may load up at video2 and video3. Setting up, say, cardinfo.conf under /etc/modprobe.d  with the line in it:

```
options ivtv ivtv_first_minor=2
``` 

will keep the PVR150s loading at /dev/video2 and later, while the 5500 and the other card fight it out for /dev/video0 and /dev/video1 Perhaps one less thing to configure.

I have learned a lot about udev and modprobe, and will use these options if I continue to experience weird device ordering issues.  My problem is not using these options, it is not knowing that they existed in the first place.  I come from a DOS world, so text files and command lines do not concern me, like they might some others.  I am fortunate that I have two individuals (yourself and nickrout) that take an interest in my problems, let alone give me advice that will actually help me fix it.  

Many thanks!  =D>

---

### Post by jlp_engineer on 2011-12-29
> **nickrout said:**
> For the record, the device nodes are documented here:

[http://www.mythtv.org/wiki/Hauppauge_PVR-500#Check_video_devices](http://www.mythtv.org/wiki/Hauppauge_PVR-500#Check_video_devices)

The only one you need to bother with is the single digit device number.

I appreciate the information.  It seems that the documentation is always out there, but finding it is usually the only challenge.  I must make more of an effort in the future.

I know that I have already asked this in another post, but what is your opinion of isolating the analog and digital tuners in their own backends, and then just let the frontends grab the appropriate tuner when a channel is selected?  I believe I have enough hardware right now to do a proof of concept, but if you have any recommendations, I would really appreciate them.

Thank you.

---

### Post by nickrout on 2011-12-29
If the PVR-150s are working OK in their own box, and you have a spare box to allocate to the other tuners, then that is certainly a way of doing it. I have never used a slave backend, but I believe it is no more rocket science than the rest of mythtv :)

---

### Post by klc5555 on 2011-12-30
> How does the guide data match up with what is in the channel editor? Is this the XMLTV ID or the channel number? If it is by XMLTV ID, then why is this blank in the channel editor?

For your Schedules Direct guide data, the xmltvid is the critical datum to match up the online schedule with mythtv's scheduler. In theory Myth ought to pull it in automatically at some point. In reality, this number almost always has to be added manually. If you "preview" your schedule online in Schedules Direct as though you were about to add your schedule again, the channels and their xmltvids will all display; you can print out the table and go to work. You can add the ids as a batch one after another in Channel Editor. Or pull up a channel in LiveTV, type "e" and add the name, callsign, and xmltvid number for that channel in the popup channel edit menu, which I find drives me less crazy. Thereafter, the scheduling information will fill in beginning the midnight after mythfilldatabase next runs (unless you run it yourself with the switch "mythfilldatabase --refresh-today", in which case the schedule data fills in for the current day).

Note that channel callsign is the critical datum that mythtv uses to keep channels with identical content separate when assigning tuners for recording, so if you have a station on your cable in both analog and digital formats (or multiple digital formats), the callsign you edit in for each version needs to be unique. WTTW vs. WTTW-DT vs. WTTW-HD, for example.

For my day-to-day watching/recording, at the moment I use three dedicated backends: a master and two slaves, which are connected to by a variety of wired and wireless remote frontends. Only one of these backends is Ubuntu at the moment, because it tends to be slower, more resource-intensive, and harder to maintain than my preferred Slackware. I tended to find that multiple stream read/writes (particularly HD, which moves 6 Gigs an hour) was my major source of degraded recordings, so I got into the habit of setting no more than two or at most three tuners per box, with each machine having a separate OS drive and a number of recording drives that at least equals the number of streams I'd expect to record simultaneously on that machine (since myth is good about assigning simultaneous streams to separate drives where possible).  I'm not sure I'd want four tuners on a single machine, so I think your idea of divvying up your collection of tuners across a couple of backends is a good idea.

---

### Post by nickrout on 2011-12-30
I find the easiest place to edit xmltvid is in mythweb (settings button| TV |Channel Info tab

---

### Post by jlp_engineer on 2012-01-01
Well...

I am happy to report some progress.  I now have three digital tuners (one pcHDTV HD-5500, and two ATi HDTV Wonders) in an 875 based P4 3.4GHz system, that has Mythbuntu 11.04 running on it, which is serving as my master backend.  I have a second, nearly identical system (3.2GHz CPU instead of a 3.4GHz CPU) with the 3 PVR-150's, configured as a slave backend.  

I ran updates and upgraded MythTV to v0.24.1.  I confirmed that the digital tuners on the master backend are working and switch from one to the other without issues.  However, when I brought up the slave backend, and began to use the PVR-150's, I noticed some strange things happening.  What happened was that the first analog tuner would tune the default channel, which happened to be "2", and that worked for each tuner when I switched between them.  However, when I changed channels on any analog tuner on the slave backend, from either front end I was using, I would get a black screen, and the front end would become slightly unresponsive.  I did not see any errors displayed, and have not checked the logs, but is this an issue that is common with these older analog tuners?  Sometimes I would get a picture, but the there was digital artifacts, distortion, and some stuttering.  

My initial thoughts, are that perhaps Mythbuntu has advanced to the point where supporting the old analog tuners is not as solid as it once was, and I am beginning to see the results of this.  As version 8.10 was running just fine, for many years, this is the only conclusion I can come to, as nothing else has changed (same system, same hardware, etc.), only the software running on it.  Are others running MPEG II analog cards under Mythbuntu without issues?

Things I am going to try next...

1 - Remove one of the PVR-150's from the slave backend, and see if the behavior of the cards improves.

2 - Reconfigure the system as a stand alone backend, and see if that changes anything.

3 - Play with the PVR-150 card PCI latency settings and see what that does.

Does anyone have any other ideas that I am missing?  Should I post the logs from the slave backend where the analog tuners are located?  I don't want to post them unless it is needed, since doing so usually makes for a R-E-A-L-L-Y long post.  Is there a way to post the logs so someone can scroll through it in a window inside the post without it making a really long message?

Thanks to all for any help you can provide.

---

### Post by nickrout on 2012-01-01
> **jlp_engineer said:**
> Well...

I am happy to report some progress.  I now have three digital tuners (one pcHDTV HD-5500, and two ATi HDTV Wonders) in an 875 based P4 3.4GHz system, that has Mythbuntu 11.04 running on it, which is serving as my master backend.  I have a second, nearly identical system (3.2GHz CPU instead of a 3.4GHz CPU) with the 3 PVR-150's, configured as a slave backend.  

I ran updates and upgraded MythTV to v0.24.1.  I confirmed that the digital tuners on the master backend are working and switch from one to the other without issues.  However, when I brought up the slave backend, and began to use the PVR-150's, I noticed some strange things happening.  What happened was that the first analog tuner would tune the default channel, which happened to be "2", and that worked for each tuner when I switched between them.  However, when I changed channels on any analog tuner on the slave backend, from either front end I was using, I would get a black screen, and the front end would become slightly unresponsive.  I did not see any errors displayed, and have not checked the logs, but is this an issue that is common with these older analog tuners?  Sometimes I would get a picture, but the there was digital artifacts, distortion, and some stuttering.  

My initial thoughts, are that perhaps Mythbuntu has advanced to the point where supporting the old analog tuners is not as solid as it once was, and I am beginning to see the results of this.  As version 8.10 was running just fine, for many years, this is the only conclusion I can come to, as nothing else has changed (same system, same hardware, etc.), only the software running on it.  Are others running MPEG II analog cards under Mythbuntu without issues?

Things I am going to try next...

1 - Remove one of the PVR-150's from the slave backend, and see if the behavior of the cards improves.

2 - Reconfigure the system as a stand alone backend, and see if that changes anything.

3 - Play with the PVR-150 card PCI latency settings and see what that does.

Does anyone have any other ideas that I am missing?  Should I post the logs from the slave backend where the analog tuners are located?  I don't want to post them unless it is needed, since doing so usually makes for a R-E-A-L-L-Y long post.  Is there a way to post the logs so someone can scroll through it in a window inside the post without it making a really long message?

Thanks to all for any help you can provide.

post to pastebin is best.

---

### Post by klc5555 on 2012-01-01
At this point, you can't tell much of anything without logs. "tail"-ing the mythbackend.log after a failed retune of a pvr 150 will give you about the last 6 lines of information. 

There have been an awful lot of changes to the ivtv driver/firmware since '08. I haven't kept track of these since I used my pvr150 for trebuchet fodder back in mid '09. You may need to troubleshoot your pvr150 array according to here: [http://ivtvdriver.org/index.php/Troubleshooting](http://ivtvdriver.org/index.php/Troubleshooting) and then ask, if necessary, on the ivtv forums. 

This probably makes you wish you'd kept the older software running on the older hardware. Sometimes 6-month upgrade cycles and blink-of-an-eye support lifetimes are not good for the end users, since they don't correspond with any normal cycle of hardware use. It's worse when the older versions of software are broomed from the internet. Does Mythbuntu 10.04 (with mythtv 0.23) run on your hardware? It's still patched and supported, and if all else fails you may find it a more compatible match for your hardware than 11.x (or beyond)

Although they are MPEG2 encoders, the old PVR150s have fairly inferior picture quality even when tweaked up to their limit. Some software cards like the analog half of the pchdtv-hd5500 produce a superior output than the pvr 150 even with the increased cpu overhead. And the overhead is not bad when the 5500 is allowed to output its default RTJPEG, rather than being shifted over to MPEG. So you may wish to have the analog half of your 5500 share in the analog recording duties.

Current MPEG2 hardware encoders like the analog half of the Hauppauge 1600 also offer picture quality that is superior to the old pvr 150s, though they have a few of their own quirks with the cx18 driver that was developed from the ivtv one.

If the slave backend improves when the pvr150 in the third slot is removed, you might consider making it just a 1 for 1 swap with the 5500 from the other backend, since the 5500 is not sensitive as to which slot it's located in. I don't know whether the HDTV-Wonders are persnicketty about their pci slot or not.

---

### Post by jlp_engineer on 2012-01-02
> **klc5555 said:**
> At this point, you can't tell much of anything without logs. "tail"-ing the mythbackend.log after a failed retune of a pvr 150 will give you about the last 6 lines of information. 

Frontend Log:

```
 2012-01-02 12:58:32.711 LiveTVChain(live-MYTHBE2-2012-01-02T12:56:36): SwitchTo() not switching to current
2012-01-02 12:58:32.768 VideoOutput: Created YV12 OSD.
2012-01-02 12:58:34.540 VideoOutputXv: XVideo Adaptor Name: 'NV40 texture adapter'
2012-01-02 12:58:34.570 OSD: Base theme size: 1280x720
2012-01-02 12:58:34.571 OSD: Scaling factors: 0.375x0.666667
2012-01-02 12:58:34.636 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2012-01-02 12:58:34.636 AFD: Opened codec 0x8ee37c0, id(MPEG2VIDEO) type(Video)
2012-01-02 12:58:34.636 AFD: codec MP2 has 2 channels
2012-01-02 12:58:34.636 AFD: Opened codec 0x8ebbc00, id(MP2) type(Audio)
2012-01-02 12:58:34.793 AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2012-01-02 12:58:34.796 ALSA, Error: Setting hardware audio buffer size to 128
2012-01-02 12:58:34.796 ALSA, Error: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
2012-01-02 12:58:34.796 ALSA, Error: Try to manually increase audio buffer with: echo 128 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
2012-01-02 12:58:34.796 ALSA, Error: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
2012-01-02 12:58:34.800 AudioPlayer: Enabling Audio
2012-01-02 12:58:34.811 AFD: Resetting byte context eof (livetv 1 was eof 0)
2012-01-02 12:58:34.839 [mpeg2video @ 0x5341b40]warning: first frame is no keyframe
2012-01-02 12:58:34.842 [mpeg2video @ 0x5341b40]warning: first frame is no keyframe
2012-01-02 12:58:34.920 OSD: Base theme size: 1280x720
2012-01-02 12:58:34.920 OSD: Scaling factors: 0.280469x0.5
2012-01-02 12:58:35.000 VideoOutput: Created YV12 OSD.
2012-01-02 12:58:57.450 OSD: Base theme size: 1280x720
2012-01-02 12:58:57.450 OSD: Scaling factors: 0.280469x0.5
2012-01-02 12:59:00.264 TV: OSDDialogEvent: result 2 text Schedule action DIALOG_MENU_SCHEDULE_0
2012-01-02 12:59:00.897 TV: OSDDialogEvent: result 0 text Program Guide action GUIDE
2012-01-02 12:59:00.930 pause_active: 0
2012-01-02 12:59:07.079 RingBuf(/var/lib/mythtv/recordings/2009_20120102125907.mpg) Warning: Not starting read ahead thread, already running
2012-01-02 12:59:08.274 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.274 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.275 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.275 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.275 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.276 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.276 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.276 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.276 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.277 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.277 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.277 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.278 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.278 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.287 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2012-01-02 12:59:08.287 AFD: Opened codec 0xaed8ea90, id(MPEG2VIDEO) type(Video)
2012-01-02 12:59:08.287 AFD: codec MP2 has 2 channels
2012-01-02 12:59:08.287 AFD: Opened codec 0xaedbfa00, id(MP2) type(Audio)
2012-01-02 12:59:08.380 AFD: Resetting byte context eof (livetv 1 was eof 0)
2012-01-02 12:59:08.544 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.544 AFD Error: Unknown decoding error
2012-01-02 12:59:08.544 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.544 AFD Error: Unknown decoding error
2012-01-02 12:59:08.545 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.545 AFD Error: Unknown decoding error
2012-01-02 12:59:08.545 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.545 AFD Error: Unknown decoding error
2012-01-02 12:59:08.545 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.545 AFD Error: Unknown decoding error
2012-01-02 12:59:08.545 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.545 AFD Error: Unknown decoding error
2012-01-02 12:59:08.545 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.546 AFD Error: Unknown decoding error
2012-01-02 12:59:08.546 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.546 AFD Error: Unknown decoding error
2012-01-02 12:59:08.546 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.546 AFD Error: Unknown decoding error
2012-01-02 12:59:08.546 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.546 AFD Error: Unknown decoding error
2012-01-02 12:59:08.546 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.546 AFD Error: Unknown decoding error
2012-01-02 12:59:08.546 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.547 AFD Error: Unknown decoding error
2012-01-02 12:59:08.547 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.547 AFD Error: Unknown decoding error
2012-01-02 12:59:08.547 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:08.547 AFD Error: Unknown decoding error
2012-01-02 12:59:08.549 [mpeg2video @ 0x5341b40]warning: first frame is no keyframe
2012-01-02 12:59:08.552 [mpeg2video @ 0x5341b40]warning: first frame is no keyframe
2012-01-02 12:59:35.785 BrowseDispInfo()
2012-01-02 12:59:35.785 BrowseStart()
2012-01-02 12:59:35.792 browsechanid: 2009 -> 2008
2012-01-02 12:59:37.117 BrowseDispInfo()
2012-01-02 12:59:37.117 BrowseStart()
2012-01-02 12:59:37.124 browsechanid: 2008 -> 2009
2012-01-02 12:59:38.116 BrowseDispInfo()
2012-01-02 12:59:38.116 BrowseStart()
2012-01-02 12:59:38.123 browsechanid: 2009 -> 2008
2012-01-02 12:59:38.749 BrowseDispInfo()
2012-01-02 12:59:38.749 BrowseStart()
2012-01-02 12:59:38.756 browsechanid: 2008 -> 2007
2012-01-02 12:59:39.548 BrowseDispInfo()
2012-01-02 12:59:39.549 BrowseStart()
2012-01-02 12:59:39.555 browsechanid: 2007 -> 2008
2012-01-02 12:59:40.148 BrowseDispInfo()
2012-01-02 12:59:40.148 BrowseStart()
2012-01-02 12:59:40.154 browsechanid: 2008 -> 2009
2012-01-02 12:59:41.647 BrowseDispInfo()
2012-01-02 12:59:41.647 BrowseStart()
2012-01-02 12:59:41.655 browsechanid: 2009 -> 2010
2012-01-02 12:59:42.146 BrowseDispInfo()
2012-01-02 12:59:42.146 BrowseStart()
2012-01-02 12:59:42.153 browsechanid: 2010 -> 2011
2012-01-02 12:59:42.613 BrowseDispInfo()
2012-01-02 12:59:42.613 BrowseStart()
2012-01-02 12:59:42.619 browsechanid: 2011 -> 2012
2012-01-02 12:59:43.112 BrowseDispInfo()
2012-01-02 12:59:43.112 BrowseStart()
2012-01-02 12:59:43.119 browsechanid: 2012 -> 2013
2012-01-02 12:59:43.678 BrowseDispInfo()
2012-01-02 12:59:43.678 BrowseStart()
2012-01-02 12:59:43.685 browsechanid: 2013 -> 2014
2012-01-02 12:59:44.111 BrowseDispInfo()
2012-01-02 12:59:44.111 BrowseStart()
2012-01-02 12:59:44.118 browsechanid: 2014 -> 2015
2012-01-02 12:59:44.611 BrowseDispInfo()
2012-01-02 12:59:44.611 BrowseStart()
2012-01-02 12:59:44.617 browsechanid: 2015 -> 2016
2012-01-02 12:59:45.111 BrowseDispInfo()
2012-01-02 12:59:45.111 BrowseStart()
2012-01-02 12:59:45.117 browsechanid: 2016 -> 2017
2012-01-02 12:59:45.543 BrowseDispInfo()
2012-01-02 12:59:45.544 BrowseStart()
2012-01-02 12:59:45.550 browsechanid: 2017 -> 2018
2012-01-02 12:59:46.010 BrowseDispInfo()
2012-01-02 12:59:46.010 BrowseStart()
2012-01-02 12:59:46.017 browsechanid: 2018 -> 2019
2012-01-02 12:59:46.476 BrowseDispInfo()
2012-01-02 12:59:46.476 BrowseStart()
2012-01-02 12:59:46.483 browsechanid: 2019 -> 2020
2012-01-02 12:59:46.909 BrowseDispInfo()
2012-01-02 12:59:46.909 BrowseStart()
2012-01-02 12:59:46.916 browsechanid: 2020 -> 2021
2012-01-02 12:59:47.342 BrowseDispInfo()
2012-01-02 12:59:47.342 BrowseStart()
2012-01-02 12:59:47.349 browsechanid: 2021 -> 2022
2012-01-02 12:59:47.708 BrowseDispInfo()
2012-01-02 12:59:47.709 BrowseStart()
2012-01-02 12:59:47.715 browsechanid: 2022 -> 2023
2012-01-02 12:59:48.308 BrowseDispInfo()
2012-01-02 12:59:48.308 BrowseStart()
2012-01-02 12:59:48.315 browsechanid: 2023 -> 2024
2012-01-02 12:59:51.605 BrowseEnd()
2012-01-02 12:59:52.790 RingBuf(/var/lib/mythtv/recordings/2024_20120102125953.mpg) Warning: Not starting read ahead thread, already running
2012-01-02 12:59:54.295 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:54.296 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:54.296 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:54.296 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:54.296 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:54.297 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:54.297 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:54.297 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:54.297 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:54.298 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:54.298 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:54.298 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:54.299 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:54.299 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:54.299 [mpeg2video @ 0x5341b40]mpeg_decode_postinit() failure
2012-01-02 12:59:54.308 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2012-01-02 12:59:54.308 AFD: Opened codec 0xaed8ea90, id(MPEG2VIDEO) type(Video)
2012-01-02 12:59:54.308 AFD: codec MP2 has 2 channels
2012-01-02 12:59:54.308 AFD: Opened codec 0xabff0d60, id(MP2) type(Audio)
2012-01-02 12:59:54.401 AFD: Resetting byte context eof (livetv 1 was eof 0)
2012-01-02 12:59:54.560 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2012-01-02 12:59:54.563 [mpeg2video @ 0x5341b40]warning: first frame is no keyframe
2012-01-02 12:59:54.623 Player(5): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAAAuLL
2012-01-02 12:59:54.640 Player(5): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAAAuLL
2012-01-02 12:59:54.704 [mpeg2video @ 0x5341b40]warning: first frame is no keyframe
2012-01-02 13:00:03.900 RingBuf(/var/lib/mythtv/recordings/2024_20120102125953.mpg): Waited 0.2 seconds for data 
			to become available... 20080 < 32768
2012-01-02 13:00:08.064 TV: Attempting to change from WatchingLiveTV to None
2012-01-02 13:00:08.556 TV: Changing from WatchingLiveTV to None
2012-01-02 13:00:23.015 Deleting UPnP client...
Error in my_thread_global_end(): 2 threads didn't exit


```

Backend log:

```


2012-01-02 12:57:19.598 RecBase(8:/dev/video1): GetKeyframePositions(31,9223372036854775807,#1) out of 3
2012-01-02 12:58:02.705 TVRec(8): Changing from WatchingLiveTV to None
2012-01-02 12:58:03.076 MainServer::ANN Playback
2012-01-02 12:58:03.123 adding: MYTHBE2 as a client (events: 0)
2012-01-02 12:58:03.167 TVRec(7): Changing from None to WatchingLiveTV
2012-01-02 12:58:03.212 TVRec(7): HW Tuner: 7->7
2012-01-02 12:58:03.263 LoadFromScheduler(): Error, called from backend.
2012-01-02 12:58:03.441 Finished recording : channel 2004
2012-01-02 12:58:03.538 LoadFromScheduler(): Error, called from backend.
2012-01-02 12:58:03.589 recording already exists...
2012-01-02 12:58:03.648 Finished recording : channel 2004
2012-01-02 12:58:03.718 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hz
			is not supported by ivtv driver, using 48000 Hz instead.
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2012-01-02 12:58:06.038 RecBase(7:/dev/video0): GetKeyframePositions(31,9223372036854775807,#0) out of 2
2012-01-02 12:58:31.782 TVRec(7): Changing from WatchingLiveTV to None
2012-01-02 12:58:32.148 MainServer::ANN Playback
2012-01-02 12:58:32.193 adding: MYTHBE2 as a client (events: 0)
2012-01-02 12:58:32.238 TVRec(8): Changing from None to WatchingLiveTV
2012-01-02 12:58:32.282 TVRec(8): HW Tuner: 8->8
2012-01-02 12:58:32.333 LoadFromScheduler(): Error, called from backend.
2012-01-02 12:58:32.497 Finished recording : channel 2004
2012-01-02 12:58:32.588 LoadFromScheduler(): Error, called from backend.
2012-01-02 12:58:32.626 recording already exists...
2012-01-02 12:58:32.677 Finished recording : channel 2004
2012-01-02 12:58:32.734 MPEGRec(/dev/video1) Warning: Audio sample rate 32000 Hz
			is not supported by ivtv driver, using 48000 Hz instead.
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2012-01-02 12:58:35.219 RecBase(8:/dev/video1): GetKeyframePositions(31,9223372036854775807,#1) out of 3
2012-01-02 12:59:05.742 TVRec(8): HW Tuner: 8->8
2012-01-02 12:59:05.969 LoadFromScheduler(): Error, called from backend.
2012-01-02 12:59:06.028 Finished recording : channel 2004
2012-01-02 12:59:06.228 Finished recording : channel 2009
2012-01-02 12:59:06.273 LoadFromScheduler(): Error, called from backend.
2012-01-02 12:59:06.317 recording already exists...
2012-01-02 12:59:06.373 Finished recording : channel 2009
2012-01-02 12:59:08.499 RecBase(8:/dev/video1): GetKeyframePositions(16,9223372036854775807,#0) out of 2
Error in my_thread_global_end(): 1 threads didn't exit
2012-01-02 12:59:51.746 TVRec(8): HW Tuner: 8->8
2012-01-02 12:59:51.976 LoadFromScheduler(): Error, called from backend.
2012-01-02 12:59:52.033 Finished recording : channel 2009
2012-01-02 12:59:52.234 Finished recording : channel 2024
2012-01-02 12:59:52.268 LoadFromScheduler(): Error, called from backend.
2012-01-02 12:59:52.312 recording already exists...
2012-01-02 12:59:52.365 Finished recording : channel 2024
2012-01-02 12:59:54.521 RecBase(8:/dev/video1): GetKeyframePositions(16,9223372036854775807,#0) out of 2
Error in my_thread_global_end(): 1 threads didn't exit
2012-01-02 13:00:08.189 TVRec(8): Changing from WatchingLiveTV to None


```

The only serious issue I can see is in the frontend log, and that is with the "mpeg decode postinit failure".  The other items in there don't look like they are a real problem.  Aside from the blank screen, I do still get the "Error opening jump program file buffer" and occassionally "video frame buffering failed too many times".  

I tried taking out my ATi/AMD graphics card in favor of an nVidia based card, and this did improve things as far as the sluggish behavior of the frontend during the blank screens, but that is all.

I will be trying other things today.  I will post my success or failure.

---

### Post by jlp_engineer on 2012-01-02
OK...Long story short, no joy on all scenarios.

RECAP.

1 - Tried pulling one of the PVR-150's out of the slave backend where there were once there were three.

Didn't help...still get blank screens when switching channels.  However, for a period of time, the first PVR-150 (video0) would tune its default channel, and switch to any channel I put to it.  Then, as suddenly as it started working, it stopped.  And gave me the "Error opening jump program file buffer" or "video frame buffering failed too many times". Also, when I first brought up the frontend on the local machine, none of the internal tuners (both the remaining PVR-150's) would not show up.  I had to delete the tuner from the list in the backend setup, and then reboot, and then they showed up - strange.

2 - Tried setting the PCI latency on my hard disk controller.

This didn't seem to work, in the sense that I don't believe it was changing the value like the command was supposed to.  I issued the command "sudo setpci -v -s 00:1f.2 latency_timer=80", and although I got a response that seemed to indicate the command was processed, I issued an "lspci -v" command that said the timer was still set to the old value.  Perpahs the lspci command was reading a file system value, and not the one in memory?  So this may still work, I just cannot seem to change the value, or at least confirm the value is changed, to test it out.  :-k  I tried the frontend anyway, but got the same issue (blank screens on channel changes). :icon_frown:

3 - Tried changing the role of the slave backend, from slave to an independent master backend.  

What a fiasco this was...  ](*,)  Many of the settings from the master backend stayed in the new backend setup.  It wiped all the storage directory paths, so these all had to be put in.  When I deleted the digital video source, it deleted it from the old master backend.  Apparently it was still connected, but it should not have been.

I have not given up yet, and perhaps that is one of my biggest character flaws. :redface: I just cannot move forward unless I find a resolution to the issue.  I may start loading older versions of Mythbuntu and see how far back I need to go in order to get a stable working system.  I know version 8.10 works, as that was running for the past few years on the same hardware.  I have multiple images stored on my NAS that I can restore, just in case anyone has some ideas I can try with the more recent (11.04) version of mythbuntu.  I would hate to leave mythbuntu 11.xx, as I like how the storage folders are automatically networked between backends and frontends, and also how much easier it is to get the digital tuners working.

TIA

---

### Post by nickrout on 2012-01-03
> **jlp_engineer said:**
> OK...Long story short, no joy on all scenarios.

RECAP.

1 - Tried pulling one of the PVR-150's out of the slave backend where there were once there were three.

Didn't help...still get blank screens when switching channels.  However, for a period of time, the first PVR-150 (video0) would tune its default channel, and switch to any channel I put to it.  Then, as suddenly as it started working, it stopped.  And gave me the "Error opening jump program file buffer" or "video frame buffering failed too many times". Also, when I first brought up the frontend on the local machine, none of the internal tuners (both the remaining PVR-150's) would not show up.  I had to delete the tuner from the list in the backend setup, and then reboot, and then they showed up - strange.

2 - Tried setting the PCI latency on my hard disk controller.

This didn't seem to work, in the sense that I don't believe it was changing the value like the command was supposed to.  I issued the command "sudo setpci -v -s 00:1f.2 latency_timer=80", and although I got a response that seemed to indicate the command was processed, I issued an "lspci -v" command that said the timer was still set to the old value.  Perpahs the lspci command was reading a file system value, and not the one in memory?  So this may still work, I just cannot seem to change the value, or at least confirm the value is changed, to test it out.  :-k  I tried the frontend anyway, but got the same issue (blank screens on channel changes). :icon_frown:

3 - Tried changing the role of the slave backend, from slave to an independent master backend.  

What a fiasco this was...  ](*,)  Many of the settings from the master backend stayed in the new backend setup.  It wiped all the storage directory paths, so these all had to be put in.  When I deleted the digital video source, it deleted it from the old master backend.  Apparently it was still connected, but it should not have been.

I have not given up yet, and perhaps that is one of my biggest character flaws. :redface: I just cannot move forward unless I find a resolution to the issue.  I may start loading older versions of Mythbuntu and see how far back I need to go in order to get a stable working system.  I know version 8.10 works, as that was running for the past few years on the same hardware.  I have multiple images stored on my NAS that I can restore, just in case anyone has some ideas I can try with the more recent (11.04) version of mythbuntu.  I would hate to leave mythbuntu 11.xx, as I like how the storage folders are automatically networked between backends and frontends, and also how much easier it is to get the digital tuners working.

TIA

Perhaps stop using livetv. It's not what myth was/is designed for :)

Also, try the mailing list, there is a far greater depth of knowledge there, including many developers. Although there are a couple on this forum, you are far more likely to find someone knowledgeable on the mailing list.

---

### Post by klc5555 on 2012-01-03
> **nickrout said:**
> Perhaps stop using livetv. It's not what myth was/is designed for :)

Also, try the mailing list, there is a far greater depth of knowledge there, including many developers. Although there are a couple on this forum, you are far more likely to find someone knowledgeable on the mailing list.

I have to agree at this stage. There are serious ivtv driver/mythtv internal issues here that are unlikely to be resolvable in this forum.

---

### Post by jlp_engineer on 2012-01-05
I finally figured it out \\:D/.  Being a computer hardware engineer, however, I really should have gotten to this point long before this :oops:. My apologies to both of you (nickrout, and klc5555) and thanks for your time and patience.

It was (drum roll, please)...  a bad tuner card.  Depending where it was on the PCI bus, it would cause trouble with the other cards and make them behave erratically.  It finally dawned on me when I loaded up v8.10 (it was really nice to see the analog channel scans working again :grin:), which should have put me right where I was a few years ago, but surprise :shock:, I had exactly the same problem I left with running 11.04.  I can't believe I didn't think of that earlier #-o, given all the trouble I was having, and all the reconfigurations that I went through ](*,).

Well, at least I learned something in the process.  I will still be using separate backends for the analog and digital tuner groups.  Do you have any parting wisdom for the analog portion of the pcHDTV HD-5500?  I can only get snow from it, and I have it configured as a V4L device in the capture card setup.

---

### Post by klc5555 on 2012-01-05
> **jlp_engineer said:**
>  Do you have any parting wisdom for the analog portion of the pcHDTV HD-5500?  I can only get snow from it, and I have it configured as a V4L device in the capture card setup.

Well progress is progress! 

If in Input Connections the analog side of the 5500 has been bound to the analog Video Source (the same analog Video Source you're using for your surviving PVR-150s), it should pretty much Just Work. As long as the DVB half of the card isn't doing anything --these cards only do one tuner at a time. For that reason the card's analog recording settings were usually set to "open DVB device on demand", EIT scan was turned off, and the two halves of the card were bound to the same Input Group, so that the card would not inadvertently default to the DVB tuner when trying to tune an analog station or try to tune two differing types of signals simultaneously. Some older setup guidance for the analog half to play nicely with the digital half is found in this thread here: [http://ubuntuforums.org/showthread.php?t=1018513](http://ubuntuforums.org/showthread.php?t=1018513) 

If simple measures like this don't get the analog side of the card working, it's time to look at dmesg output for clues. It could be that the tuner is misdetected or no tveeprom is detected at all for it.

The remaining configuration caveats with this card generally pertain to analog sound configuration. That is, it wants to be set up for sound on the good old-fashioned device nodes /dev/dsp or /dev/dsp1. These were removed in 10.10 to solve some bug or other (and may not be back). In some cases the remaining /dev/ options result in no sound. The usual solution for those afflicted is to compile your own kernel, for which see here: [http://ubuntuforums.org/showthread.php?t=1607546](http://ubuntuforums.org/showthread.php?t=1607546) The analog side of the card is also sensitive to audio sampling rate --if the card has sound but it has a weird "tinny" quality, the sampling rate will need to be altered (to 48000) in both the backend setup and the frontend setup. 

There once was considerable detailed information on configuring the analog side of these cards on the mythtv wiki and on the v4l wiki. This info may have proved to be too useful and accordingly is no longer to be found. Some additional guidance, if necessary, may be had by combing through the sparse pickings in pchdtv's own forum.

---

