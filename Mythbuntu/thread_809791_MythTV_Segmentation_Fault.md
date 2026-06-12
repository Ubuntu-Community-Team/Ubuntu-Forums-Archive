---
title: "MythTV Segmentation Fault"
date: 2008-05-27
forum: Mythbuntu
---

### Post by badwolf on 2008-05-27
Hello.

I have recently installed mythbuntu on my computer, using the dtv1000t card to capture digital tv.

I was able to successfully scan for channels with myth TV, but when I attempt to "watchTV" from the frontend menu, I get a segmentation fault.

This is the output when mythfrontend is run in a terminal

```

2008-05-28 07:29:47.187 lirc init success using configuration file: /home/badwolf/.mythtv/lircrc
2008-05-28 07:29:47.188 JoystickMenuClient Error: Joystick disabled - Failed to read /home/badwolf/.mythtv/joystickmenurc
2008-05-28 07:29:51.848 Specified base font 'medium' does not exist for font clock
2008-05-28 07:29:51.849 Specified base font 'medium' does not exist for font small
2008-05-28 07:29:51.849 Specified base font 'medium' does not exist for font medium
2008-05-28 07:29:51.850 Specified base font 'medium' does not exist for font large
2008-05-28 07:29:51.855 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-05-28 07:29:52.160 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-05-28 07:29:52.420 Registering Internal as a media playback plugin.
2008-05-28 07:29:52.728 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-05-28 07:29:52.877 Failed to run 'cdrecord --scanbus'
2008-05-28 07:29:52.883 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-05-28 07:29:52.889 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-05-28 07:29:53.059 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.2.6:5060 NAT address 192.168.2.6
SIP: Cannot register; proxy, username or password not set
2008-05-28 07:29:58.791 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-05-28 07:29:58.794 Using protocol version 40
2008-05-28 07:29:58.842 TV: Attempting to change from None to WatchingLiveTV
2008-05-28 07:29:58.844 Using protocol version 40
2008-05-28 07:30:00.187 NVP: Disabling Audio, params(-1,2,44100)
Segmentation fault


```

While this is the output in my mythtfrontend.log
```

2008-05-28 07:29:21.284 Specified base font 'medium' does not exist for font medium
2008-05-28 07:29:21.284 Specified base font 'medium' does not exist for font large
2008-05-28 07:29:21.289 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2008-05-28 07:29:21.590 Loading from: /usr/share/mythtv/themes/default/base.xml
2008-05-28 07:29:21.956 Registering Internal as a media playback plugin.
2008-05-28 07:29:22.332 MonitorRegisterExtensions(0x100, gif,jpg,png)
2008-05-28 07:29:22.825 Failed to run 'cdrecord --scanbus'
2008-05-28 07:29:22.830 Failed to run 'cdrecord --scanbus -dev=ATA'
2008-05-28 07:29:22.836 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2008-05-28 07:29:22.981 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
SIP listening on IP Address 192.168.2.6:5060 NAT address 192.168.2.6
SIP: Cannot register; proxy, username or password not set
2008-05-28 07:29:29.666 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-05-28 07:29:29.670 Using protocol version 40
2008-05-28 07:29:29.691 TV: Attempting to change from None to WatchingLiveTV
2008-05-28 07:29:29.693 Using protocol version 40
2008-05-28 07:29:31.070 DPMS Deactivated 
2008-05-28 07:29:31.248 NVP: Disabling Audio, params(-1,2,44100)

```

And this is my Mythbackend.log
```


2008-05-28 07:29:31.400 Finished recording Unknown: channel 2022
2008-05-28 07:29:58.795 MainServer::HandleAnnounce Monitor
2008-05-28 07:29:58.799 adding: mythtv-server as a client (events: 0)
2008-05-28 07:29:58.812 MainServer::HandleAnnounce Monitor
2008-05-28 07:29:58.814 adding: mythtv-server as a client (events: 1)
2008-05-28 07:29:58.845 MainServer::HandleAnnounce Playback
2008-05-28 07:29:58.846 adding: mythtv-server as a client (events: 0)
2008-05-28 07:29:58.854 TVRec(1): Changing from None to WatchingLiveTV
2008-05-28 07:29:58.873 TVRec(1): HW Tuner: 1->1
2008-05-28 07:30:00.035 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2008-05-28 07:30:00.291 TVRec(1): Changing from WatchingLiveTV to None
2008-05-28 07:30:00.351 Finished recording Unknown: channel 2022
QDateTime::fromString: Parameter out of range
2008-05-28 07:30:05.019 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-28 07:30:05.065 Expiring 0 MBytes for 2022 @ Wed May 28 07:22:11 2008 => Unknown
2008-05-28 07:30:05.083 Expiring 0 MBytes for 2003 @ Tue May 27 07:14:34 2008 => Unknown
2008-05-28 07:32:05.151 Expiring 0 MBytes for 2022 @ Wed May 28 07:29:29 2008 => Unknown
QDateTime::fromString: Parameter out of range


```

Apparently the QDateTime error message is listed in another thread as "harmless". So im not sure what is wrong,

Any idea what i can do to fix this?

---

### Post by s_g_robertson on 2008-06-06
I've got an almost identical fault.  However mine is slightly different in that it is only a new mythbuntu installation on a laptop that is causing a problem.  My FE/BE system and seperate FE are both still fine(Admittedly neither running Mythbuntu but both running 0.21-fixes)

There is nothing in the output even with mythfrontend -v all that seem to give any clues.  Need to go find out the best way to debug a segmentation fault.  Any suggestions anyone?
Stephen.

---

### Post by laga on 2008-06-06
Hi,

we'll need you guys to turn on apport to generate a bug report.

* sudo aptitude install apport-gtk

* edit /etc/default/apport and set "default=" to "1"

* sudo /etc/init.d/apport start

* reproduce crash, file bug report on launchpad.

Thanks!

---

### Post by s_g_robertson on 2008-06-06
Right will do that later.

Cheers
Stephen.

EDIT:  Done

---

### Post by badwolf on 2008-06-15
After much head bashing (and trying are reinstall of mythbuntu, mythdora, and knoppmyth) I finally discovered that the PCI port which my card was plugged into was faulty. 
:(

Well thats a lot of time wasted. Atleast i can watch TV now.... If only my remote worked :s

---

### Post by kansei on 2008-06-18
Hmm I see in your console output it mentions "disabling audio".. I get a segfault when I press "watch tv" as well, and I get the following in terminal (not the exact text as I'm on my laptop not the home theatre computer):

Opening audio device '/dev/audio'
Opening OSS audio device '/dev/audio'.
Segmentation fault (core dumped)

I'm submitting the apport bug report right now

---

