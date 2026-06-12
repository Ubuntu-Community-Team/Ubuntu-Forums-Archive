---
title: "REcord/Playback Speed Problem"
date: 2008-09-28
forum: Mythbuntu
---

### Post by Ronno6 on 2008-09-28
Yesterday I recorded 6 episodes of the same show in a row. Same settings for all recordings. Yet, the 5th one plays back at about 4x the normal speed. File size for this episode is off, but just a bit, from normal 770mb range down to 738mb. Pressing "A" during playback allows reduction to .5x, which is still about double normal speed. 

I have had this happen on random recordings in the past.
What should I check?

Dell Optiplex GX370
Pentium4 2.8g
2g ram
Dvico Fusion HDTV5 RT Gold
PNY 6200GX 256mb

---

### Post by Ronno6 on 2008-09-28
This one has me baffled, but that is nothing new. Does anyone have any ideas? 
Will there be a way to salvage this file?

---

### Post by newlinux on 2008-09-28
what happens when you play the file outside with myth (like with mplayer)?

---

### Post by Ronno6 on 2008-09-29
No difference when using mplayer. Speed is fast,audio is choppy. Seems to be jumping frames . 
The video DOES play at normal speed when on the Media Library > Watch Recordings menu. The thumbnail preview screen plays the vid at normal speed, but there is no audio. Could the audio stream be causing this? Is the audio data available, viewable, and correctable for these recordings? Once again, all settings were the same for all recordings.

---

### Post by Ronno6 on 2008-09-30
I really need to get a grip on this problem, as I cannot rely on Muthbuntu to render consistent recording results unless I can figure it out. Is there information I need to furnish in order to adequately diagnose what is happening?

---

