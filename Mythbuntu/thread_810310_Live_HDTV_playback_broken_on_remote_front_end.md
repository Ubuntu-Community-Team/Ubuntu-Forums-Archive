---
title: "Live HDTV playback broken on remote front end"
date: 2008-05-28
forum: Mythbuntu
---

### Post by pssturges on 2008-05-28
Hi,

Since I upgraded to 8.04, I cannot get live HD playback to work on my remote frontend machine. The picture either completely freezes or stutters do badly its unwatchable. The audio however, generally continues on unhindered, although it does sometimes stutter badly also.

Strangely, everything else works, including recorded HDTV playback & live SD playback. It seems its not a codec issue. My main frontend/backend machine works fine also.

This machine ran well under Gutsy. This problem any appeared after upgrading to Hardy.

Both machines are running Nvidia 6200 video cards with restricted drivers.

Thanks in advance for any help.
Phil

---

### Post by volkswagner on 2008-05-28
Please post /var/log/mythtv/mythfrontend.log.

---

### Post by pssturges on 2008-05-28
Now that's strange! I have no /var/log/mythtv/mythfrontend.log. In fact there is no mythtv folder within the /var/log folder.

Here's the output when running mythfrontend from the terminal. In this session I played some recorded SD, recorded HD, Live SD and finally some live HD.

