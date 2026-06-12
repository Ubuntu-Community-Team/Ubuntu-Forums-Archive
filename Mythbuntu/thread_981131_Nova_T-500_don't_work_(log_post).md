---
title: "Nova T-500 don't work (log post)"
date: 2008-11-13
forum: Mythbuntu
---

### Post by oscar69 on 2008-11-13
Hi all, I'm having some trouble with the DBV-T card from Hauppauge.

I'm new about Mythtv, so for now I tried to make it working with less hand-work as possible.

I started with a fresh 8.4 Ubuntu, after that I installed the Mythbuntu from the link in Mythbuntu site.

In the same case I've also a Hauppauge PVR-500, that works perfectly: I've also used the S-Video from it, with success.

I've tried a lot of triks from forums, but nothing solved.

The only changes I noticed is that using the "options dvb-usb-dib0700 force_lna_activation=1" sometime (very few, just 1 or 2) it worked: the first time I watched live tv, the second one I saw nothing, but found the temporary file full.

Here is the frontend log:

Starting mythfrontend.real..
2008-11-12 20:19:20.760 New DB connection, total: 2
2008-11-12 20:19:20.761 Connected to database 'mythconverg' at host: localhost
2008-11-12 20:19:20.762 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-11-12 20:19:20.762 Enabled verbose msgs:  important general
2008-11-12 20:19:21.042 No theme dir: /home/oscar/.mythtv/themes/G.A.N.T
2008-11-12 20:19:21.044 Primary screen 0.
2008-11-12 20:19:21.044 Using screen 0, 1280x1024 at 0,0
2008-11-12 20:19:21.044 No theme dir: /home/oscar/.mythtv/themes/G.A.N.T
2008-11-12 20:19:21.045 Switching to square mode (G.A.N.T)
2008-11-12 20:19:21.068 Using the Qt painter
mythtv: could not connect to socket
mythtv: Connection refused
2008-11-12 20:19:21.068 lirc_init failed for mythtv, see preceding messages
2008-11-12 20:19:21.068 JoystickMenuClient Error: Joystick disabled - Failed to read /home/oscar/.mythtv/joystickmenurc
2008-11-12 20:19:22.139 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2008-11-12 20:19:22.294 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-11-12 20:19:22.316 Registering Internal as a media playback plugin.
2008-11-12 20:19:22.374 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-11-12 20:19:22.376 No theme dir: /home/oscar/.mythtv/themes/G.A.N.T
2008-11-12 20:20:12.246 Connecting to backend server: 192.168.91.34:6543 (try 1 of 5)
2008-11-12 20:20:12.248 Using protocol version 40
2008-11-12 20:20:12.261 TV: Attempting to change from None to WatchingLiveTV
2008-11-12 20:20:12.262 Using protocol version 40
2008-11-12 20:20:14.439 New DB connection, total: 3
2008-11-12 20:20:14.440 Connected to database 'mythconverg' at host: localhost
2008-11-12 20:20:14.470 DPMS Deactivated 
2008-11-12 20:20:15.433 AFD: Opened codec 0x2943920, id(MPEG2VIDEO) type(Video)
2008-11-12 20:20:15.433 AFD: codec MP2 has 2 channels
2008-11-12 20:20:15.433 AFD: Opened codec 0x27cb3c0, id(MP2) type(Audio)
2008-11-12 20:20:15.557 Opening audio device 'default'. ch 2(2) sr 48000
2008-11-12 20:20:15.557 Opening ALSA audio device 'default'.
2008-11-12 20:20:15.573 ALSA, Warning: mmap not available, attempting to fall back to slow writes.
2008-11-12 20:20:15.689 Mixer unable to find control PCM
2008-11-12 20:20:15.689 Mixer unable to find control PCM
2008-11-12 20:20:15.694 Mixer unable to find control PCM
2008-11-12 20:20:15.694 Mixer unable to find control PCM
2008-11-12 20:20:15.695 Mixer unable to find control PCM
2008-11-12 20:20:15.695 Mixer unable to find control PCM
2008-11-12 20:20:15.696 Mixer unable to find control PCM
2008-11-12 20:20:15.738 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-11-12 20:20:15.811 OSD Theme Dimensions W: 640 H: 480
2008-11-12 20:20:16.247 TV: Changing from None to WatchingLiveTV
2008-11-12 20:20:16.254 Realtime priority would require SUID as root.
2008-11-12 20:20:16.356 Video timing method: USleep with busy wait
2008-11-12 20:20:34.856 Using protocol version 40
2008-11-12 20:20:43.055 RingBuf(/var/lib/mythtv/recordings/2006_20081112202035.mpg): Invalid file (fd -1) when opening '/var/lib/mythtv/recordings/2006_20081112202035.mpg'.
2008-11-12 20:20:43.067 NVP: Disabling Audio, params(-1,2,44100)
2008-11-12 20:20:43.086 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-11-12 20:20:43.156 OSD Theme Dimensions W: 640 H: 480
2008-11-12 20:20:43.539 Realtime priority would require SUID as root.
2008-11-12 20:20:43.545 New DB connection, total: 4
2008-11-12 20:20:43.546 Connected to database 'mythconverg' at host: localhost
2008-11-12 20:20:43.659 Something went terribly wrong in PMT parsing when looking at program info