### Post by newlinux on 2008-09-30
Tell what recording profile you are using give us your frontend log from the time you are playing a recording that doesn't work well... You might want to turn up the verbosity by doing ```
mythfrontend -v playback
``` option.

---

### Post by Ronno6 on 2008-09-30
For recording profile I'm using the High Quality profile set to Lossless Transcoding.


here's the log:
Starting mythfrontend.real..
2008-09-30 10:41:57.731 New DB connection, total: 2
2008-09-30 10:41:57.731 Connected to database 'mythconverg' at host: localhost
2008-09-30 10:41:57.735 mythfrontend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-09-30 10:41:57.735 Enabled verbose msgs:  important general
2008-09-30 10:41:57.833 Unable to parse themeinfo.xml for glass-wide
2008-09-30 10:41:57.834 The theme (glass-wide) is missing a themeinfo.xml file
2008-09-30 10:41:57.998 Unable to parse themeinfo.xml for glass-wide
2008-09-30 10:41:57.998 The theme (glass-wide) is missing a themeinfo.xml file
2008-09-30 10:41:58.264 No theme dir: /home/ronno6/.mythtv/themes/blootube-wide
2008-09-30 10:41:58.265 Primary screen 0.
2008-09-30 10:41:58.266 Using screen 0, 1280x720 at 0,0
2008-09-30 10:41:58.268 No theme dir: /home/ronno6/.mythtv/themes/blootube-wide
2008-09-30 10:41:58.269 Switching to wide mode (blootube-wide)
2008-09-30 10:41:58.287 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-09-30 10:41:58.287 lirc_init failed for mythtv, see preceding messages
2008-09-30 10:41:58.287 JoystickMenuClient Error: Joystick disabled - Failed to read /home/ronno6/.mythtv/joystickmenurc
2008-09-30 10:42:00.389 Specified base font 'medium' does not exist for font clock
2008-09-30 10:42:00.407 Specified base font 'medium' does not exist for font small
2008-09-30 10:42:00.407 Specified base font 'medium' does not exist for font medium
2008-09-30 10:42:00.408 Specified base font 'medium' does not exist for font large
2008-09-30 10:42:00.409 Loading from: /usr/share/mythtv/themes/blootube-wide/base.xml
2008-09-30 10:42:00.459 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-09-30 10:42:00.512 Registering Internal as a media playback plugin.
2008-09-30 10:42:00.701 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-09-30 10:42:00.751 Failed to run 'cdrecord --scanbus'
2008-09-30 10:42:00.754 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-09-30 10:42:00.756 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-09-30 10:42:00.794 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.1.102:5060 NAT address 192.168.1.102
SIP: Cannot register; proxy, username or password not set
2008-09-30 10:42:00.921 No theme dir: /home/ronno6/.mythtv/themes/blootube-wide
2008-09-30 10:42:08.392 XMLParse::LoadTheme using /usr/share/mythtv/themes/blootube-wide/ui.xml
2008-09-30 10:42:08.493 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-09-30 10:42:08.494 Using protocol version 40
2008-09-30 10:42:14.235 TV: Attempting to change from None to WatchingPreRecorded
2008-09-30 10:42:14.251 DPMS Deactivated 
2008-09-30 10:42:14.550 Opening audio device 'default'. ch 2(2) sr 48000
2008-09-30 10:42:14.550 Opening ALSA audio device 'default'.
2008-09-30 10:42:14.594 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-09-30 10:42:14.636 OSD Theme Dimensions W: 640 H: 480
2008-09-30 10:42:15.062 TV: Changing from None to WatchingPreRecorded
2008-09-30 10:42:15.067 Realtime priority would require SUID as root.
2008-09-30 10:42:15.162 Video timing method: USleep with busy wait
2008-09-30 10:43:58.609 TV: Attempting to change from WatchingPreRecorded to None
2008-09-30 10:43:58.750 TV: Changing from WatchingPreRecorded to None
2008-09-30 10:43:58.819 DPMS Reactivated.

In review, this particular recording is only 738mb; the others are 770mb. I fear that the difference is lost audio, although I cant understand why the 5th out of a series of 6 recordings is different. 
Thanks for your assistance.

---

### Post by Ronno6 on 2008-09-30
These recordings were all made on Saturday the 27th.
I see a series of 4 log lines from Sunday the 28th that read:

NVP::AddAudioData(): pl:Audio buffer overflow, audio data lost!

That looks suspicious. Any idea as for cause? How about prevention in the future?

Thanks again.

---

### Post by Ronno6 on 2008-10-01
Does the log provide any clue? Is there more info required? 
Any thoughts about the buffer overrun,audio data lost message from the day after recording?

Thanks, again.

---

### Post by bbuck2002 on 2008-10-26
Ronno6, did you ever resolve your random recording issue?  Do you have any additional information regarding your setup?

The scenario I have is the same as yours, randomly a recording plays at 4X speed.  I am using pcHDTV 5500 tuners as both digital for HDTV and analog for cable, and only the analog recordings are affected.  It does seem that about 1 out of every 5 or 6 analog recordings are affected.

---

### Post by napsilan on 2008-10-29
I am having the same problem here.  ~1/10 recordings are at double speed.  Playing then back at half speed doesn't help since the problem appears to be missing frames and audio data. Haven't tried any other players besides myth.  

PCHDTV 5500, recording sound from card (not the audio patch cable)
ubuntu hardy
kernel 2.6.24-19-generic
libmyth-0.21-0     0.21.0+fixes18207-0ubuntu4~hardy1 
mythtv-backend     0.21.0+fixes18207-0ubuntu4~hardy1 
happens with both rtjpeg and mpeg4 encoding

---

### Post by Ronno6 on 2008-10-30
Nope. Check your logs for the audio buffer overflow indication. As the video plays properly in the preview box (no audio) I believe the problem to be in that area. But there has been no suggestions as to the cause, or resolution of this issue. If you find one,please let me know. Maybe this needs to be submitted as a bug?
Pardon the delay-I've been on vacation. 

Thanks.

---

### Post by Valen00 on 2008-10-30
just as something to try, 
go into the playback settings and tick "use video as timebase"
it might help 
possibly.

---

### Post by napsilan on 2008-10-30
"use video as timebase" will not correct already corrupted recordings.  I'll come back in a day or two and see if any new recordings are corrupted after enabling it.


edit: still getting new corrupted recordings (RIP good eats)

---

### Post by Ronno6 on 2008-10-30
I don't believe that the corrupted files can be corrected; not if the "audio data is lost" is the root cause of the playback issues, as I believe.The file size of the "corrupted" program is 738mb vs. 770mb for other, normal recordings of the same series.What I also think is odd is the fact that the "audio buffer overflow" message didn't appear in the logs till the next day. Maybe that showed after I attempted playback? Did playback cause that problem? I just wish I knew. I have the audio buffer increased, or expanded, whichever is the term. I am not using aggressive buffering, as I have read that causes problems. I would be happy to post any settings that might help, but they were the same for all programs recorded at that time, and only 1 show had a problem. I have not had the problem since, but have not used Mythbuntu for any critical recordings since the problem occurred,as I cannot be sure I will get the recording I desire without issue.

---

### Post by thebitpit on 2008-11-11
:lolflag:This is just a shot from the hip! Which file system are you using to hold the recordings? I recall that some file systems such as reiser are great for lots of small files, but prone to error with the gigantic files created by HDTV data streams. I use jfs and have never seen the speed problem.

My setup is odd in that my tuners are in an old box as they use PCI bus cards. The video files, database, and frontend are in a faster new box using PCIe bus for the video card. Once, as a test, I started the old box first and it failed to mount the video file directory since the new box was not yet running. It wrote the data to files on the old box, as expected, on a reiser file system. I use mythtv release .21 file pools so all the data was accessible by the frontend. Playback was too choppy to watch.:(

---

### Post by Ronno6 on 2008-11-13
Thanks for the reply. I am clueless as to the file system in use, just whatever the default file system in Mythbuntu. How do I determine??

BTW- the program is not HD. Recorded from analog cable, 5th show in a continuous series of 6 broadcasts.

---

### Post by dmfrey on 2008-11-14
I noticed that this was happening and couldn't figure out what may be causing it.  Originally, I was thinking it was related to loss of signal or two recorders recording at the same time.  I came across a recording doing this and still had the logs from that night.  What I noticed is that it also was updating it listing information at the same time.  I have actually confirmed this on two recordings on two separate days.  Always, the listings are being updated.

Can someone check and confirm if their listings are downloading at the same time these shows with errors are recording?

Thanks.

---

### Post by dmartin on 2008-11-18
I also have a PCHDTV5500 and have the same exact problem you've all described.  This has to be something wrong with the v4l-dvb driver for the 5500.  I don't think that it has anything to do with the filesystem, concurrent downloading, or anything of that sort, because I have other tuners recording on the same rig to the same filesystem without any problems.

---

### Post by novellahub on 2008-11-18
I had the same issue with a Leadtek Winfast TV2000XP card.  The issue seemed to occur on the second recording on consecutive recordings.  The first recording would be done and the commercial flagging process was running against it.  Then the next recording would have the speed up issue for the first one or two mintues. Then it would be fine after that.

I since removed the TV card and not had a issue ever since then.  This seems to be a issue with v4l analog tuners.

---

### Post by Ronno6 on 2008-11-18
I had wondered if flagging commercials on a prior recording caused this problem, but , as I recorded 6 in a row with only recording #5 having the problem, I discounted this as the root cause. 
Likewise, I never updated the schedule automatically, so that was not the cause either. 
Anyway, as my Mythbuntu machine is now exhibiting other problems (hang-ups while scrolling through schedules, balky live television watching, and inability to switch tuners ) I believe that Myth and I will go our separate ways. I guess I'll spring for the VideoRedo program to edit and record shows to DVD that I recorded from SageTV. That seems to be *reliable*.

Good luck to all.

---

### Post by dmfrey on 2008-11-18
I still think there may be an issue with syncing the listings.  I have seen it max out my one of my processors when it is occurring.  In a dual core machine (AMD64 5400+) and it is recording on two tuners and trying to sync its listings.  The recordings (one firewire, one pvr-150) don't come anywhere near maxing out both cores.

---

### Post by Ronno6 on 2008-11-18
Have you guys checked your backend logs to see if the audio buffer overflow problem is indicated? Do your file sizes differ from other similar recordings?I believe the overflow resulting in lost audio data is the cause, but have never received any guidance on that issue.
BTW- I'm using a Dvico Fusion 5HD Gold, not the 5500 card you mentioned.

---

### Post by dmartin on 2008-11-19
This happened to me tonight, so I checked my logs.  My mythbackend.log shows nothing interesting at all.  However, dmesg has a big relevant section:
```
[ 3748.498979] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.499000] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.499007] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.499022] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509551] cx88[0]: irq aud [0x1101] dn_risci1* dnf_of dn_sync*
[ 3748.509567] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509572] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509583] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509588] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509593] cx88[0]: irq aud [0x1000] dn_sync*
[ 3748.509597] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509603] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509609] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509614] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509620] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509625] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509630] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509636] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509642] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509648] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509653] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509658] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509667] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509672] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509678] cx88[0]: irq aud [0x1000] dn_sync*
[ 3748.509682] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509688] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509694] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509699] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509705] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509710] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509716] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509722] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509727] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509733] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509738] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509744] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509750] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509755] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509761] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509766] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509773] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509779] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509784] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509790] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509796] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509802] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509808] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509813] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509819] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509824] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509830] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509837] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509842] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509848] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509854] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509860] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509865] cx88[0]: irq aud [0x1000] dn_sync*
[ 3748.509870] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509876] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509881] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509887] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509893] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509897] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509904] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509909] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509915] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509921] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509926] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509932] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509937] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509943] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509946] cx88[0]/1: IRQ loop detected, disabling interrupts
[ 3748.509968] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509974] cx88[0]: irq aud [0x1000] dn_sync*
[ 3748.509979] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509984] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.509990] cx88[0]: irq aud [0x1000] dn_sync*
[ 3748.509995] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510001] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510007] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510013] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510019] cx88[0]: irq aud [0x1000] dn_sync*
[ 3748.510024] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510030] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510036] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510042] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510048] cx88[0]: irq aud [0x1000] dn_sync*
[ 3748.510052] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510058] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510065] cx88[0]: irq aud [0x1000] dn_sync*
[ 3748.510077] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510082] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510088] cx88[0]: irq aud [0x1000] dn_sync*
[ 3748.510097] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510103] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510108] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510115] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510120] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510126] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510132] cx88[0]: irq aud [0x1000] dn_sync*
[ 3748.510136] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510142] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510148] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510153] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510159] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510164] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510170] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510176] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510181] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510187] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510192] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.510196] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
[ 3748.561706] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*