Thanks
Phil
```


2008-05-29 08:38:10.591 Using runtime prefix = /usr, libdir = /usr/lib
2008-05-29 08:38:11.214 XScreenSaver support enabled
2008-05-29 08:38:11.214 DPMS is active.
2008-05-29 08:38:11.215 Empty LocalHostName.
2008-05-29 08:38:11.215 Using localhost value of theatrepc
2008-05-29 08:38:11.216 Testing network connectivity to 192.168.0.10
2008-05-29 08:38:11.236 New DB connection, total: 1
2008-05-29 08:38:11.240 Connected to database 'mythconverg' at host: 192.168.0.10
2008-05-29 08:38:11.242 Closing DB connection named 'DBManager0'
2008-05-29 08:38:11.244 Primary screen 0.
2008-05-29 08:38:11.246 Connected to database 'mythconverg' at host: 192.168.0.10
2008-05-29 08:38:11.248 Using screen 0, 1280x720 at 0,0
2008-05-29 08:38:11.261 New DB connection, total: 2
2008-05-29 08:38:11.264 Connected to database 'mythconverg' at host: 192.168.0.10
2008-05-29 08:38:11.266 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2008-05-29 08:38:11.266 Enabled verbose msgs:  important general
2008-05-29 08:38:11.404 Unable to parse themeinfo.xml for glass-wide
2008-05-29 08:38:11.404 The theme (glass-wide) is missing a themeinfo.xml file
2008-05-29 08:38:11.638 Unable to parse themeinfo.xml for glass-wide
2008-05-29 08:38:11.638 The theme (glass-wide) is missing a themeinfo.xml file
2008-05-29 08:38:11.993 Primary screen 0.
2008-05-29 08:38:11.994 Using screen 0, 1280x720 at 0,0
2008-05-29 08:38:11.996 Switching to wide mode (Mythbuntu-8.04-wide)
2008-05-29 08:38:12.021 Using the Qt painter
2008-05-29 08:38:12.023 JoystickMenuClient Error: Joystick disabled - Failed to read /home/phil/.mythtv/joystickmenurc
2008-05-29 08:38:12.023 lirc init success using configuration file: /home/phil/.mythtv/lircrc
2008-05-29 08:38:12.855 Specified base font 'medium' does not exist for font clock
2008-05-29 08:38:12.855 Specified base font 'medium' does not exist for font small
2008-05-29 08:38:12.856 Specified base font 'medium' does not exist for font medium
2008-05-29 08:38:12.856 Specified base font 'medium' does not exist for font large
2008-05-29 08:38:12.857 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04-wide/base.xml
2008-05-29 08:38:12.916 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-05-29 08:38:12.990 Registering Internal as a media playback plugin.
2008-05-29 08:38:13.099 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-05-29 08:38:13.140 Failed to run 'cdrecord --scanbus'
2008-05-29 08:38:13.143 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-05-29 08:38:13.147 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-05-29 08:38:13.178 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.0.2:5060 NAT address 192.168.0.2
SIP: Cannot register; proxy, username or password not set
2008-05-29 08:40:51.822 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04-wide/ui.xml
2008-05-29 08:40:52.778 Connecting to backend server: 192.168.0.10:6543 (try 1 of 5)
2008-05-29 08:40:52.778 Using protocol version 40
2008-05-29 08:40:58.190 AFD: Opened codec 0x82e1e40, id(MPEG2VIDEO) type(Video)
2008-05-29 08:40:58.191 AFD: codec AC3 has 2 channels
2008-05-29 08:40:58.192 AFD: Opened codec 0x83066a0, id(AC3) type(Audio)
2008-05-29 08:41:00.586 AFD: codec MP3 has 2 channels
2008-05-29 08:41:00.587 AFD: Opened codec 0x85a8da0, id(MP3) type(Audio)
2008-05-29 08:41:00.591 AFD: Opened codec 0x8336730, id(MPEG2VIDEO) type(Video)
2008-05-29 08:41:10.288 TV: Attempting to change from None to WatchingPreRecorded
2008-05-29 08:41:10.291 New DB connection, total: 3
2008-05-29 08:41:10.294 Connected to database 'mythconverg' at host: 192.168.0.10
2008-05-29 08:41:10.399 DPMS Deactivated 
2008-05-29 08:41:11.531 AFD: codec MP3 has 2 channels
2008-05-29 08:41:11.531 AFD: Opened codec 0x8300140, id(MP3) type(Audio)
2008-05-29 08:41:11.539 AFD: Opened codec 0x82e1930, id(MPEG2VIDEO) type(Video)
2008-05-29 08:41:11.563 Opening audio device 'default'. ch 2(2) sr 48000
2008-05-29 08:41:11.572 Opening ALSA audio device 'default'.
2008-05-29 08:41:12.265 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-05-29 08:41:12.363 Unable to parse themeinfo.xml for glass-wide
2008-05-29 08:41:12.363 The theme (glass-wide) is missing a themeinfo.xml file
2008-05-29 08:41:12.363 OSD Theme Dimensions W: 640 H: 480
2008-05-29 08:41:13.149 TV: Changing from None to WatchingPreRecorded
2008-05-29 08:41:13.150 The realtime priority setting is not enabled.
greedyhdeint: size changed from 0 x 0 -> 720 x 576
2008-05-29 08:41:13.262 Video timing method: USleep with busy wait
2008-05-29 08:41:27.920 TV: Attempting to change from WatchingPreRecorded to None
2008-05-29 08:41:28.059 TV: Changing from WatchingPreRecorded to None
2008-05-29 08:41:28.159 DPMS Reactivated.
2008-05-29 08:41:28.445 Connecting to backend server: 192.168.0.10:6543 (try 1 of 5)
2008-05-29 08:41:28.446 Using protocol version 40
2008-05-29 08:41:28.842 AFD: codec MP3 has 2 channels
2008-05-29 08:41:28.843 AFD: Opened codec 0x82e1e40, id(MP3) type(Audio)
2008-05-29 08:41:28.847 AFD: Opened codec 0x852e350, id(MPEG2VIDEO) type(Video)
2008-05-29 08:41:30.926 AFD: codec MP3 has 2 channels
2008-05-29 08:41:30.927 AFD: Opened codec 0x852e350, id(MP3) type(Audio)
2008-05-29 08:41:30.931 AFD: Opened codec 0x82e1e40, id(MPEG2VIDEO) type(Video)
2008-05-29 08:41:32.127 AFD: codec MP3 has 2 channels
2008-05-29 08:41:32.127 AFD: Opened codec 0x82e1e40, id(MP3) type(Audio)
2008-05-29 08:41:32.131 AFD: Opened codec 0x852e350, id(MPEG2VIDEO) type(Video)
2008-05-29 08:41:35.199 Connecting to backend server: 192.168.0.10:6543 (try 1 of 5)
2008-05-29 08:41:35.238 Using protocol version 40
2008-05-29 08:41:36.488 AFD: Opened codec 0x852e350, id(MPEG2VIDEO) type(Video)
2008-05-29 08:41:36.489 AFD: codec AC3 has 2 channels
2008-05-29 08:41:36.490 AFD: Opened codec 0x8b26080, id(AC3) type(Audio)
2008-05-29 08:41:40.181 TV: Attempting to change from None to WatchingPreRecorded
2008-05-29 08:41:40.286 DPMS Deactivated 
2008-05-29 08:41:40.885 AFD: Opened codec 0x98c4100, id(MPEG2VIDEO) type(Video)
2008-05-29 08:41:40.885 AFD: codec AC3 has 2 channels
2008-05-29 08:41:40.886 AFD: Opened codec 0x82e4850, id(AC3) type(Audio)
2008-05-29 08:41:40.889 Opening audio device 'default'. ch 2(2) sr 48000
2008-05-29 08:41:40.889 Opening ALSA audio device 'default'.
2008-05-29 08:41:40.894 Opening audio device 'default'. ch 2(2) sr 48000
2008-05-29 08:41:40.894 Opening ALSA audio device 'default'.
2008-05-29 08:41:41.117 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-05-29 08:41:41.359 Unable to parse themeinfo.xml for glass-wide
2008-05-29 08:41:41.359 The theme (glass-wide) is missing a themeinfo.xml file
2008-05-29 08:41:41.359 OSD Theme Dimensions W: 640 H: 480
2008-05-29 08:41:43.052 TV: Changing from None to WatchingPreRecorded
2008-05-29 08:41:43.056 The realtime priority setting is not enabled.
2008-05-29 08:41:43.154 Video timing method: USleep with busy wait
2008-05-29 08:41:46.586 WriteAudio: buffer underrun
2008-05-29 08:41:46.654 WriteAudio: buffer underrun
2008-05-29 08:41:46.752 WriteAudio: buffer underrun
2008-05-29 08:41:56.875 TV: Attempting to change from WatchingPreRecorded to None
2008-05-29 08:41:57.011 TV: Changing from WatchingPreRecorded to None
2008-05-29 08:41:57.180 DPMS Reactivated.
2008-05-29 08:41:57.981 AFD: Opened codec 0x852e350, id(MPEG2VIDEO) type(Video)
2008-05-29 08:41:57.981 AFD: codec AC3 has 2 channels
2008-05-29 08:41:57.982 AFD: Opened codec 0x8b26080, id(AC3) type(Audio)
2008-05-29 08:41:59.351 AFD: Opened codec 0x82e1e40, id(MPEG2VIDEO) type(Video)
2008-05-29 08:41:59.351 AFD: codec AC3 has 2 channels
2008-05-29 08:41:59.352 AFD: Opened codec 0x8b26080, id(AC3) type(Audio)
2008-05-29 08:42:03.491 TV: Attempting to change from None to WatchingLiveTV
2008-05-29 08:42:03.492 Using protocol version 40
2008-05-29 08:42:05.155 NVP: Disabling Audio, params(-1,2,44100)
2008-05-29 08:42:05.172 DPMS Deactivated 
2008-05-29 08:42:05.189 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-05-29 08:42:05.254 Unable to parse themeinfo.xml for glass-wide
2008-05-29 08:42:05.255 The theme (glass-wide) is missing a themeinfo.xml file
2008-05-29 08:42:05.255 OSD Theme Dimensions W: 640 H: 480
2008-05-29 08:42:05.795 TV: Changing from None to WatchingLiveTV
greedyhdeint: size changed from 0 x 0 -> 720 x 576
2008-05-29 08:42:05.801 The realtime priority setting is not enabled.
2008-05-29 08:42:05.898 Video timing method: USleep with busy wait
2008-05-29 08:42:07.974 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-05-29 08:42:08.222 AFD: Opened codec 0x9255b90, id(MPEG2VIDEO) type(Video)
2008-05-29 08:42:08.222 AFD: codec MP3 has 2 channels
2008-05-29 08:42:08.222 AFD: Opened codec 0x9255f10, id(MP3) type(Audio)
2008-05-29 08:42:08.222 AFD: codec AC3 has 2 channels
2008-05-29 08:42:08.223 AFD: Opened codec 0x9256390, id(AC3) type(Audio)
2008-05-29 08:42:08.292 Opening audio device 'default'. ch 2(2) sr 48000
2008-05-29 08:42:08.292 Opening ALSA audio device 'default'.
2008-05-29 08:42:08.309 NVP: Enabling Audio
2008-05-29 08:42:08.311 Opening audio device 'default'. ch 2(2) sr 48000
2008-05-29 08:42:08.311 Opening ALSA audio device 'default'.
2008-05-29 08:42:35.706 NVP: prebuffering pause
2008-05-29 08:42:35.763 WriteAudio: buffer underrun
2008-05-29 08:42:38.905 NVP: Prebuffer wait timed out 10 times.
2008-05-29 08:42:39.404 AFD: Opened codec 0x93a4f70, id(MPEG2VIDEO) type(Video)
2008-05-29 08:42:39.404 AFD: codec AC3 has 6 channels
2008-05-29 08:42:39.405 AFD: Opened codec 0x93f7080, id(AC3) type(Audio)
2008-05-29 08:42:39.523 Opening audio device 'default'. ch 2(2) sr 48000
2008-05-29 08:42:39.524 Opening ALSA audio device 'default'.
2008-05-29 08:42:39.713 WriteAudio: buffer underrun
greedyhdeint: size changed from 720 x 576 -> 1440 x 1088
2008-05-29 08:42:40.629 WriteAudio: buffer underrun
2008-05-29 08:42:40.670 WriteAudio: buffer underrun
2008-05-29 08:42:40.722 WriteAudio: buffer underrun
2008-05-29 08:42:40.816 WriteAudio: buffer underrun
2008-05-29 08:42:40.857 WriteAudio: buffer underrun
2008-05-29 08:42:40.949 WriteAudio: buffer underrun
2008-05-29 08:43:26.651 TV: Attempting to change from WatchingLiveTV to None
2008-05-29 08:43:26.794 TV: Changing from WatchingLiveTV to None
2008-05-29 08:43:26.807 DPMS Reactivated.
Destroying SipFsm object 
2008-05-29 08:43:33.859 Deleting UPnP client...

```

