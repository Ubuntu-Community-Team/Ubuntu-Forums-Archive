---
title: "Frontend dumps on recording end or exit, every time"
date: 2009-07-09
forum: Mythbuntu
---

### Post by MonsterMaxx on 2009-07-09
My TV died so until I can scrounge up the funds to buy a new one I'm just using the backend and a monitor. Sux, but is what it is.

Anyway, backend is a mythbuntu 9 install and every time I'm watching something and the recording ends it dumps the frontend completely. Even an exit of the recording dumps it 99% of the time (once in a while it does not.)

My dedicated frontend is a fedora derivative install (centos) so I don't know if this is common with 'buntu or not.

Any bright ideas why this is happening?

---

### Post by ian dobson on 2009-07-10
Hi,

What do you see in your logs (/var/log/mythtv)?

Regards
Ian Dobson

---

### Post by MonsterMaxx on 2009-07-10
nothing in there but mythbackend.log files

---

### Post by ian dobson on 2009-07-10
Hi,

Then please start the frontend with logging options enabled.

This will create a log file mythfrontend.log in the /var/log/mythtv directory.

Regards
Ian Dosbson

---

### Post by MonsterMaxx on 2009-07-10
I poked around in the setups but didn't see it. Doesn't mean it's not there, just that I didn't go thru the hundreds of pages to find that one setting.

Where is it?

---

### Post by ian dobson on 2009-07-10
Hi,

Have a look in the "mythwelcome settings screens" if your using "mythwelcome" or /etc/mythtv/session-settings if your not.

Regards
Ian Dobson

---

### Post by issih on 2009-07-10
Or if you can't be bothered with that look in the logs of the machine the front end is running on....Or indeed start the front end from a terminal, so when it dumps you can just read its output.

Hope that helps

---

### Post by MonsterMaxx on 2009-07-10
ok, I got it (I think)

I opened the log file, wiped it out, then started mythfrontend, went into recordings, made something play and hit esc. Frontend dumped as it usually does. Here's the contents of the log file.

```

Starting mythfrontend.real..
2009-07-10 12:25:02.136 New DB connection, total: 2
2009-07-10 12:25:02.137 Connected to database 'mythconverg' at host: localhost
2009-07-10 12:25:02.138 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-07-10 12:25:02.138 Enabled verbose msgs:  important general
2009-07-10 12:25:02.497 No theme dir: /home/robin/.mythtv/themes/Mythbuntu-8.04
2009-07-10 12:25:02.499 Primary screen 0.
2009-07-10 12:25:02.499 Using screen 0, 1600x1200 at 0,0
2009-07-10 12:25:02.499 No theme dir: /home/robin/.mythtv/themes/Mythbuntu-8.04
2009-07-10 12:25:02.500 Switching to square mode (Mythbuntu-8.04)
2009-07-10 12:25:02.518 Using the Qt painter
2009-07-10 12:25:02.518 JoystickMenuClient Error: Joystick disabled - Failed to read /home/robin/.mythtv/joystickmenurc
mythtv: could not connect to socket
mythtv: No such file or directory
2009-07-10 12:25:02.528 lirc_init failed for mythtv, see preceding messages
2009-07-10 12:25:03.211 Specified base font 'medium' does not exist for font clock
2009-07-10 12:25:03.212 Specified base font 'medium' does not exist for font small
2009-07-10 12:25:03.212 Specified base font 'medium' does not exist for font medium
2009-07-10 12:25:03.212 Specified base font 'medium' does not exist for font large
2009-07-10 12:25:03.213 Loading from: /usr/share/mythtv/themes/Mythbuntu-8.04/base.xml
2009-07-10 12:25:03.328 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-07-10 12:25:03.373 Registering Internal as a media playback plugin.
2009-07-10 12:25:03.437 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-07-10 12:25:03.472 Failed to run 'cdrecord --scanbus'
2009-07-10 12:25:03.478 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-07-10 12:25:03.484 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-07-10 12:25:03.507 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-07-10 12:25:03.568 No theme dir: /home/robin/.mythtv/themes/Mythbuntu-8.04
2009-07-10 12:25:06.769 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04/ui.xml
2009-07-10 12:25:06.918 Connecting to backend server: 192.168.0.215:6543 (try 1 of 5)
2009-07-10 12:25:06.918 Using protocol version 40
sh: gggg: not found
2009-07-10 12:25:09.283 TV: Attempting to change from None to WatchingPreRecorded
2009-07-10 12:25:09.521 AFD: Opened codec 0xa3037e0, id(MPEG2VIDEO) type(Video)
2009-07-10 12:25:09.521 AFD: codec MP2 has 2 channels
2009-07-10 12:25:09.521 AFD: Opened codec 0xa5b4810, id(MP2) type(Audio)
2009-07-10 12:25:09.524 Opening audio device 'default'. ch 2(2) sr 48000
2009-07-10 12:25:09.524 Opening ALSA audio device 'default'.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
2009-07-10 12:25:09.790 Mixer unable to find control Master
2009-07-10 12:25:09.791 Mixer unable to find control Master
2009-07-10 12:25:09.952 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-07-10 12:25:09.993 OSD Theme Dimensions W: 640 H: 480
2009-07-10 12:25:10.280 TV: Changing from None to WatchingPreRecorded
2009-07-10 12:25:10.283 New DB connection, total: 3
2009-07-10 12:25:10.283 Realtime priority would require SUID as root.
2009-07-10 12:25:10.283 Connected to database 'mythconverg' at host: localhost
2009-07-10 12:25:10.385 Video timing method: USleep with busy wait
2009-07-10 12:25:12.809 TV: Attempting to change from WatchingPreRecorded to None
```