```

---

### Post by Ronno6 on 2008-11-19
It has been so long now that I can't recall if my problem showed up in the frontend or backend log. 
When selecting the recording to view from your list of recordings, does the video play normally in the thumbnail view? 
Yours may be a different problem.

---

### Post by jnorth on 2009-02-01
I'm yet another person with the same issue.

Symptoms:

[LIST]
[*]"Fast-forward" like playback in livetv and recordings
[*]Affects only items on the analog channels
[*]Random appearance.  Sometimes on a lone recording, sometimes on consecutive, first, or last, etc.  Different times, without concurrent recordings or other activities (i.e. syncs or data transfers).
[*]When video alone is viewed (i.e. in either the Watch Recordings thumbnail preview or in the mythweb flash player) the video is at normal speed with all frames.
[/LIST]
Troubleshooting info:

[LIST]
[*]PCHDTV 5500 card (only card)
[*]Dedicated backend (no audio or other cards to conflict with)
[*]Some log snippets below:
[/LIST]
Dmesg/syslog during recordings where the issue manifests has a block of these errors, normal recordings do not.```
Jan 31 22:00:03 mc01 kernel: [455146.252566] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
Jan 31 22:00:03 mc01 kernel: [455146.252572] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
Jan 31 22:00:03 mc01 kernel: [455146.263155] cx88[0]: irq aud [0x1101] dn_risci1* dnf_of dn_sync*
Jan 31 22:00:03 mc01 kernel: [455146.263171] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
Jan 31 22:00:03 mc01 kernel: [455146.263357] cx88[0]: irq aud [0x1000] dn_sync*
Jan 31 22:00:03 mc01 kernel: [455146.263477] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*
Jan 31 22:00:03 mc01 kernel: [455146.263480] cx88[0]/1: IRQ loop detected, disabling interrupts
Jan 31 22:00:03 mc01 kernel: [455146.300291] cx88[0]: irq aud [0x1001] dn_risci1* dn_sync*