---

### Post by pssturges on 2008-06-03
Anyone?

---

### Post by pssturges on 2008-06-05
OK, after a lot of testing I have finally got it working. But I think there might still be an underlying problem.

Firtly, trying a few different decoder profiles I was able to get it working with "Slim" and also "CPU++".

Now, what's interesting, is that on nearly all profiles there was a significant increase in CPU load when playing LiveTV as apposed to RecordedTV. So, on some profiles, that meant CPU load maxed out on liveHD and therfore wouldn't play properly. As this is a remote front-end machine, I can't see any reason why there should be any difference between live & recorded tv as far as CPU load goes.

By way of example when set to "High Quality" load would run at roughly 60-65% for recorded HD, but max out for live HD and not play. Recorded SD would run at about 50-55% and 100% for live SD but still managed to play. This magnitude of variation is fairly consistant for all profiles.

This same machine worked perfectly well under gutsy with the standard decoder and deinterlacing set to kernel.

So is this a bug or is there some other reason? I would like to be able to try out some of the other profiles and see if I can sqeeze out a little better picture quality if I can.

Hardware:
Athlon 64 3000+
512mb RAM
Nvidia 6200 AGP -> DVI -> HDMI -> Sanyo Z5 Projector (720P @50Hz)

Content (PAL):
SD - 576i @ 50hz
HD - 1080i @ 50hz