Last line repeated 225 times, with some line :

2008-11-12 20:20:45.681 NVP: Prebuffer wait timed out 10 times.

After that, logs ends with:

2008-11-12 20:21:08.429 RingBuf(/var/lib/mythtv/recordings/2006_20081112202036.mpg): Timing out wait due to impending livetv switch.
2008-11-12 20:21:08.429 Tuning to 'MPEG Program 1' pnum: 0x1 without CRC check on PMT
2008-11-12 20:21:08.439 mpegts_read_header: could not find any PMT's
2008-11-12 20:21:08.439 AFD Error: avformat err(-1) on av_open_input_file call.
2008-11-12 20:21:08.439 Couldn't open decoder for: /var/lib/mythtv/recordings/2006_20081112202036.mpg
2008-11-12 20:21:08.439 NVP, Error: JumpToProgram failed.
2008-11-12 20:21:08.441 TV: Attempting to change from WatchingLiveTV to None
2008-11-12 20:21:08.490 NVP, Error: Unknown error, exiting decoder
2008-11-12 20:21:08.502 NVP: Prebuffer wait timed out 10 times.
2008-11-12 20:25:21.375 TV: Changing from WatchingLiveTV to None
2008-11-12 20:25:21.433 DPMS Reactivated.
2008-11-12 20:25:24.141 Deleting UPnP client...


The fronted exit from watching tv screen, and come back to the menu.
In the meantime in the backend log:

2008-11-12 20:19:08.640 New DB connection, total: 3
2008-11-12 20:19:08.660 Connected to database 'mythconverg' at host: localhost
2008-11-12 20:19:10.271 New DB scheduler connection
2008-11-12 20:19:10.272 Connected to database 'mythconverg' at host: localhost
2008-11-12 20:19:11.542 Main::Registering HttpStatus Extension
2008-11-12 20:19:11.543 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-11-12 20:19:11.544 Enabled verbose msgs:  important general
2008-11-12 20:19:11.550 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-11-12 20:19:13.300 Reschedule requested for id -1.
2008-11-12 20:19:13.341 Scheduled 1 items in 0.0 = 0.01 match + 0.03 place
2008-11-12 20:19:13.348 Seem to be woken up by USER
2008-11-12 20:19:20.332 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-11-12 20:19:21.075 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-11-12 20:19:24.050 MainServer::HandleAnnounce Monitor
2008-11-12 20:19:24.947 adding: oscar-desktop as a client (events: 0)
2008-11-12 20:19:24.948 MainServer::HandleAnnounce Monitor
2008-11-12 20:19:24.949 adding: oscar-desktop as a client (events: 1)
2008-11-12 20:19:24.952 Reschedule requested for id -1.
2008-11-12 20:19:24.977 Scheduled 1 items in 0.0 = 0.01 match + 0.01 place
2008-11-12 20:20:02.749 MainServer::HandleAnnounce Monitor
2008-11-12 20:20:02.752 adding: oscar-desktop as a client (events: 0)
2008-11-12 20:20:12.248 MainServer::HandleAnnounce Monitor
2008-11-12 20:20:12.252 adding: oscar-desktop as a client (events: 0)
2008-11-12 20:20:12.254 MainServer::HandleAnnounce Monitor
2008-11-12 20:20:12.255 adding: oscar-desktop as a client (events: 1)
2008-11-12 20:20:12.262 MainServer::HandleAnnounce Playback
2008-11-12 20:20:12.264 adding: oscar-desktop as a client (events: 0)
2008-11-12 20:20:12.289 TVRec(1): Changing from None to WatchingLiveTV
2008-11-12 20:20:12.295 TVRec(1): HW Tuner: 1->1
2008-11-12 20:20:13.451 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-11-12 20:20:13.459 MPEGRec(/dev/video0) Warning: Audio sample rate 32000 Hz
                        is not supported by ivtv driver, using 48000 Hz instead.
 *********************** WARNING ***********************
 ivtv drivers prior to 0.10.0 can cause lockups when    
 reading VBI. Drivers between 0.10.5 and 1.0.3+ do not  
 properly capture VBI data on PVR-250 and PVR-350 cards.

