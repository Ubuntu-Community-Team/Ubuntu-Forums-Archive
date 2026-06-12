---
title: "[SOLVED] QAM Station Display Problems"
date: 2008-08-10
forum: Mythbuntu
---

### Post by Ronno6 on 2008-08-10
I'm so close now. One final setup point:
When I tune to a QAM channel the display just shows multicolored static, for loss of a better term. The screen pretty much freezes up. No viewable video or intelligible audio. 
How do I correct this one?
Dell Optiplex GX270 Pentium 4 2.8ghz, 2gig RAM
Fusion HDTV5RT Gold tuner, QAM capapble
pny NVIDIA Verto 6200 video AGP

---

### Post by Ronno6 on 2008-08-11
Further information: I have installed the NVIDIA drivers package that comes with Mythbuntu 8.04.1, and configured resolution for 1280x720. I'm using TV out via component outputs, into n Akai 32" 720p screen. 
The tuner in the Akai tunes and displays the QAM stations properly, so I know that they are clear. 
Is any further information required to obtain suggestions for the fix?
Thanks.

---

### Post by newlinux on 2008-08-11
Sounds like a video configuration problem. Can you playback any of the QAM recordings on another machine properly? Can you playback other media files successfully?

---

### Post by Ronno6 on 2008-08-11
I have not moved into the world of recordings as of yet. The problem is while watching live TV (or-attempting to do so.)Regular cable channels are fine-problem exists with the QAM channels only.

---

### Post by newlinux on 2008-08-11
livetv is really no different than recordings to myth (it records everything you watch live). if you could just hit the "r" key when you are watching something that would suffice. Or you can find files from when you are watching livetv in your livetv storage group (but by default they get cleaned deleted pretty quickly). If you can test the files you will be able to find out if the problem is playback related or capture related with the QAM recordings, assuming your QAM scan in myth went fine.

---

### Post by Ronno6 on 2008-08-12
Is there a separate scan for QAM channels in Muthbuntu? The QAM stations appeared after the one channel scan in backend setup. 
I don't have another machine on which to test the recordings. 
As I get no intelligible sound I would have to consider that it is a tuning or processing issue. Maybe as I am using a Pentium 4 2.8gig machine as frontend and backend, which is not recommended, the problem lies there?

Thanks for your input so far. I am a newbie at Debian, Linux, and Mythbuntu, so I am learning as I go.

---

### Post by novellahub on 2008-08-12
I belive a Pentium 4 2.8 ghz machine is capable of QAM HDTV playback. Do you have a "Digital Cable" type lineup for schedules direct?  I used this for my Kworld 115 QAM setup.  I then did a channel scan after associating the lineup with the tv card (I use QAM-256 in my area).  Also, what do you have the tuner set up as? DVB?

---

### Post by newlinux on 2008-08-12
I used to run a hidef capable combined frontend backend with a P4 2.6 and 3 tuners, so you should have enough power. 

QAM scanning is in the same place in mythtv-setup, but you have to use different settings. 

you can test the recordings on the same machine using a VLC or mplayer and see what that yields as well (cd into your recordings or livetv directory and use the command line, or use a file manager (nautilus/konqueror/thunar) to open them. This will at least tell you if the internal myth player is the problem as opposed to a system problem.

Maybe we should take a step back so that I know exactly where you are.

1. Do you have your Dvico Fusion 5 set up as a DVB card?
2. Your QAM scan settings should be something like QAM 256 (there may be some station on QAM 64 so you might want to do a QAM 64 scan too). Do a full cable scan.

---

### Post by newlinux on 2008-08-12
Also, check your frontend and backend logs for errors...

---

### Post by Ronno6 on 2008-08-12
> **novellahub said:**
>  Do you have a "Digital Cable" type lineup for schedules direct?  I used this for my Kworld 115 QAM setup.  I then did a channel scan after associating the lineup with the tv card (I use QAM-256 in my area).  Also, what do you have the tuner set up as? DVB?

The "Digital Lineup" for my cable company differs from the "Basic Cable" lineup. But, the clear QAM channels are present in the basic lineup. So., if the Digital Lineup schedule is required, I have not utilized it as of yet. I don't know where to set the card up as aDVB card, so I would have to say "No" t that question to both you and newlinux.

newlinux, 
All's I did was a full scan. I did not set up any specifications for the QAM channels 264 or 64. Do I do that as a separate job? How and where? (I told ya I'm a newbie!)