Thanks again for any help,
Phil

---

### Post by TimA on 2008-06-05
I have a similar problem on my Mythbuntu 8.04 combined FE/BE. I can't watch live 1080i HDTV without problems, but I can watch recorded HD fine even when I'm recording another HD channel from my HDHomeRun. 

It seems that mythfrontend uses all the available CPU (~90%) for 1080i live HDTV, but only 50-60% CPU for recorded 1080i. 720p seems to work fine with 40-50% CPU during live and recorded viewing. I'm running an Athlon XP 3200 with a NVidia 6200 AGP card (restricted drivers).

HDTV livetv and playback worked great with 40-60% CPU using Knoppmyth 5F27 before I upgraded to Mythbuntu 8.04.

I'm using the Standard MPEG decoder, OpenGL sync, with BOB deinterlacing. The deinterlacing method does not change CPU usage.

Live HDTV works great on my remote Ubuntu 8.04 FE, but it has a AMD 64 X2 4200 CPU with a Nvidia 6600 GT AGP.

Tim

---

### Post by pssturges on 2008-06-06
Interesting. My FE/BE machine is an AMD 64x2 4600 with Nvidia 6200 PCI-E and runs perfectly with live and recorded tv. CPU runs at about 10% & 30% for either live or recorded HD (1080i). And that's with the High Quality profile.
Pretty much what you would expect.

---

### Post by novellahub on 2008-06-06
> **TimA said:**
> I have a similar problem on my Mythbuntu 8.04 combined FE/BE. I can't watch live 1080i HDTV without problems, but I can watch recorded HD fine even when I'm recording another HD channel from my HDHomeRun. 

It seems that mythfrontend uses all the available CPU (~90%) for 1080i live HDTV, but only 50-60% CPU for recorded 1080i. 720p seems to work fine with 40-50% CPU during live and recorded viewing. I'm running an Athlon XP 3200 with a NVidia 6200 AGP card (restricted drivers).

HDTV livetv and playback worked great with 40-60% CPU using Knoppmyth 5F27 before I upgraded to Mythbuntu 8.04.

I'm using the Standard MPEG decoder, OpenGL sync, with BOB deinterlacing. The deinterlacing method does not change CPU usage.