2008-11-12 20:20:30.283 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2008-11-12 20:20:34.470 TVRec(1): Changing from WatchingLiveTV to None
2008-11-12 20:20:34.818 Finished recording Agrodolce: channel 1043
2008-11-12 20:20:34.856 MainServer::HandleAnnounce Playback
2008-11-12 20:20:34.864 adding: oscar-desktop as a client (events: 0)
2008-11-12 20:20:34.868 TVRec(4): Changing from None to WatchingLiveTV
2008-11-12 20:20:34.875 TVRec(4): HW Tuner: 4->4
2008-11-12 20:20:36.547 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-11-12 20:20:36.986 Finished recording Unknown: channel 2006
2008-11-12 20:20:38.034 Finished recording Unknown: channel 2006
2008-11-12 20:20:38.076 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-11-12 20:20:38.230 Using runtime prefix = /usr
2008-11-12 20:20:38.233 Empty LocalHostName.
2008-11-12 20:20:38.234 Using localhost value of oscar-desktop
2008-11-12 20:20:38.249 New DB connection, total: 1
2008-11-12 20:20:38.257 Connected to database 'mythconverg' at host: localhost
2008-11-12 20:20:38.260 Closing DB connection named 'DBManager0'
2008-11-12 20:20:38.261 Connected to database 'mythconverg' at host: localhost
2008-11-12 20:20:38.266 New DB connection, total: 2
2008-11-12 20:20:38.272 Connected to database 'mythconverg' at host: localhost
2008-11-12 20:20:38.276 Current Schema Version: 1214
2008-11-12 20:20:38.312 Preview Error: Previewer file '/var/lib/mythtv/recordings/2006_20081112202035.mpg' is not valid.
2008-11-12 20:20:38.315 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/2006_20081112202035.mpg'
2008-11-12 20:20:38.331 Preview Error: Preview process not ok.
                        fileinfo(/var/lib/mythtv/recordings/2006_20081112202035.mpg.png) exists: 0 readable: 0 size: 0
