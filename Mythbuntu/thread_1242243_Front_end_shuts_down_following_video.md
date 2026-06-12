---
title: "Front end shuts down following video"
date: 2009-08-16
forum: Mythbuntu
---

### Post by tindola on 2009-08-16
Hello, 

I've been working with mythbuntu 9.04 for a couple weeks now and I am really happy with most of it.  However, whenever i am watching a video or dvd and i stop it midway or when it ends, the Mythbuntu frontend is closed an I am back on the ubuntu desktop..I am using the Internal command for watching the video.  This does not happen when I watch an Apple Trailer. Any help on how to change the settings so that it goes back to the mythbuntu frontend would be appreciated.  



Tindola

---

### Post by tindola on 2009-08-18
Hi.  I am still having this problem.  Is there more information that I should post to help to try to get an answer.  This was my first post.  I've gotten a ton of useful info from these boards, but i hadn't found an answer to this problem.  Thanks in advance for your help.

---

### Post by larsolav on 2009-08-18
> **tindola said:**
> Hi.  I am still having this problem.  Is there more information that I should post to help to try to get an answer.  This was my first post.  I've gotten a ton of useful info from these boards, but i hadn't found an answer to this problem.  Thanks in advance for your help.

It may help to see your frontend log (or at least the end of the logs from right before / after the frontend crashes). The log may shed some light...

/var/log/mythtv/mythfrontend.log

---

### Post by logicl77 on 2009-08-19
Hello, I have the exact same issue with my Mythbuntu frontend on 9.04. 

I renamed by mythfrontend.log file and then ran frontend, went to recordings, played a previously recorded tv show, during playback, I clicked on esc key and it kills the frontend and I'm back at the desktop.  Any ideas.

here is my var/log/mythtv/mythfrontend.log file

  GNU nano 2.0.9                             File: /var/log/mythtv/mythfrontend.log                                                                                                                                

Starting mythfrontend.real..
2009-08-19 17:28:37.524 New DB connection, total: 2
2009-08-19 17:28:37.528 Connected to database 'mythconverg' at host: 192.168.10.210
2009-08-19 17:28:37.534 mythfrontend version: 0.21.20080304-1 [www.mythtv.org]("http://www.mythtv.org")
2009-08-19 17:28:37.534 Enabled verbose msgs:  important general
2009-08-19 17:28:38.097 No theme dir: /home/lewisl/.mythtv/themes/G.A.N.T
2009-08-19 17:28:38.099 Primary screen 0.
2009-08-19 17:28:38.100 Using screen 0, 1280x720 at 0,0
2009-08-19 17:28:38.101 No theme dir: /home/lewisl/.mythtv/themes/G.A.N.T
2009-08-19 17:28:38.101 Switching to square mode (G.A.N.T)
2009-08-19 17:28:38.125 Using the Qt painter
2009-08-19 17:28:38.130 JoystickMenuClient Error: Joystick disabled - Failed to read /home/lewisl/.mythtv/joystickmenurc
2009-08-19 17:28:38.131 lirc init success using configuration file: /home/lewisl/.mythtv/lircrc
2009-08-19 17:28:38.712 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-08-19 17:28:38.779 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-08-19 17:28:38.940 Registering Internal as a media playback plugin.
2009-08-19 17:28:39.038 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-08-19 17:28:39.058 Failed to run 'cdrecord --scanbus'
2009-08-19 17:28:39.062 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-08-19 17:28:39.064 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-08-19 17:28:39.132 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-08-19 17:28:39.237 No theme dir: /home/lewisl/.mythtv/themes/G.A.N.T
2009-08-19 17:28:46.291 XMLParse::LoadTheme using /usr/share/mythtv/themes/G.A.N.T/ui.xml
2009-08-19 17:28:46.494 Connecting to backend server: 192.168.10.210:6543 (try 1 of 5)
2009-08-19 17:28:46.496 Using protocol version 40
2009-08-19 17:28:48.790 AFD: Opened codec 0x85f6860, id(MPEG2VIDEO) type(Video)
2009-08-19 17:28:48.790 AFD: codec AC3 has 6 channels
2009-08-19 17:28:48.791 AFD: Opened codec 0x85f5fc0, id(AC3) type(Audio)
2009-08-19 17:28:49.675 TV: Attempting to change from None to WatchingPreRecorded
2009-08-19 17:28:49.779 DPMS Deactivated
2009-08-19 17:28:50.051 AFD: Opened codec 0x8653130, id(MPEG2VIDEO) type(Video)
2009-08-19 17:28:50.051 AFD: codec AC3 has 6 channels
2009-08-19 17:28:50.052 AFD: Opened codec 0x86678d0, id(AC3) type(Audio)
2009-08-19 17:28:50.307 AFD: Opened codec 0xadda3ef0, id(MPEG2VIDEO) type(Video)
2009-08-19 17:28:50.307 AFD: codec AC3 has 6 channels
2009-08-19 17:28:50.308 AFD: Opened codec 0xadda4370, id(AC3) type(Audio)
2009-08-19 17:28:50.313 Opening audio device 'default'. ch 2(2) sr 48000
2009-08-19 17:28:50.313 Opening ALSA audio device 'default'.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2009-08-19 17:28:50.655 AudioOutput Warning: Mixer attach error -2: No such file or directory
                        Check Mixer Name in Setup: '/dev/mixer'
2009-08-19 17:28:50.821 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-08-19 17:28:50.919 OSD Theme Dimensions W: 640 H: 480
2009-08-19 17:28:51.578 TV: Changing from None to WatchingPreRecorded
2009-08-19 17:28:51.578 New DB connection, total: 3
2009-08-19 17:28:51.579 Realtime priority would require SUID as root.
2009-08-19 17:28:51.582 Connected to database 'mythconverg' at host: 192.168.10.210
2009-08-19 17:28:51.681 Video sync method can't support double framerate (refresh rate too low for bob deint)
2009-08-19 17:28:51.682 Video timing method: USleep with busy wait
2009-08-19 17:29:18.465 DPMS Reactivated.
2009-08-19 17:29:22.698 TV: Attempting to change from WatchingPreRecorded to None


Thanks,

Lewis

---

### Post by larsolav on 2009-08-20
Others have had similar issues, it seems.
Someone mentioned removing Pulse audio:
[http://ubuntuforums.org/showthread.php?t=1145048](http://ubuntuforums.org/showthread.php?t=1145048)
Don't know if it would help you...

Hope you get it working soon!

---

### Post by tindola on 2009-08-30
thank you.  Removing the Pulse Audio fixed this issue for me.

---

### Post by Robert_Br on 2009-08-30
I just posted a similar thread [here]("http://ubuntuforums.org/showthread.php?p=7871670"). I'm having the same issue, but pulseaudio is not installed on my system. :(

---