---

### Post by issih on 2009-07-10
Hmmn not much there...

these threads may help:

[http://ubuntuforums.org/showthread.php?t=1145048](http://ubuntuforums.org/showthread.php?t=1145048)
[http://swiss.ubuntuforums.org/showthread.php?t=1205593](http://swiss.ubuntuforums.org/showthread.php?t=1205593)

One report of a straight reinstall fixing things, another of sorting it out by removing pulse audio....

Can't say really, as I am running trunk (0.22 branch) and in there I have to enable the experimental pulse audio patch to get it working in jaunty, but as you are on stable (0.21 branch) you shouldn't have that.

I'd try reinstalling mythbuntu first, then if the problem persists try nixxing pulseaudio and going back to good old alsa.

Hope that helps

---

### Post by MonsterMaxx on 2009-07-10
It's set to use alsa, not pulse

---

### Post by issih on 2009-07-10
Doesn't matter..if pulse is installed it will still screw it all up as pulse hijacks the alsa devices and virtualises them,and by default it is installed in jaunty. 

Try reinstalling myth first, and then try removing pulse audio if that doesn't sort it.

---

### Post by MonsterMaxx on 2009-07-10
Got to say, I'm very hesitant to do any reinstalls. It was a MFSOB to get myth working with my cable box and recording the high channels. Finally had to get my pal from Atlanta up here and he had to tweak the firewire code to make it work.

how would I go about uninstalling pulse without wrecking everything else?

---

### Post by issih on 2009-07-10
```
sudo apt-get remove pulseaudio
```

Ought to do it, or just ferret it out in synaptic package manager.

You might want to run an apt-get autoremove after that to clean out anything that pulled in as a dependancy, just for neatness sake.

Hope that sorts it

---

### Post by MonsterMaxx on 2009-07-10
that seems to have fixed it, mucho thanks.

---

### Post by issih on 2009-07-12
Good oh :)

---

### Post by MonsterMaxx on 2009-07-25
Hi, could uninstalling this have caused the video search feature to break? I'm talking about the 'search imdb' under the video manager.

It was working fine when I tried it a few months ago, last night I tried to add a few vids and it locks up.

First oddity is that when I go into the video manager, there's a box already up that says 'Enter IMDB #' But it's not active or anythign, I can scroll thru normally.

When I try to execute the search it says "user/share/mythtv/mythvideo/s (the rest is truncated so I don't know exactly what is the file)
failed: not executable
Check VideoManager settings.
Press 'ok' and that's the last thing the frontend will do, it's locked up.


I don't recall making any changes to videomanager settings, doesn't mean I didn't, just don't remember doing so.

Is this related or should I start a new thread?

---