2008-11-12 20:21:05.624 Error: offset>181, pes length & current can not be queried
2008-11-12 20:21:07.130 TVRec(4): HW Tuner: 4->4
2008-11-12 20:21:08.181 Finished recording Unknown: channel 2006
2008-11-12 20:21:08.318 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-11-12 20:21:08.372 Using runtime prefix = /usr
2008-11-12 20:21:08.385 Empty LocalHostName.
2008-11-12 20:21:08.387 Using localhost value of oscar-desktop
2008-11-12 20:21:08.395 DTVSM(0) Error: Wrong PMT; pmt->pn(101) desired(4)
2008-11-12 20:21:08.401 New DB connection, total: 1
2008-11-12 20:21:08.406 DTVSM(0) Error: Wrong PMT; pmt->pn(102) desired(4)
2008-11-12 20:21:08.414 Connected to database 'mythconverg' at host: localhost
2008-11-12 20:21:08.436 DTVSM(0) Error: Wrong PMT; pmt->pn(103) desired(4)
2008-11-12 20:21:08.449 Closing DB connection named 'DBManager0'
2008-11-12 20:21:08.452 DTVSM(0) Error: Wrong PMT; pmt->pn(104) desired(4)
2008-11-12 20:21:08.457 Connected to database 'mythconverg' at host: localhost
2008-11-12 20:21:08.460 DTVSM(0) Error: Wrong PMT; pmt->pn(105) desired(4)
2008-11-12 20:21:08.466 New DB connection, total: 2
2008-11-12 20:21:08.471 DTVSM(0) Error: Wrong PMT; pmt->pn(106) desired(4)
2008-11-12 20:21:08.480 DTVSM(0) Error: Wrong PMT; pmt->pn(107) desired(4)
2008-11-12 20:21:08.476 Connected to database 'mythconverg' at host: localhost
2008-11-12 20:21:08.484 DTVSM(0) Error: Wrong PMT; pmt->pn(132) desired(4)
2008-11-12 20:21:08.489 Current Schema Version: 1214
2008-11-12 20:21:08.493 TVRec(4): Changing from WatchingLiveTV to None
2008-11-12 20:21:08.496 DTVSM(0) Error: Wrong PMT; pmt->pn(133) desired(4)
2008-11-12 20:21:08.512 DTVSM(0) Error: Wrong PMT; pmt->pn(12) desired(4)
2008-11-12 20:21:08.516 DTVSM(0) Error: Wrong PMT; pmt->pn(13) desired(4)
2008-11-12 20:21:08.534 DTVSM(0) Error: Wrong PMT; pmt->pn(8015) desired(4)
2008-11-12 20:21:08.536 DTVSM(0) Error: Wrong PMT; pmt->pn(3) desired(4)
2008-11-12 20:21:08.540 DTVSM(0) Error: Wrong PMT; pmt->pn(5) desired(4)
2008-11-12 20:21:08.544 DTVSM(0) Error: Wrong PMT; pmt->pn(6) desired(4)
2008-11-12 20:21:08.548 DTVSM(0) Error: Wrong PMT; pmt->pn(1) desired(4)
2008-11-12 20:21:08.555 DTVSM(0) Error: Wrong PMT; pmt->pn(2) desired(4)
2008-11-12 20:21:08.542 Something went terribly wrong in PMT parsing when looking at program info
(a lot of repeated lines...)
2008-11-12 20:21:08.602 Finished recording Unknown: channel 2004
2008-11-12 20:21:14.274 Tuning to 'MPEG Program 1' pnum: 0x1 without CRC check on PMT
2008-11-12 20:21:20.004 mpegts_read_header: could not find any PMT's
2008-11-12 20:21:20.007 AFD Error: avformat err(-1) on av_open_input_file call.
2008-11-12 20:21:20.011 Couldn't open decoder for: /var/lib/mythtv/recordings/2006_20081112202036.mpg
2008-11-12 20:21:20.016 NVP, Error: Could not open file for preview.
2008-11-12 20:21:20.049 Preview Error: Run() file not local: '/var/lib/mythtv/recordings/2006_20081112202036.mpg'
2008-11-12 20:21:20.065 Preview Error: Preview process not ok.
                        fileinfo(/var/lib/mythtv/recordings/2006_20081112202036.mpg.png) exists: 0 readable: 0 size: 0

And so on.

I tried to upgrade firmware to dvb-usb-dib0700-1.20.fw (using a link with the old .10 name);
I tried configuring the card to not use the EIT active scanning, to open it on demand, ad up to 200 ms of tuning delay;
I tried with options dvb-usb disable_rc_polling=1 and usbcore autosuspend=-1

Nothing of that helped.

I'll appreciate any suggestions.

Thanks

Giulio

---

### Post by SiHa on 2008-11-13
The NovaT-500 should work OOB, apart form the LNA activation thing, which you've already done.

You say you installed Ubuntu then **Mythbuntu**? Not sure that's the way to go, or do you mean Ubuntu then **MythTV**?

Why not just install Mythbuntu clean? I have the above card and 8.04 in my BE/FE, and it installed flawlessley. The remote is another story, but the card itself should just work.