WAIT_ I'm attempting to do it, and-It's doing something! I'll let you know how it turns out. Thanks

Thanks,guys, for your help so far.

---

### Post by newlinux on 2008-08-12
Just downloading a lineup won't be good enough for QAM because many of the channels won't match your schedules direct information you may have to go in and fix some of that later. You definitely need to do a full scan with QAM settings in mythtv-setup with the card setup as a DVB card (create an a capture card with your dvico with the DVB driver). The scan should take a a little while. you should apply this scan using your "digital lineup"

Let us know exactly what you did to setup this card when you post back.

---

### Post by Ronno6 on 2008-08-12
What I did? I goofed it up, that's what I did. Now I can't even bring the frontend or backend up at all. I get this pretty blue screen asking me to select a language, then a screen that says "No UPnP backends found", then the "Database configuration 1/2" screen then "2/2" then Cannot log into database? And that's all, folks.

I had set up the card as DVB as an additional source,scanned for channels, found them, filled the database, although no programming ever appeared for the digital channels. After doing this, the previously viewable channels became unwatchable. Now, BSOD !! I thought that only occurred in Windows! I am dead in the water.

I'm beginning to agree with Pinny Parlour!

---

### Post by newlinux on 2008-08-12
did you change your database server IP or password or something? Is mysql running?

---

### Post by Ronno6 on 2008-08-12
Yup. Changed user name and password, I believe in front end setup.I thought I had done that during setup to begin with. Went to watch live TV, and it went back to desktop. Next time I tried to open, BSOD! 
How do I correct?

How do i check if mysql is running?

---

### Post by Ronno6 on 2008-08-13
Well, I know not to do *THAT* again! Reloaded, started from scratch. Now, back to the original issue.

---

### Post by newlinux on 2008-08-13
When I asked for exactly how you setup the card I needed more detail (driver setup for the capture card, what video source you attached to it, *all* scan settings, the result of your scan, etc.) than what you gave to figure out the problem. Do you have any other capture cards setup. You said you can see non QAM stations. Do you have this card setup as a V4L card as well?


With QAM stations, its doubtful mythfilldatabase will be useful until you have mapped them to their corresponding stations in your lineup (using XMLTVIDs or station identifiers), unless your provider sends good PSIP information that is picked up during the scan.

---

### Post by Ronno6 on 2008-08-13
I hope this is complete:

This card IS set up as V4L card for TELEVISION output.
It is the only capture card in the machine.
I am using the default driver provided by Linux/ubuntu/Mythbuntu. I have not installed any proprietary driver for this card.

New Capture card
  Card Type : DVB DTV capture V3.X
  DVB Device number: 0
  all else DEFAULT SETTINGS

Video Source
   Name: QAM Fusion HDTV 5
   Listings Grbber: Schedules Direct.org
   Retrieved listings for Digital Channels
   Channel frequency table: us-cable

Input Connections
   Video Source: QAM Fusion HDTV 5
   Fetched Channels from listing source
   Scanned for channels
      Modulation QAM256
      Channel separator 5_1
      All other settings DEFAULT

The scan yielded the QAM channels

Scanning for AM64 gave a blank scanning screen.

Interactions between inputs: 
   Group 1 shows as DVB0
   Group 2 generic

I ram Mythfilldatabase

Plus, now I am asked for my password when exiting backend setup, before being asked to  to run mythfilldatabase. This is a bit curious.

The QAM channels, complete with listings in the program guide now appear. However, regular channels are now unwatchable: Choppy and staticy, and the QAM channels just display lined colored static as before.
I hope this helps.Thank you for your help so far.

---

### Post by newlinux on 2008-08-13
When you say "regular" channels what do you mean? What are you using to tune none QAM channels? Did you setup a different tuner for that or did you setup your Dvico as a V4L tuner as well? If you are doing a scan you really shouldn't fetch channel listings from source for QAM. You'll end up pulling in stations you can't tune with QAM unless you already eliminated all those in schedules direct and the ones you did pull down match your QAM scan output.

I think you should stick to one step at a time. Delete all your channels, do not fetch listings from provider, scan with QAM, do not run mythfilldatabase, and try to tune channels from there. See what your QAM channel listing looks like from there as well and try to tune a few of your QAM stations.

---