```Backend log from recording start - the only error I can see that looks odd is the line "strange error flushing buffer" - but here is the log...```
2009-01-31 22:00:02.801 MainServer::HandleAnnounce Monitor
2009-01-31 22:00:03.234 adding: mc01.atl02.point808.com as a client (events: 0)
2009-01-31 22:00:03.231 TVRec(3): Changing from None to RecordingOnly
2009-01-31 22:00:03.364 TVRec(3): HW Tuner: 3->3
2009-01-31 22:00:03.351 Using runtime prefix = /usr
2009-01-31 22:00:03.405 Empty LocalHostName.
2009-01-31 22:00:03.424 Using localhost value of mc01.atl02.point808.com
2009-01-31 22:00:03.473 New DB connection, total: 1
2009-01-31 22:00:03.479 Connected to database 'mythconverg' at host: mc01.atl02.point808.com
2009-01-31 22:00:03.481 Closing DB connection named 'DBManager0'
2009-01-31 22:00:03.483 Connected to database 'mythconverg' at host: mc01.atl02.point808.com
2009-01-31 22:00:03.487 New DB connection, total: 2
2009-01-31 22:00:03.496 Connected to database 'mythconverg' at host: mc01.atl02.point808.com
2009-01-31 22:00:03.500 Current Schema Version: 1214
2009-01-31 22:00:03.579 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-31 22:00:03.621 Started recording: CSI: Miami "Body Count": channel 1038 on cardid 3, sourceid 1
strange error flushing buffer ... 
2009-01-31 22:00:03.627 scheduler: Last message repeated 1 times: Finished recording: NCIS "Recoil": channel 2461
2009-01-31 22:00:03.644 scheduler: Started recording: CSI: Miami "Body Count": channel 1038 on cardid 3, sourceid 1
2009-01-31 22:00:04.596 MainServer::HandleAnnounce Monitor
2009-01-31 22:00:04.602 adding: mc02.atl02.point808.com as a client (events: 0)
2009-01-31 22:00:04.676 Reschedule requested for id 0.
2009-01-31 22:00:07.486 AFD: Opened codec 0x907b9b0, id(MPEG2VIDEO) type(Video)
2009-01-31 22:00:07.492 AFD: codec AC3 has 6 channels
2009-01-31 22:00:07.522 AFD: Opened codec 0x907bfa0, id(AC3) type(Audio)
2009-01-31 22:00:07.852 Scheduled 357 items in 3.2 = 0.00 match + 3.17 place
2009-01-31 22:00:07.859 scheduler: Scheduled items: Scheduled 357 items in 3.2 = 0.00 match + 3.17 place
2009-01-31 22:00:08.748 Preview: Grabbed preview '/media/slot4/MythTV/Recordings/2461_20090131210000.mpg' 1920x1088@64s

