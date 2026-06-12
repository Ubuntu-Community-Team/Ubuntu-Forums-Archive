---
title: "[SOLVED] Mythmusic Crashes to Desktop"
date: 2008-06-20
forum: Mythbuntu
---

### Post by DrewMac on 2008-06-20
I have a brand new MythTV box set up with mythbuntu 8.04. Everything works great.. but mythmusic. If I go Media Library > Listen to Music, I will find myself at the Desktop. For some reason, it crashes right out. No other plugins do this.

_System Specs_
> - Asus P5Kc Motherboard
- P4 3.0GHz w/ HT
- 2GB RAM
- nVidia GeForce 8400 GS
- Twinhan 1020A DVB-S Satellite Card
- WD 7200RPM 320GB HDD
- LG SuperMulti DVD Writer

_Mythfrontend.log_
> Starting mythfrontend.real..
2008-06-20 23:48:20.321 New DB connection, total: 2
2008-06-20 23:48:20.321 Connected to database 'mythconverg' at host: localhost
2008-06-20 23:48:20.325 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-06-20 23:48:20.325 Enabled verbose msgs:  important general
2008-06-20 23:48:20.488 Unable to parse themeinfo.xml for glass-wide
2008-06-20 23:48:20.488 The theme (glass-wide) is missing a themeinfo.xml file
2008-06-20 23:48:20.685 Unable to parse themeinfo.xml for glass-wide
2008-06-20 23:48:20.685 The theme (glass-wide) is missing a themeinfo.xml file
2008-06-20 23:48:20.964 Primary screen 0.
2008-06-20 23:48:20.965 Using screen 0, 1024x768 at 0,0
2008-06-20 23:48:20.967 Switching to square mode (Mythbuntu-8.04)
2008-06-20 23:48:20.988 Using the Qt painter
2008-06-20 23:48:20.989 JoystickMenuClient Error: Joystick disabled - Failed to read /home/htpc/.mythtv/joystickmenurc
2008-06-20 23:48:20.990 lirc init success using configuration file: /home/htpc/.mythtv/lircrc
2008-06-20 23:48:22.134 Specified base font 'medium' does not exist for font clock
2008-06-20 23:48:22.134 Specified base font 'medium' does not exist for font small
2008-06-20 23:48:22.134 Specified base font 'medium' does not exist for font medium
2008-06-20 23:48:22.136 Specified base font 'medium' does not exist for font large
2008-06-20 23:48:22.138 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-06-20 23:48:22.271 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-06-20 23:48:22.346 Registering Internal as a media playback plugin.
2008-06-20 23:48:22.440 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-06-20 23:48:22.511 Failed to run 'cdrecord --scanbus'
2008-06-20 23:48:22.514 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-06-20 23:48:22.521 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-06-20 23:48:22.564 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)

_Mythbackend.log_
> 2008-06-20 23:46:03.321 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-06-20 23:46:51.653 Reschedule requested for id -1.
2008-06-20 23:46:51.797 Scheduled 0 items in 0.1 = 0.11 match + 0.03 place
2008-06-20 23:49:51.799 DVBChan(1:1) Warning: Unsupported fec_inner parameter.
2008-06-20 23:49:52.461 DVBSM(1), Warning: Can not measure Bit Error Rate
			eno: Operation not supported (95)
2008-06-20 23:49:52.573 DVBSM(1), Warning: Can not count Uncorrected Blocks
			eno: Operation not supported (95)
2008-06-20 23:49:52.982 DTVSM(1) Error: Wrong PMT; pmt->pn(821) desired(800)
2008-06-20 23:49:53.077 DTVSM(1) Error: Wrong PMT; pmt->pn(886) desired(800)
2008-06-20 23:50:04.285 MainServer::HandleAnnounce Monitor
2008-06-20 23:50:04.708 adding: HTPC-MythTV as a client (events: 0)

I believe the problem is more to do with the frontend because the backend log doesn't seem to even say anything that pertains to mythmusic.

---

### Post by DrewMac on 2008-06-21
Weird.. the problem just fixed itself. While I was in mythweb, I was that it had a new option to be able to view my music library. I clicked the button and my library came up. Then I decided to try it on my MythTV box, and what do you know! Mythmusic fired up perfectly!

---

### Post by Marsupilami23 on 2008-07-19
I had the same problem, found out that cdrecord was not installed.

---