Live HDTV works great on my remote Ubuntu 8.04 FE, but it has a AMD 64 X2 4200 CPU with a Nvidia 6600 GT AGP.

Tim

Edit the /etc/X11/xorg.conf file and add the line:

Option "UseEvents" "True"

To the "Device" section. 

This change will significantly lower the CPU usage for both the mythfrontend and xorg.

---

### Post by TimA on 2008-06-06
I have "UseEvents" "True" in my xorg.conf. I learned that lesson the hard way when I was using Knoppmyth.

HDTV playback from recorded shows works great. I only have a problem with live HDTV. I'm wondering if their is a problem with the kernel SATA drivers and my motherboard. The only difference I can think of with live HDTV is more hard drive activity - writing and reading at the same time.

Tim

---

### Post by pssturges on 2008-06-06
> **TimA said:**
> The only difference I can think of with live HDTV is more hard drive activity - writing and reading at the same time.

That may be possible in your situation (be/fe), but I'm experiencing the same problem on a frontend only machine.

I haven't had a chance to try the UseEvents thing yet. At work atm. I'll report any results.

Phil

---

### Post by TimA on 2008-06-07
Problem solved - Possibly a mythfrontend bug with the playback profiles or faulty playback profile logic on my part.

I use the following custom playback profile under Setup->TV Settings->Playback->Playback Profiles (3/9):

If rez > 0 0 & < 1280 720 then ffmpeg & XVideo 
(with Greedy Mighmotion deinterlacing for SD content - plenty of CPU left for Greedy deinterlacing during SD playback)
If rez == 1280 720 then ffmpeg & Xvideo 
(no deinterlacing since my projector is 1280 x 720p)
If rez > 1280 720 -> ffmpeg & XVideo 
(with Bob 2X deinterlacing)

All above use Standard decoder with xv-blit

I noticed in my mythfrontend log that Greedy Highmotion was being used for 1080i content during live HDTV playback from my HDHomeRun even though I selected Bob 2X in the profile. This was causing mythfrontend to use lots of CPU ~90% for Greedy which left my system with little CPU headroom. Mythfrontend played back the same content recored live with much less CPU ~50%.

Here is the solution - I changed the deinterlacer for "If rez > 0 0 & < 1280 720 then ffmpeg & XVideo" from Greedy Highmotion to Bob 2X and mythfrontend uses only ~50% CPU during live 1080i HTDV viewing. It appears mythfrontend wasn't switching to the proper deinterlacer for my >  'greater than' 1280x720 profile during live playback.

For some reason my playback profile logic seems to work during recorded playback but not during live TV. I would have discovered this issue faster if I created a simple playback profile like the following:

If rez > 0 0 -> ffmpeg & XVideo (with a simple deinterlacer)

Tim

---

### Post by pssturges on 2008-06-08
Great work! That sounds exactly like what I'm experincing. I did a bit of searching, and it looks like this has been reported as already been reported as a bug [here]("http://svn.mythtv.org/trac/ticket/5025")

And there seems ti be a patch! Only problem is I have no idea how to apply it. Can someone point me in the right direction?


Thanks
Phil

---

### Post by TimA on 2008-06-11
Thanks for the info on the patch. I've never applied a patch, but I hope Mythbuntu will have a mythfrontend package update soon.

Tim

---

### Post by pssturges on 2008-06-12
I installed the Myth packages from the hardy proposed repositories, but the problem is still there. I guess we'll just have to wait...

Phil

---

### Post by SeanOB on 2008-08-12
Hello,

Just subscribing to this thread.  I have this issue too.
I have a "frontend only" machine that does fine with all recorded content; but 'live tv' (aka 'watch tv') is super choppy, slow to change channels, and generally unresponsive.

I have worked around it for a while now without issue.  In fact, I didn't really care until the in-laws came to visit and just "wanted to watch tv."  And I said:

Its easy!  Just go to manage recordings, schedule recordings, then program guide.  Then select the show you want to watch, say record only this instance, then exit that, exit again, and exit again to get to the main menu and go to media library, then select watch recordings, now select the recording. Easy! And they just stared back at me and said...  "no no, we just want to watch tv."  Yeah - not easy.  So anyhoo - just looking for plain old "easy" watch tv again.

-Sean

---

### Post by novellahub on 2008-08-12
It appears from the [ticket](http://svn.mythtv.org/trac/ticket/5025) that the fixes are now in the mythtv 0.21-fixes branch.  You can grab these fixes by enabling "Automated Weekly MythTV 0.21-fixes Builds".

[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

---