### Post by Ronno6 on 2008-08-13
I only have 1 tuner card: divico Fusion HDTV 5 RT Gold
By "regular" I meant cable, non QAM channels. This card was set up to do cable AND QAM channels.
I deleted all capture cards, as I had this tuner set up as both V4L and DVB. I deleted video sources.
I did not fetch channels from the source. 

I set the Fusion card up as DVB0, scanned for channels. Found 16#0, 16#2,16#3,64#'s 0-3,and 65#'s 0-7. 

When I tried to "Watch TV" the screen went blank giving channel information at the bottom of the screen (channel # and "unknown"information,)then went totally blank. and the processor fan sped way up. The computer froze in that state, and I had to do a hard restart to free up.

All channels appear in the program guide, and are all listed as "unknown. 
They will not even display as colored static as before. 

Thank you for your ongoing help.

---

### Post by newlinux on 2008-08-13
At least now you can be sure the channels you have available to you can actually be tuned by your card. You can clean up the listings and channels names and guide info later. That's the easy part. I'm just trying to eliminate as many variable sas possible when troubleshooting because without seeing your system that's the easiest way for me to help. that's why I wanted you to only setup the DVB card, no other cards. You do need to have video sources however, you will want to recreate those, but not fetch channels from listings, but still assign one to the input. I wanted you to delete the channels, not the video sources.

After you do that, it would be really helpful to see the logs I asked about earlier, especially the frotnend log at the time you are trying to tune a station.

BTW, QAM is cable, just digital transmitted. By regular channels you mean analog cable. 

I strongly recommend you just try to get the DVB driver working by itself before adding the V4L input. Since your card really is only one tuner that can tune two different types of signals (digital and analog) we want to eliminate any chance of conflict (I have a dvico and other cards that do QAM and NTSC cable, and if for some reason the analog side or digital side is being used or hasn't been released my system will crash if the other side of the card is attempted to be used at the same time). When you get it all setup, you will want to setup your input groups properly so both sides of the cards cannot be accessed at the same time by myth. that's later though.

Make sure you have the Open DVB card on demand option checked too in the capture card setup (in recording options). You'll neeed that option or you'll have problems switching from the analog to the digital side of the card when tuning or vice versa.

---

### Post by Ronno6 on 2008-08-13
I've set up the video sources, without fetching channels. I've put an "X"by  the Open DVB card on demand option (in recording options.) I hope that is correct. Normally I would consider an "x" to disallow something. 

Now, as I am a linux/Ubuntu newb, how do I get the logs you requested? Once displayed, it it a simple cut and paste to this thread?

The Mythbuntu box is a different machine from this one, but I can connect to this forum via that HTPC. 

Thanks again.

---

### Post by newlinux on 2008-08-13
Are you running mythfrontend from the Applications menu? If so it puts the logs in the:

/var/log/mythtv/

folder (mythfrontend.log is the frontend log, mythbackend.log is the backend)

If you run it from commandline you could do:
```

mythfrontend -l <LOGFILE>

```

and it will put the log in whatever you specify as <LOGFILE>

Now if you run it commandline, you can get more detailed logs by doing:

```

mythfrontend -v playback -l <LOGFILE>

```
This will give more information about playback.

You can cut and paste the relevant sections (you may need to look through them to figure out whats relevant, look for sections with the time code near where you are having the problem tuning in the station.
Yep, X indicates it is selected.

---

### Post by Ronno6 on 2008-08-13
I hope I get relevant parts:
From the frontend log:
2008-08-13 15:24:24.887 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-08-13 15:24:24.890 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-08-13 15:24:24.927 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.102:5060 NAT address 192.168.1.102
SIP: Cannot register; proxy, username or password not set
2008-08-13 15:25:10.874 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-08-13 15:25:10.875 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
Destroying SipFsm object 
2008-08-13 15:25:21.494 Deleting UPnP client...
Starting mythfrontend.real..
2008-08-13 15:27:12.138 New DB connection, total: 2
2008-08-13 15:27:12.139 Connected to database 'mythconverg' at host: localhost
2008-08-13 15:27:12.141 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-08-13 15:27:12.141 Enabled verbose msgs:  important general
2008-08-13 15:27:12.237 Unable to parse themeinfo.xml for glass-wide
2008-08-13 15:27:12.237 The theme (glass-wide) is missing a themeinfo.xml file
2008-08-13 15:27:12.401 Unable to parse themeinfo.xml for glass-wide
2008-08-13 15:27:12.401 The theme (glass-wide) is missing a themeinfo.xml file
2008-08-13 15:27:12.660 Primary screen 0.
2008-08-13 15:27:12.661 Using screen 0, 1280x720 at 0,0
2008-08-13 15:27:12.663 Switching to square mode (Mythbuntu-8.04)
2008-08-13 15:27:12.679 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-08-13 15:27:12.680 lirc_init failed for mythtv, see preceding messages
2008-08-13 15:27:12.680 JoystickMenuClient Error: Joystick disabled - Failed to read /home/ronno6/.mythtv/joystickmenurc
2008-08-13 15:27:13.789 Specified base font 'medium' does not exist for font clock
2008-08-13 15:27:13.789 Specified base font 'medium' does not exist for font small
2008-08-13 15:27:13.789 Specified base font 'medium' does not exist for font medium
2008-08-13 15:27:13.789 Specified base font 'medium' does not exist for font large
2008-08-13 15:27:13.790 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-08-13 15:27:13.876 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-08-13 15:27:13.929 Registering Internal as a media playback plugin.
2008-08-13 15:27:14.211 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-08-13 15:27:14.261 Failed to run 'cdrecord --scanbus'
2008-08-13 15:27:14.264 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-08-13 15:27:14.267 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-08-13 15:27:14.303 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.102:5060 NAT address 192.168.1.102
SIP: Cannot register; proxy, username or password not set
2008-08-13 15:27:19.969 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-08-13 15:27:19.971 Using protocol version 40
2008-08-13 15:27:19.983 TV: Attempting to change from None to WatchingLiveTV
2008-08-13 15:27:19.984 Using protocol version 40
2008-08-13 15:27:21.191 New DB connection, total: 3
2008-08-13 15:27:21.191 Connected to database 'mythconverg' at host: localhost
2008-08-13 15:27:21.204 DPMS Deactivated 
2008-08-13 15:27:21.239 NVP: Disabling Audio, params(-1,2,44100)
2008-08-13 15:27:21.319 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-08-13 15:27:21.380 OSD Theme Dimensions W: 640 H: 480
2008-08-13 15:27:22.151 TV: Changing from None to WatchingLiveTV
2008-08-13 15:27:22.159 Realtime priority would require SUID as root.
2008-08-13 15:27:22.257 Video timing method: USleep with busy wait
2008-08-13 15:27:23.815 VideoOutputXv: XvMC Adaptor Name: 'NV17 Video Texture'
2008-08-13 15:27:24.382 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2008-08-13 15:27:24.383 VideoOutputXv: ProcessFrameXvMC: Called without frame
2008-08-13 15:27:24.384 AFD: Opened codec 0x8607460, id(MPEG2VIDEO_XVMC) type(Video)
2008-08-13 15:27:24.384 AFD: codec AC3 has 6 channels
2008-08-13 15:27:24.385 AFD: Opened codec 0x871d790, id(AC3) type(Audio)
2008-08-13 15:27:24.472 Opening audio device 'default'. ch 2(2) sr 48000
2008-08-13 15:27:24.473 Opening ALSA audio device 'default'.
2008-08-13 15:27:24.549 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2008-08-13 15:27:24.550 VideoOutputXv: ProcessFrameXvMC: Called without frame
2008-08-13 15:27:24.716 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2008-08-13 15:27:24.716 VideoOutputXv: ProcessFrameXvMC: Called without frame
2008-08-13 15:27:24.883 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2008-08-13 15:27:24.883 VideoOutputXv: ProcessFrameXvMC: Called without frame
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-08-13 15:27:24.989 AudioOutput Warning: Mixer attach error -2: No such file or directory
			Check Mixer Name in Setup: '/dev/mixer'
2008-08-13 15:27:24.991 NVP: Enabling Audio
2008-08-13 15:27:25.013 XvMC: picture structure FRAME
2008-08-13 15:27:25.016 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:26.346 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:27.677 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:29.007 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:30.337 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:31.668 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:32.998 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:34.328 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:35.659 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:36.989 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:38.320 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:39.650 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:40.980 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:42.310 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:43.641 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:44.971 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:46.301 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:47.632 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:48.962 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:50.293 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:50.850 TV: Attempting to change from WatchingLiveTV to None
2008-08-13 15:27:51.623 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:52.954 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:54.285 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:55.615 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:56.945 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:58.275 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:27:59.606 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:28:00.936 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:28:02.266 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:28:03.596 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:28:04.926 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:28:06.257 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:28:07.587 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:28:08.918 NVP: Prebuffer wait timed out 10 times.
2008-08-13 15:28:10.248 NVP: Prebuffer wait timed out 10 times.
ICE default IO error handler doing an exit(), pid = 6389, errno = 11
Mutex destroy failure: Device or resource busy
Mutex destroy failure: Device or resource busy
Starting mythfrontend.real..
2008-08-13 15:29:43.603 New DB connection, total: 2
2008-08-13 15:29:43.604 Connected to database 'mythconverg' at host: localhost
2008-08-13 15:29:43.605 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-08-13 15:29:43.606 Enabled verbose msgs:  important general
2008-08-13 15:29:45.843 Unable to parse themeinfo.xml for glass-wide
2008-08-13 15:29:45.843 The theme (glass-wide) is missing a themeinfo.xml file
2008-08-13 15:29:47.292 Unable to parse themeinfo.xml for glass-wide
2008-08-13 15:29:47.292 The theme (glass-wide) is missing a themeinfo.xml file
2008-08-13 15:29:49.991 Primary screen 0.
2008-08-13 15:29:49.991 Using screen 0, 1280x720 at 0,0
2008-08-13 15:29:49.993 Switching to square mode (Mythbuntu-8.04)
2008-08-13 15:29:50.062 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-08-13 15:29:50.062 lirc_init failed for mythtv, see preceding messages
2008-08-13 15:29:50.063 JoystickMenuClient Error: Joystick disabled - Failed to read /home/ronno6/.mythtv/joystickmenurc
2008-08-13 15:29:54.062 Specified base font 'medium' does not exist for font clock
2008-08-13 15:29:54.063 Specified base font 'medium' does not exist for font small
2008-08-13 15:29:54.063 Specified base font 'medium' does not exist for font medium
2008-08-13 15:29:54.063 Specified base font 'medium' does not exist for font large
2008-08-13 15:29:54.064 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-08-13 15:29:54.219 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-08-13 15:29:54.331 Registering Internal as a media playback plugin.
2008-08-13 15:29:54.765 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-08-13 15:29:55.386 Failed to run 'cdrecord --scanbus'
2008-08-13 15:29:55.389 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-08-13 15:29:55.392 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-08-13 15:29:55.434 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.102:5060 NAT address 192.168.1.102
SIP: Cannot register; proxy, username or password not set
2008-08-13 16:06:03.568 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-08-13 16:06:03.569 Using protocol version 40
Destroying SipFsm object 
2008-08-13 16:06:06.138 Deleting UPnP client...

From the backend log:
2008-08-13 15:27:02.580 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-13 15:27:02.583 Empty LocalHostName.
2008-08-13 15:27:02.585 Using localhost value of MythbuntuHTPC
2008-08-13 15:27:02.596 New DB connection, total: 1
2008-08-13 15:27:02.618 Connected to database 'mythconverg' at host: localhost
2008-08-13 15:27:02.622 Closing DB connection named 'DBManager0'
2008-08-13 15:27:02.623 Connected to database 'mythconverg' at host: localhost
2008-08-13 15:27:02.627 New DB connection, total: 2
2008-08-13 15:27:02.633 Connected to database 'mythconverg' at host: localhost
2008-08-13 15:27:02.637 Current Schema Version: 1214
Starting up as the master server.
2008-08-13 15:27:02.666 New DB connection, total: 3
2008-08-13 15:27:02.667 Connected to database 'mythconverg' at host: localhost
2008-08-13 15:27:02.726 New DB scheduler connection
2008-08-13 15:27:02.727 Connected to database 'mythconverg' at host: localhost
2008-08-13 15:27:02.784 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-08-13 15:27:02.785 Main::Registering HttpStatus Extension
2008-08-13 15:27:02.786 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-08-13 15:27:02.788 Enabled verbose msgs:  important general
2008-08-13 15:27:02.791 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-13 15:27:05.732 Reschedule requested for id -1.
2008-08-13 15:27:05.759 Scheduled 0 items in 0.0 = 0.01 match + 0.02 place
2008-08-13 15:27:05.766 Seem to be woken up by USER
2008-08-13 15:27:19.971 MainServer::HandleAnnounce Monitor
2008-08-13 15:27:19.975 adding: MythbuntuHTPC as a client (events: 0)
2008-08-13 15:27:19.976 MainServer::HandleAnnounce Monitor
2008-08-13 15:27:19.977 adding: MythbuntuHTPC as a client (events: 1)
2008-08-13 15:27:19.984 MainServer::HandleAnnounce Playback
2008-08-13 15:27:20.006 adding: MythbuntuHTPC as a client (events: 0)
2008-08-13 15:27:20.008 TVRec(4): Changing from None to WatchingLiveTV
2008-08-13 15:27:20.018 TVRec(4): HW Tuner: 4->4
2008-08-13 15:27:20.042 New DB connection, total: 4
2008-08-13 15:27:20.045 Connected to database 'mythconverg' at host: localhost
2008-08-13 15:27:21.130 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-13 15:27:21.625 Finished recording Unknown: channel 1160
2008-08-13 15:27:22.682 Finished recording Unknown: channel 1160
2008-08-13 15:27:22.729 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-08-13 15:27:22.965 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-13 15:27:22.969 Empty LocalHostName.
2008-08-13 15:27:22.970 Using localhost value of MythbuntuHTPC
2008-08-13 15:27:22.980 New DB connection, total: 1
2008-08-13 15:27:22.986 Connected to database 'mythconverg' at host: localhost
2008-08-13 15:27:22.987 Closing DB connection named 'DBManager0'
2008-08-13 15:27:22.989 Connected to database 'mythconverg' at host: localhost
2008-08-13 15:27:22.995 New DB connection, total: 2
2008-08-13 15:27:22.996 Connected to database 'mythconverg' at host: localhost
2008-08-13 15:27:23.000 Current Schema Version: 1214
2008-08-13 15:27:23.013 Preview Error: Previewer file '/var/lib/mythtv/recordings/1160_20080813152720.mpg' is not valid.
2008-08-13 15:27:23.015 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/1160_20080813152720.mpg'
2008-08-13 15:27:23.023 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/recordings/1160_20080813152720.mpg.png) exists: 0 readable: 0 size: 0
2008-08-13 15:27:50.890 TVRec(4): Changing from WatchingLiveTV to None
2008-08-13 15:27:51.169 Finished recording Unknown: channel 1160
2008-08-13 15:29:17.428 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-13 15:29:17.629 Empty LocalHostName.
2008-08-13 15:29:17.754 Using localhost value of MythbuntuHTPC
2008-08-13 15:29:17.911 New DB connection, total: 1
2008-08-13 15:29:17.923 Connected to database 'mythconverg' at host: localhost
2008-08-13 15:29:17.925 Closing DB connection named 'DBManager0'
2008-08-13 15:29:17.927 Connected to database 'mythconverg' at host: localhost
2008-08-13 15:29:17.950 New DB connection, total: 2
2008-08-13 15:29:18.116 Connected to database 'mythconverg' at host: localhost
2008-08-13 15:29:18.247 Current Schema Version: 1214
Starting up as the master server.
2008-08-13 15:29:18.519 New DB connection, total: 3
2008-08-13 15:29:18.736 Connected to database 'mythconverg' at host: localhost
2008-08-13 15:29:18.903 New DB scheduler connection
2008-08-13 15:29:19.148 Connected to database 'mythconverg' at host: localhost
2008-08-13 15:29:19.488 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-08-13 15:29:19.505 Main::Registering HttpStatus Extension
2008-08-13 15:29:19.574 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-08-13 15:29:19.575 Enabled verbose msgs:  important general
2008-08-13 15:29:19.698 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-13 15:29:22.352 Reschedule requested for id -1.
2008-08-13 15:29:22.588 Scheduled 0 items in 0.2 = 0.16 match + 0.07 place
2008-08-13 15:29:22.746 Seem to be woken up by USER
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
2008-08-13 15:30:39.352 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-13 15:30:39.401 Expiring 0 MBytes for 1160 @ Wed Aug 13 15:27:20 2008 => Unknown
2008-08-13 15:30:39.406 Expiring 56 MBytes for 1160 @ Wed Aug 13 15:27:21 2008 => Unknown
QDateTime::fromString: Parameter out of range
2008-08-13 15:45:39.441 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QDateTime::fromString: Parameter out of range
QDateTime::fromString: Parameter out of range
2008-08-13 16:00:39.466 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-08-13 16:06:03.570 MainServer::HandleAnnounce Monitor
2008-08-13 16:06:03.575 adding: MythbuntuHTPC as a client (events: 0)
2008-08-13 16:06:03.577 MainServer::HandleAnnounce Monitor
2008-08-13 16:06:03.578 adding: MythbuntuHTPC as a client (events: 1)
QDateTime::fromString: Parameter out of range
2008-08-13 16:15:39.498 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QDateTime::fromString: Parameter out of range

I know it's a bunch, but it is all from the relevant time. hope this holds the key.
Thanks again.

---

### Post by newlinux on 2008-08-13
first thought from scanning through that is look into your playback profile (Setup->TV Settings-> Playback). Which one are you currently using?

Try using CPU++ or CPU+ to start. It looks like it is definitely having a display problem, trying to use XvMC, which you shouldn't need to use.

---

### Post by newlinux on 2008-08-13
just as another thing to do, try enabling extra audio buffering (in the Playback settings as well)

---

### Post by Ronno6 on 2008-08-13
Current playback setting is CPU+

Should I change to CPU++  ?
Extra audio buffering is enabled already. Once again, "X" marks enabled ?

---

### Post by newlinux on 2008-08-13
> **Ronno6 said:**
> Current playback setting is CPU+

Should I change to CPU++  ?
Extra audio buffering is enabled already. Once again, "X" marks enabled ?

Yes, CPU+ uses XvMc for High def content. CPU++ doesn't.

---

### Post by newlinux on 2008-08-13
Since your problem seems to be playback, you can try other profiles too. Hopefully one of the preset profiles will work, otherwise you may need to look into setting up a custom one.

---

### Post by newlinux on 2008-08-13
If CPU++ doesn't change anything, be sure to post the relevant sections of the frontend log after trying to view with that. It will be interesting to see what changes.

---

### Post by Ronno6 on 2008-08-13
BINGO ! CPU++ did the trick. Thanks!

Now, where do I go from here for analog channels?

---

### Post by newlinux on 2008-08-13
You'd want to go back into mythtv-setup and create a V4L card, attach the analog video source (tied to your analog schedules direct listing), and if you already know what channels you get analog and have them setup in schedules direct, you can just fetch the channels, you don't need to scan in this case. You will want to create input groups and put both tuners in the same input group (not Generic). I'm not completely sure how input groups work, but in theory if you put both your V4L and dvb input devices into the same input groups, they should not be able to be used at the same time (so you don't get the conflict, since only one can be used at a time).

You'll also want to match up your QAM channels with their actual channel numbers so that the schedules direct data (from mythfilldatabase) fills in the right channels and guide information. All you need to do is put in their XMLID for each channel in the mythweb or the channel editor in mythtv-setup. You can get the XMLID from schedules direct.

---

### Post by Ronno6 on 2008-08-14
Well, I hope I have things set up correctly, but it isn't working yet. As I did not scan analog channels for the V4L card, do I need to TRANSPORT the lineup from channel editor? Or, somehow ADD the channels manually? I fetched the lineup, ran Mythdatafill, and all channels appear on the program guide, along with program information for the analog channels. Problem is, when watching TV, the only channels available using the up/down keys are the digital channels. The analog channels are not there. I've missed a step somewhere. 

Does any sort of comprehensive guide on "Using Mythbuntu" exist anywhere?

Thanks again for the help so far.

---

### Post by newlinux on 2008-08-14
When watching liveTV, pressing up and down will only show you channels that are available for that input (in this case, your QAM input). Don't ask me why, it's annoying. If you press teh "y" while watching liveTV key you can switch to your other tuner and you should see your analog stations (but not your QAM). The only way to see both is look at the guide ("s" key I believe, I use a remote so I don't remember). And you can direct tune as well if you know the station number. just enter it directly from either tuner.

---

### Post by newlinux on 2008-08-14
For a decent (but not comprehensive) userguide to myth in general:

[http://www.mythtv.org/wiki/index.php/User_Manual:Index](http://www.mythtv.org/wiki/index.php/User_Manual:Index)

---

### Post by Ronno6 on 2008-08-14
Once again you are on target. I am going to list this thread as "solved." I will start another for further inquiries.

Thank you, again.

---

### Post by agamotto on 2008-08-21
You typically want to scan the high cable frequencies for QAM-256, this solves most people's problems.  If you are looking for the unscrambled digital HD channels, use 8-VSB instead of QAM-256 in the same frequencies.

---