```My frontend has absolutely no errors when I try to watch one of these malfunctioning recordings.

I'll do whatever it takes to get more info or try to troubleshoot this if anyone has any ideas.

Oh - system specs, my backend is a little old, but it does HD perfectly so I don't see how it would be the cause.  Plus, it recorded analog just fine using another tuner cardin the past.

mc01 - Master backend (Recording + NFS fileserver)

[LIST]
[*]AMD Athlon(tm) 64 Processor 3000+
[*]2G DDR2 SDRAM
[*]1 TB SATA JBOD array (Recordings/LiveTV)
[*]1 TB SATA LVM Raid 1 array (Movies/Music/Pictures/Backup)
[*]100 SATA GB Raid 1 array (OS/Misc)
[*]PCHDTV 5500
[/LIST]
mc02 - Frontend, slave backend (Theater + flagging + mythweb + transmission client)

[LIST]
[*]Apple Mac Mini Core Duo 1.66
[*]1.66 GHz Intel Core Duo (T2300)
[*]2G DDR2 SDRAM
[*]5400 RPM 80 GB SATA (OS/Misc)
[*]Intel GMA950, 64 MB shared DDR2 SDRAM
[*]250 GB Firewire disk (Backup)
[*]DVI->HDMI->LG 42" Plasma (Video)
[*]Mini TOSLink->Media converter->Digital coaxial->5.1 speaker system(Audio)
[*]Plextor ConvertX TV402U-NA
[/LIST]

---

### Post by Ronno6 on 2009-02-01
Geez, I'd written this thread off a while ago. 

That "strange error flushing buffer" seems to be the culprit.Searches have indicated that this of no importance, calling it a LAME (the MP3 encoder) complaint for some "obscure reason." Maybe an "obscure," but it sure messes things up.I have another thread addressing this message, but have had no responses. 

I've seen another log entry that indicates a buffer overflow error, with audio data lost. If you look at the sizes of the afflicted recordings, they will be smaller than similar length recordings that do not have the problem. As Myth syncs the video with the audio (some of which is missing,) it is choppy and faster speed.
that is why the thumbnail video plays at normal speed-there is  no audio with which to sync. 
  
What I cannot come to grips with is the apparent randomness of this problem. If it was continuous, more frequent,or even statistically predictable, it certainly would be easier to troubleshoot.If there were some settings amiss, one would think the problem to be prevalent.I guess this is why nobody seems to have a clue.
 
I got 8 out of 9 recordings perfectly in a consecutive series last week, but one was amiss. This is unacceptable for dependability reasons, and I have reverted to SageTV and an testing VideoReDo as means to the end.Cost $$$$, sure, but they WORK !

---

### Post by jnorth on 2009-02-01
Ditto that about the randomness.  I can find nothing to tie it down.

QUestion for you though, I'm not that familiar with SageTV or Videoredo - are you using the same hardware for those as you did for mythtv?  Just wondering if i can completely eliminate the hardware as a potential source.

---

### Post by Ronno6 on 2009-02-02
The Sage/VideoReDo are loaded on another machine. 
My Mythbuntu machine is:

Dell Optiplex GX370
Pentium 4 2.8g
2g ram
Dvico Fusion HDTV5 RT Gold
PNY 6200GX 256mb

This machine is frontend and backend both. If you think your machine is old, mine is ancient. But, it works most of the time.

I do have a spare PC that is a clone of my HTPC which I could try, but that one has a Hauppauge 1600 tuner in it. There are those who have gotten that tuner to work, but I fear that that task would be beyond my meager capabilities. 

I am disappointed in the quality of the recordings I've made from analog cable,but that would be a topic for another thread.

Addendum: I thought that ## looked familiar. Seems that the 4 of you guys: jnorth, bbuck2002, napsilan, and dmartin are all using the PCHD TV 5500 tuner. Sounds like a common thread - for you 4 guys. I'm using the Dvico HDTV5 RT Gold. I wonder if those cards share some sort of glitch?? Anybody have input ??

---

### Post by bbuck2002 on 2009-02-22
I am not sure about the Dvico HDTV5 and how it would relate to the pcHDTV 5500, but I do know that this problem did not happen with analog recordings when I was using the Hauppauge PVR-250 cards.  I had to switch from these cards because my new server only supported 3.3V PCI-X, and the Hauppauge cards would only work in a 5.0V slot even though the card was keyed for both...

The issue for me is still occurring, in fact it appears to be happening more frequently since my last run of updates on the server.

jnorth, are you by chance running your 5500 in a 3.3V slot?  I assume most people would be using standard desktop hardware with 5V PCI slots, so I am trying to find things that are unique about our setups...  I can't imagine only our group has encountered this issue.

---

### Post by jnorth on 2009-02-22
Afraid not - it's in a regular 5v slot...

It's just the oddest thing.  I've used other tuners just fine.  For now, I've just added an old Plextor ConvertX USB capture device with a higher priority than the analog input of the 5500 so that it is used for 90% of my analog recordings, and my 5500 is used almost exclusively for digital - the only time I record analog on the 5500 is when I have overlapping programs in analog only, and then I just cross my fingers ;)

---

### Post by cnykerk on 2009-02-22
I am having the same issue.  I have two pchdtv 5500 cards that work fine in HD mode, but when one is set for analog, the analog recordings randomly have the choppy/fast forward playback issue.  All of the recording and playback sound rates are set to 48000 in mythtv. 


System specs:
Ubuntu 8.10
Nvidia 8400GS
GA-MA74GM-S2
AMD Athlon X2 BE-2300
4GB RAM

---

### Post by jnorth on 2009-02-22
OT - but dang dude - your box makes my setup look like crap ;)

---

### Post by Ronno6 on 2009-02-23
Snif,snif! I feel so all alone. All you guys are using the 5500 , and I'm the only one with the Dvico. 

  I,too, use the 48000 sampling rate, as that was required in order to get sound on digital broadcasts.

One would think that, as the numbers seem to keep growing, that this might qualify as a bug!?

I've  changed my recording profile( I can't remember to what, but it had been CPU+, then SLIM ) in order to get a better quality picture. But, I really haven't used Mythbuntu for recordings lately. I bit the bullet and purchased VideoReDo, and I'm suitably impressed. Burning DVD's is F-A-S-T !!

I'll keep an eye on this forum to see if any fix ever evolves. I hope one does.

---

### Post by mattsteven on 2009-03-06
I too have this problem, and I am using a Hauppage HVR-950.  My driver is the 2.6.28 kernel's built in em28xx.

The next time I notice a recording doing this, I will try to post more information from the kernel log.  It looks likely that it is an issue with several v4l drivers so it may be worthwhile to file a bug report with that project and reference this thread once people get enough information together.

---

### Post by Ronno6 on 2009-03-07
Maybe then someone can get a handle on the situation. The total randomness of the problem is what drives me crazy. 
Good luck with the bug reporting. I hope that gets it fixed.

---

### Post by mattsteven on 2009-03-26
No errors appear during the recording process.  They are only shown in the log once Commercial flagging starts.

A small sample follows.

So the problem seems to be that ffmpeg gets to these errors in the file and somewhere along the way the timing information gets damaged so that the rest of the recording plays at double speed, sounding like an episode of The Chipmunks.  You can play them back at half speed but of course the voices are up a few registers.

The next thing I'll try is disabling transcoding for recordings on that weaker channel.  That should give the frontend a chance to jump around the corrupted spots and play normally if it misses one.




```
2009-03-23 20:00:54.937 [mpeg2video @ 0xb732e028]invalid mb type in P Frame at 34 10
2009-03-23 20:00:54.938 [mpeg2video @ 0xb732e028]invalid mb type in P Frame at 62 11
2009-03-23 20:00:54.940 [mpeg2video @ 0xb732e028]ac-tex damaged at 21 12
2009-03-23 20:00:54.941 [mpeg2video @ 0xb732e028]invalid mb type in P Frame at 71 15
2009-03-23 20:00:54.943 [mpeg2video @ 0xb732e028]ac-tex damaged at 76 17
2009-03-23 20:00:54.945 [mpeg2video @ 0xb732e028]ac-tex damaged at 23 38
2009-03-23 20:00:54.947 [mpeg2video @ 0xb732e028]ac-tex damaged at 7 41
2009-03-23 20:00:54.948 [mpeg2video @ 0xb732e028]invalid cbp at 30 42
2009-03-23 20:00:54.949 [mpeg2video @ 0xb732e028]ac-tex damaged at 0 2
2009-03-23 20:00:54.950 [mpeg2video @ 0xb732e028]mb incr damaged
2009-03-23 20:00:54.951 [mpeg2video @ 0xb732e028]ac-tex damaged at 0 38
2009-03-23 20:00:54.952 [mpeg2video @ 0xb732e028]invalid mb type in P Frame at 2 42
2009-03-23 20:00:54.953 [mpeg2video @ 0xb732e028]ac-tex damaged at 0 43
2009-03-23 20:00:54.954 [mpeg2video @ 0xb732e028]ac-tex damaged at 2 44
2009-03-23 20:00:54.955 [mpeg2video @ 0xb732e028]Warning MVs not available
2009-03-23 20:00:54.996 [ac3 @ 0xb732e028]frame CRC mismatch
2
```

Finally, if anyone has pre-and-post encoding copies of a smallish video that demonstrates this problem, can you please submit a proper bug report to ffmpeg and update this thread?   I will try to do this once I get a recording that fails but it may take awhile.

[http://www.ffmpeg.org/bugreports.html](http://www.ffmpeg.org/bugreports.html)

---

### Post by FakeOutdoorsman on 2009-03-26
> **mattsteven said:**
> ...

Finally, if anyone has pre-and-post encoding copies of a smallish video that demonstrates this problem, can you please submit a proper bug report to ffmpeg and update this thread?   I will try to do this once I get a recording that fails but it may take awhile.

[http://www.ffmpeg.org/bugreports.html](http://www.ffmpeg.org/bugreports.html)
Do not submit a bug report unless you are using SVN FFmpeg or release 0.5.  Bug reports related to Ubuntu's ancient release of FFmpeg will be ignored.

---

### Post by Chunk of Earth on 2009-04-17
I had Mythbuntu configured with a Hauppauge HVR-1600 and a pcHDTV 5500 on a PCI bus and I was getting the recording problem on the pcHDTV card and the "IRQ Loop" error in the syslog. I eventually purchased another HVR-1600 and reconfigured the pcHDTV card for ATSC-only recording from an antennna which worked fairly well. I found new errors in syslog, though ...

```
Apr 11 20:10:02 atoz kernel: [31359.563955] cx88_wakeup: 3 buffers handled (should be 1)
```I believe these are due to IRQ handling issues, also.

You could check your IRQ routing with the command```
cat /proc/interrupts
```If you have a multi-core processor or mulitple processors and CPU0 is handling all your hardware interrupts then CPU0 could become overwhelmed with the task of interrupt handling.

You could try installing irqbalance to spread out the interrupt handling duty.```
sudo apt-get install irqbalance
```Restart your system and see if the interrupts are now being handled by your other cores or processors.```
cat /proc/interrupts
           CPU0       CPU1
  0:        403          0   IO-APIC-edge      timer
  1:          2          0   IO-APIC-edge      i8042
  3:          2          0   IO-APIC-edge
  4:         13          0   IO-APIC-edge      serial
  7:          0          0   IO-APIC-edge      parport0
  8:         55          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          4          0   IO-APIC-edge      i8042
 14:     158642          0   IO-APIC-edge      ata_piix
 15:    3291233          0   IO-APIC-edge      ata_piix
 16:    2017377          0   IO-APIC-fasteoi   uhci_hcd:usb2, uhci_hcd:usb5, nvidia
 17:    1112986          0   IO-APIC-fasteoi   cx18-0
 18:    1968518          0   IO-APIC-fasteoi   uhci_hcd:usb4, ata_piix, eth0
 19:        109     331757   IO-APIC-fasteoi   uhci_hcd:usb3, cx18-1
 21:          0          0   IO-APIC-fasteoi   cx88[0], cx88[0], cx88[0]
 22:      79463       7648   IO-APIC-fasteoi   EMU10K1
 23:          3          0   IO-APIC-fasteoi   ehci_hcd:usb1