I would suggest grabbing the iso for Mythbuntu 8.04.1 here:
[http://mythbuntu.org/download/?file=mythbuntu-8.04.1-desktop-i386.iso](http://mythbuntu.org/download/?file=mythbuntu-8.04.1-desktop-i386.iso)
and trying that, accepting all the defaults.

---

### Post by extasy on 2008-11-13
I don't think T-500 would work oob in 8.04. How ever in 8.10 it should work better.

Here is a guide to follow to get it to work.

[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI]("http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI")


Good luck! Ps. I'm still on fw 1.10 not 1.20, it gave me problem.

---

### Post by SiHa on 2008-11-14
> **extasy said:**
> I don't think T-500 would work oob in 8.04. 
Well, it did for me, apart from the aforementioned LNA activation being required (which it still is under 8.10), and some remote niggles.
My point is that Scanning / Tuning / Watching all worked without intervention, when installing this card on a vanilla Mythbuntu 8.04 install.

Yes, I've added all the other bits mentioned like tuning delay, no Active EIT and open card on demand 'just in case' but it worked fine without.

Anyway, my twopenceworth.

SiHa

---

### Post by oscar69 on 2008-11-14
Extasy, thanks for link but I know it, and I tested it them all...

SiHa, I tried (with another hd) to install from scratch it all, but the problem is the same.

I'll investigate about signal strength, the only thing I not tested before.

I'll back with news.

Thanks all!

Giulio

---

### Post by oscar69 on 2008-11-15
No good news :(

To test both the card and the signal, I installed XP and the tv program that was within the card box. It works, and say something like good quality signal.

I tried to upgrade all to 8.10 (via update manager), but nothing changed.

Last try that I can imagine by myself is to reinstall from scratch mythbuntu 8.10.

I didn't say: my hw is amd-based (and iso selected according to it). But I think that it isn't the matter.

Some test/debug I can do??

Thanks

Giulio

---

### Post by oscar69 on 2008-11-16
I'm trying to install Mythbuntu 8.10.

I can find the PVR-500 (both analog & MPEG2) but cannot find the Nova T-500:
I select in Card Type the "DVB DTV capture card (v3.x)" but the DVB Device Number is blank and the Fronted ID say:"Could not get card info for card #0 su....(other is out of the screen)".

I've also found:
2008-11-16 11:52:15.512 Can't open DVB frontend (/dev/dvb/adapter0/frontend0).
2008-11-16 11:52:15.514 DiSEqCDevTree, Warning: No device tree for cardid 0
2008-11-16 11:52:32.537 Couldn't get handle
                        eno: No such file or directory (2)

Can this help to undestand something?

Thanks

Giulio

---

### Post by SiHa on 2008-11-16
My BE has a single Win NovaT and a NovaT-500. When installing, I found I first had to install the -500 with nothing in the other PCI slot. Then, after setting up this card, I powered down and added the single-tuner card which was then detected OK.
If trying to setup with both cards in, it sees neither, with the same "could not get card info..." error. 
I don't know for sure what causes this behaviour - I assume it's some sort of IRQ conflict or something like that, but installing one at a time fixed it.

---

### Post by oscar69 on 2008-11-16
Ok, I reinstalled all from scratch, 8.10 mythbubtu, with just Nova T-500 inserted.

The problem is the same.

Log say:

Can't open DVB frontend (/dev/dvb/adapter0/frontend0).
DiSEqCDevTree, Warning: No device tree for card id 0

but looking for it, there is:

#ls -la /dev/dvb/adapter0
total 0
drwxr-xr-x 2 root root     120 2008-11-16 23:55 .
drwxr-xr-x 2 root root      80 2008-11-16 23:55 ..
crw-rw---- 1 root video 212, 4 2008-11-16 23:55 demux0
crw-rw---- 1 root video 212, 5 2008-11-16 23:55 dvr0
crw-rw---- 1 root video 212, 3 2008-11-16 23:55 frontend0
crw-rw---- 1 root video 212, 7 2008-11-16 23:55 net0

I can register the card, it's stored as "[DVB: -1]".
After reboot, I can correct it: the frontend ID is "DiBcom 3000MC/P Subtype: DVB-T" and can point to 2 device number.

So I can scan for channels, it founds, as usual, but trying to see live video I got the error.

What else can I do ? :confused: 

Thanks 

Giulio

---

### Post by oscar69 on 2008-11-17
I found on [http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards](http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards) : "PCI 2.2 card using 3.3V. Failed to run on PCI 2.1 system". 

What exactly does it mean? 

How I can check if I'm using PCI 2.1 or 2.2 ???

My mobo is Gigabyte GA-M56S-S3 ([manual]("http://america.giga-byte.com/FileList/Manual/motherboard_manual_ga-m56s-s3_e.pdf")).

Thanks

Giulio

---

### Post by oscar69 on 2008-11-17
Today's news, good news.

I followed [this guide]("http://www.linuxtv.org/wiki/index.php/Testing_your_DVB_device") and I found that... it works.

So, I can say that the card is good, the signal is good enought, the firmware and everything else is ok, but... the Mythtv/Mythbuntu problem persist.

In sintesis, I did:

apt-get install dvb-utils
scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/it-Roma > /home/oscar/.tzap/channels.conf
tzap -r -c /home/oscar/.tzap/channels.conf  "RaiUno" &
mplayer /dev/dvb/adapter0/dvr0

Now, what kind of test I can do with Mythtv?

Thanks

Giulio

---