NMI:          0          0   Non-maskable interrupts
LOC:   17932097   18400883   Local timer interrupts
RES:    3283541    8584802   Rescheduling interrupts
CAL:       1127       2735   function call interrupts
TLB:     133157     167543   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0

```This resolved my syslog errors but I haven't tried reconfiguring the pcHDTV card for NTSC recording to see if it fixes the jumpy playback issue.
Anyone want to give it a try?

---

### Post by Ronno6 on 2009-04-17
I only have the 1 Dvico tuner card, running only analog cable at present. I never got back to setting up the HDTV off-air side of things. It has been some time since I've played with that machine, and I think I need to swap hard drives around again to bring Mythbuntu back up again. My processor is a plain old Pentium 4,  2.8ghz . So I don't have the multi-core situation. Would your solution apply to single-core machines?

---

### Post by newlinux on 2009-04-17
> **Ronno6 said:**
> I only have the 1 Dvico tuner card, running only analog cable at present. I never got back to setting up the HDTV off-air side of things. It has been some time since I've played with that machine, and I think I need to swap hard drives around again to bring Mythbuntu back up again. My processor is a plain old Pentium 4,  2.8ghz . So I don't have the multi-core situation. Would your solution apply to single-core machines?

I'm guessing if you P4 that is hyperthreading it would apply.

---

### Post by Chunk of Earth on 2009-04-17
> My processor is a plain old Pentium 4, 2.8ghz . So I don't have the multi-core situation. Would your solution apply to single-core machines?Yes. It sounds like your system has the same CPU as mine. Issue the following command and you will see your CPU info...
```
cat /proc/cpuinfo
```This is the result on my Mythbuntu system...```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping        : 9
cpu MHz         : 2792.985
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
apicid          : 0
initial apicid  : 0
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
bogomips        : 5585.97
clflush size    : 64
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping        : 9
cpu MHz         : 2792.985
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
apicid          : 1
initial apicid  : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
bogomips        : 5586.42
clflush size    : 64
power management:

```If you have two processor sections then it's a dual-core processor and you could benefit from optimizing your interrupt affinity.

---

### Post by Ronno6 on 2009-04-20
Here's what mine looks like:

ronno6@MythbuntuHTPC:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 3
model name	: Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping	: 4
cpu MHz		: 2793.367
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni monitor ds_cpl cid xtpr
bogomips	: 5591.14
clflush size	: 64

ronno6@MythbuntuHTPC:~$ 

Looks like mine is not hyperthreading??

---

### Post by xioustic on 2009-05-14
Same exact problem with a Hauppauge HVR-1600 card. Every 1/5 or so recordings is sped up and unwatchable. I'll try redistributing the IRQ allocation (as I've just been punching in new cards for the past few weeks). I've seen this happen before on a GBPVR installation on my Windows install as well, which might indicate more that it's a hardware (IRQ?) problem.

Subscribing this thread in hopes it might one day be solved.

:popcorn:

---

### Post by Ronno6 on 2009-05-15
Welcome to the thread, and thanks for posting. I keep watching and hoping, but, as of this time, there has not been any progress on my end, nor any success among the others that suffer this affliction. (Or at least none posted.) At least now we have another tuner card in the mix.
What do your logs show?

---

### Post by xioustic on 2009-05-21
Well, I've done about 40 - 60 recordings since I last posted and I haven't ejc08jtered any that are all sped up... I can't repeat the problem for some reason. I don't know if I did anything different.

I'll have to go back through all my recordings again and doublecheck, but for some reason I think the problem is fixed. irqbalance and a few restarts may have done the trick...? I honestly don't know. I really haven't done much else to the system other than the regular system updates (MythBuntu) and the installation of irqbalance. Hm.

---

### Post by Ronno6 on 2009-05-22
I hope you have the situation licked on your end. I have not had any reply to my post about my processor as to whether that IRQ program would benefit my system or not. Mine only indicates one processor, so I still don't know. Maybe someone has a reply?

---

### Post by newlinux on 2009-05-22
don't know if the program will help single cores or non hyperthreaded CPUS, buy you can find out for sure if yours is hypethreading by installing htop and running it (it's basically an enhanced top - but it will show two CPUs if yours is hyperthreading or dual core) or using top and then press the "1" key. It would show two CPUs at the top.

---

### Post by Ronno6 on 2009-05-23
Thanks. Htop showed only 1 processor. I found the hyperthreading to be disabled in BIOS, so I enabled it. Now I show 2 processors. I've installed irqbalance, so we'll see if that helps the problem.

At least it is a step; now to see in which direction!

---

### Post by remarkosmoc on 2009-07-20
I was happy to find this thread so I know I'm not the only one. 

Mine is a Core2duo 2.66, 4G ram.  I think the problem is isolated to this backend on the analog side of the HDTV card.  I'll keep an eye on this thread as well as try do some irq management.

---

### Post by Ronno6 on 2009-07-25
Thanks for joining in.
Mine is on the analog side of the tuner,as I haven't set the HD side up.
Please post anything you discover.

---

### Post by Ronno6 on 2009-12-14
Did anyone ever discover the cause or cure for this problem?

---

