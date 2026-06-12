---
title: "mythfrontend.re recently started taking up over 100% of the CPU"
date: 2014-11-07
forum: Mythbuntu
---

### Post by neutron68 on 2014-11-07
All of a sudden (the week of Nov. 5, 2014) the mythtvfrontend.re started hogging the CPU, without warning.

Tonight is the 2nd night this week that the Mythtv frontend became unresponsive to the IR Remote AND the pc keyboard.

Both times, I used the pc keyboard and did an ALT-F1 to get to a terminal screen, and checked the "top" command.
Both times, I saw the mythfrontend.re process taking up over 100% of the CPU!

I found that if I did a "sudo pkill mythrontend" then "sudo pkill mythfrontend.re", I was able to get control of the GUI interface again.
At that point, I restarted the Mythtv Frontend from the GUI interface and it worked again.

**Is anyone else seeing this CPU hogging?**

Is this realted to the mythtv 0.27.4 update or other updates this week?

---

### Post by uteck on 2014-11-08
Do you know if it is happening on certain types of video playback?  It's been awhile since I used MythFronted, but a few times after an update the playback settings got reset to default so some video playback would fail, but others worked fine.

---

### Post by neutron68 on 2014-11-09
It's not happening during video playback.  It's happening while the Mythtv Front End is just sitting there showing the on screen menus.

I discover it's in this 100%+ usage state when I try to use the arrow keys on the pc keyboard or IR remote and they don't respond.

This just started this past week, and I didn't make any changes to the system other than allowing a few updates in the Update Manager.

Eric

---

### Post by neutron68 on 2014-11-09
Another symptom...

see:
[http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu_12-04/20141109_130629_zpsp0cz8sun.jpg]("http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu_12-04/20141109_130629_zpsp0cz8sun.jpg")

It's complaining about not having enough memory to auto-generate a report?  
There is 2GB of RAM, which was enough in the past (Mythbuntu 12.04 64-bit with mythtv 0.25).

Current system:
Mythbuntu 12.04 64-bit, mythtv 0.27+updates repo, VDPAU enabled, 
AMD 4000+, 64x, Dual Core, 2GB RAM, 2TB WD SATA hard drive, Nvidia GT220 card (with 1GB DDR2 RAM), 
BIOSTAR NF4Ultra NF4 Ultra-A9A motherboard

---

### Post by bmcwilliams on 2014-11-12
I have the exact same problem.  Ubuntu 14.04LTS.

I compared the output from ls -l /proc/<PID>/ from when it is behaving to when it is misbehaving, and they are the same.

Here's my Myth details:

MythTV Version : v0.27.4-6-ge0b0027
MythTV Branch : fixes/0.27
Network Protocol : 77
Library API : 0.27.20141016-1
QT Version : 4.8.6
Options compiled in:
 linux profile use_hidesyms using_alsa using_oss using_pulse using_pulseoutput using_backend using_bindings_perl using_bindings_python using_bindings_php using_crystalhd using_dvb using_firewire using_frontend using_hdhomerun using_ceton using_hdpvr using_ivtv using_joystick_menu using_libcrypto using_libdns_sd using_libfftw3 using_libxml2 using_lirc using_mheg using_opengl using_opengl_video using_qtwebkit using_qtscript using_qtdbus using_sdl using_taglib using_v4l2 using_x11 using_xrandr using_xv using_profiletype using_bindings_perl using_bindings_python using_bindings_php using_mythtranscode using_opengl using_vaapi using_vdpau using_ffmpeg_threads using_mheg using_libass using_libxml2

---

### Post by khPWXxF on 2014-11-13
Once you regain control, what do you see in the frontend log and in system log at the time of failure?  ?  

```
less /var/log/mythtv/mythfrontend.log
less /var/log/syslog
``` 

Phil

---

### Post by neutron68 on 2014-11-15
> **khPWXxF said:**
> Once you regain control, what do you see in the frontend log and in system log at the time of failure?  ?  

```
less /var/log/mythtv/mythfrontend.log
less /var/log/syslog
``` 

Phil
I'll keep watching.  It's not happened in 7 days.
I looked in /var/log/mythtv/mythfrontend.log, but I only know the days not the exact times times when the mythfrontend took over the CPU.
I'm grepping for keywords like "error" but not seeing anything suspicious from the days of the processor runaway.

---

### Post by bmcwilliams on 2014-12-08
Ok, so here is what I have found so far:

First off, I am running 14.04LTS with all current updates.

I wrote a simple script to log the CPU Utilization of mythfrontend, mythbackend, and mythcommflag.  It took a couple days to catch it (for a while I was coming home to find 100% CPU every day, but once it knew I was watching it behaved.)  I caught it the other day.

So, mythfrontend idles around 0.5%.  It ran like that for a couple days.  On 12/04/2014 at 21:30 it began to ramp up CPU load.  It ramped up in a fairly linear fashion to 13.7% until 23:37.  At 23:37 mythcommflag started, and mythfrontend CPU load continued to increase linearly to 32.0% at 00:29 when mythcommflag finished.  It continued to increase to 91.6% in what appeared a linear increase to 12/05/2014 at 22:34 when I restarted mythfrontend.

I looked for oddities in the mythfrontend log when the CPU started to ramp up.  I found about five errors like this:

Dec  4 21:30:34 DRJ-myth mythfrontend.real: mythfrontend[2454]: E PlaybackBoxHelper playbackboxhelper.cpp:88 (CheckAvailability) PlaybackBoxHelper: CHECK_AVAILABILITY 'myth://DRJ-myth/1091_20140928030000.mpg' file not found

It looks like about that time, I went looking for recordings whose files went missing.  Other than that, there doesn't seem much out of the ordinary at the time it began to increase.  Then I started watching something else.  It doesn't look like I had been watching anything before that time from the logs.

There weren't any errors during most of that time.  from 12/5 from 02:22 to 18:42 there isn't a single log entry.  The box sat idle.


I will watch for the next failure and see if I can see any patterns.  Anything else I should look for?

---

### Post by tgm4883 on 2014-12-09
> **bmcwilliams said:**
> Ok, so here is what I have found so far:

First off, I am running 14.04LTS with all current updates.

I wrote a simple script to log the CPU Utilization of mythfrontend, mythbackend, and mythcommflag.  It took a couple days to catch it (for a while I was coming home to find 100% CPU every day, but once it knew I was watching it behaved.)  I caught it the other day.

So, mythfrontend idles around 0.5%.  It ran like that for a couple days.  On 12/04/2014 at 21:30 it began to ramp up CPU load.  It ramped up in a fairly linear fashion to 13.7% until 23:37.  At 23:37 mythcommflag started, and mythfrontend CPU load continued to increase linearly to 32.0% at 00:29 when mythcommflag finished.  It continued to increase to 91.6% in what appeared a linear increase to 12/05/2014 at 22:34 when I restarted mythfrontend.

I looked for oddities in the mythfrontend log when the CPU started to ramp up.  I found about five errors like this:

Dec  4 21:30:34 DRJ-myth mythfrontend.real: mythfrontend[2454]: E PlaybackBoxHelper playbackboxhelper.cpp:88 (CheckAvailability) PlaybackBoxHelper: CHECK_AVAILABILITY 'myth://DRJ-myth/1091_20140928030000.mpg' file not found

It looks like about that time, I went looking for recordings whose files went missing.  Other than that, there doesn't seem much out of the ordinary at the time it began to increase.  Then I started watching something else.  It doesn't look like I had been watching anything before that time from the logs.

There weren't any errors during most of that time.  from 12/5 from 02:22 to 18:42 there isn't a single log entry.  The box sat idle.


I will watch for the next failure and see if I can see any patterns.  Anything else I should look for?

What theme are you using? It sounds like this only occurs when the frontend is idle, correct?

---

### Post by bmcwilliams on 2014-12-10
> **tgm4883 said:**
> What theme are you using? It sounds like this only occurs when the frontend is idle, correct?

MythCenter-wide 1.7.  So far it seems to happen when idle.  For a while it happened daily.  Now it is much less frequent.

---

### Post by khPWXxF on 2014-12-11
Have you seen this similar thread?
[https://forum.mythtv.org/viewtopic.php?f=36&t=496](https://forum.mythtv.org/viewtopic.php?f=36&t=496)
Phil

---

### Post by neutron68 on 2014-12-14
> **khPWXxF said:**
> Have you seen this similar thread?
[https://forum.mythtv.org/viewtopic.php?f=36&t=496](https://forum.mythtv.org/viewtopic.php?f=36&t=496)
Phil
No, I haven't.  Looks like this is a real problem and we're not alone!

The problem had been dormant for 4 weeks and JUST occurred again tonight - as before 100%+ CPU utilization on process mythfrontend.re.

What info should I harvest from logs?

I'm using MythCenter Wide as a theme.

Here's today's mythbackend.log (grep "mythfrontend.real" /var/log/mythtv/mythfrontend.log)
```
Dec 14 00:20:55 Mythbuntu mythfrontend.real: mythfrontend[3801]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 14 01:20:55 Mythbuntu mythfrontend.real: mythfrontend[3801]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 14 02:20:55 Mythbuntu mythfrontend.real: mythfrontend[3801]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 14 03:20:55 Mythbuntu mythfrontend.real: mythfrontend[3801]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 14 04:20:55 Mythbuntu mythfrontend.real: mythfrontend[3801]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 14 04:23:35 Mythbuntu mythfrontend.real: mythfrontend[3801]: I CoreContext mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 2
Dec 14 05:20:55 Mythbuntu mythfrontend.real: mythfrontend[3801]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 14 06:20:55 Mythbuntu mythfrontend.real: mythfrontend[3801]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 14 07:20:55 Mythbuntu mythfrontend.real: mythfrontend[3801]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 14 08:20:55 Mythbuntu mythfrontend.real: mythfrontend[3801]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 14 09:20:55 Mythbuntu mythfrontend.real: mythfrontend[3801]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 14 10:20:55 Mythbuntu mythfrontend.real: mythfrontend[3801]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 14 11:20:55 Mythbuntu mythfrontend.real: mythfrontend[3801]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 14 12:20:55 Mythbuntu mythfrontend.real: mythfrontend[3801]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 14 13:20:55 Mythbuntu mythfrontend.real: mythfrontend[3801]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 14 14:20:55 Mythbuntu mythfrontend.real: mythfrontend[3801]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 14 15:20:55 Mythbuntu mythfrontend.real: mythfrontend[3801]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 14 16:20:55 Mythbuntu mythfrontend.real: mythfrontend[3801]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 14 16:22:08 Mythbuntu mythfrontend.real: mythfrontend[3801]: I CoreContext mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 2
Dec 14 16:22:08 Mythbuntu mythfrontend.real: mythfrontend[3801]: N CoreContext mythmainwindow.cpp:2810 (ExitStandby) Leaving standby mode
Dec 14 17:20:55 Mythbuntu mythfrontend.real: mythfrontend[3801]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 14 17:52:09 Mythbuntu mythfrontend.real: mythfrontend[3801]: N CoreContext mythmainwindow.cpp:2760 (IdleTimeout) Entering standby mode after 90 minutes of inactivity
Dec 14 18:20:55 Mythbuntu mythfrontend.real: mythfrontend[3801]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 14 18:25:40 Mythbuntu mythfrontend.real: mythfrontend[3801]: N CoreContext mythmainwindow.cpp:2810 (ExitStandby) Leaving standby mode
Dec 14 18:25:40 Mythbuntu mythfrontend.real: mythfrontend[3801]: I CoreContext mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 2
Dec 14 19:55:42 Mythbuntu mythfrontend.real: mythfrontend[3801]: N CoreContext mythmainwindow.cpp:2760 (IdleTimeout) Entering standby mode after 90 minutes of inactivity
Dec 14 19:56:56 Mythbuntu mythfrontend.real: mythfrontend[3801]: N CoreContext mythmainwindow.cpp:2810 (ExitStandby) Leaving standby mode
Dec 14 19:58:50 Mythbuntu mythfrontend.real: mythfrontend[3801]: E PlaybackBoxHelper programinfo.cpp:2358 (GetPlaybackURL) ProgramInfo(2091_20141215015900.mpg): GetPlaybackURL: '2091_20141215015900.mpg' should be local, but it can not be found.
Dec 14 19:58:50 Mythbuntu mythfrontend.real: mythfrontend[3801]: E PlaybackBoxHelper playbackboxhelper.cpp:88 (CheckAvailability) PlaybackBoxHelper: CHECK_AVAILABILITY 'GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/Mythbuntu/2091_20141215015900.mpg' file not found
Dec 14 19:58:50 Mythbuntu mythfrontend.real: mythfrontend[3801]: E PlaybackBoxHelper programinfo.cpp:2358 (GetPlaybackURL) ProgramInfo(2091_20141215015900.mpg): GetPlaybackURL: '2091_20141215015900.mpg' should be local, but it can not be found.
Dec 14 19:58:50 Mythbuntu mythfrontend.real: mythfrontend[3801]: E PlaybackBoxHelper playbackboxhelper.cpp:88 (CheckAvailability) PlaybackBoxHelper: CHECK_AVAILABILITY 'GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/Mythbuntu/2091_20141215015900.mpg' file not found
Dec 14 19:58:50 Mythbuntu mythfrontend.real: mythfrontend[3801]: E PlaybackBoxHelper programinfo.cpp:2358 (GetPlaybackURL) ProgramInfo(2091_20141215015900.mpg): GetPlaybackURL: '2091_20141215015900.mpg' should be local, but it can not be found.
Dec 14 19:58:50 Mythbuntu mythfrontend.real: mythfrontend[3801]: E PlaybackBoxHelper playbackboxhelper.cpp:88 (CheckAvailability) PlaybackBoxHelper: CHECK_AVAILABILITY 'GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/Mythbuntu/2091_20141215015900.mpg' file not found
Dec 14 20:04:41 Mythbuntu mythfrontend.real: mythfrontend[3801]: I CoreContext tv_play.cpp:1063 (TV) TV: Creating TV object
Dec 14 20:04:41 Mythbuntu mythfrontend.real: mythfrontend[3801]: N CoreContext mythmainwindow.cpp:2737 (PauseIdleTimer) Suspending idle timer
Dec 14 20:04:41 Mythbuntu mythfrontend.real: mythfrontend[3801]: I CoreContext tv_play.cpp:1280 (Init) TV: Created TvPlayWindow.
Dec 14 20:04:41 Mythbuntu mythfrontend.real: mythfrontend[3801]: I CoreContext tv_play.cpp:2225 (HandleStateChange) TV: Attempting to change from None to WatchingPreRecorded
```


Eric

---

### Post by tgm4883 on 2014-12-15
> **neutron68 said:**
> 
Here's today's mythbackend.log (grep "mythfrontend.real" /var/log/mythtv/mythfrontend.log)
Eric

Quick point of clarification, not every log is a mythbackend.log file. mythbackend.log is the log file for the backend process. You posted the frontend log (as specified by the command you ran). Super minor point, but I thought I'd point it out since I was replying anyway.


Now back to the issue. What happens if you disable idle mode? Does the issue still occur?

---

### Post by bmcwilliams on 2014-12-16
> **tgm4883 said:**
> Now back to the issue. What happens if you disable idle mode? Does the issue still occur?

I have idle mode disabled already and have the problem.  I have never tried enabling idle mode since I setup the box.  It was still on my to-do list.

---

### Post by tgm4883 on 2014-12-16
> **bmcwilliams said:**
> I have idle mode disabled already and have the problem.  I have never tried enabling idle mode since I setup the box.  It was still on my to-do list.

Does it only happen when you leave the frontend on the main menu?

---

### Post by neutron68 on 2014-12-16
> **tgm4883 said:**
> Does it only happen when you leave the frontend on the main menu?
That's how it's been on my system.  I discover it when I can't get the Menu to respond to commands.

And I don't know to enable or disable idle mode, so the system is running in whatever the default mode is.

On my earlier message, I mistyped.  
I meant to type "Here's today's [COLOR="#FF0000"]mythfrontend.log[/COLOR] (grep "mythfrontend.real" /var/log/mythtv/mythfrontend.log)"

---

### Post by neutron68 on 2014-12-19
The machine did it again today...100%+ on the mythfrontend.re task.

Here's the output from grep "mythfrontend.real" /var/log/mythtv/mythfrontend.log again.

I'm pretty sure the the 100%+ cpu usage situation occurred somewhere in the time frame of these entries.

```
Dec 19 00:35:12 Mythbuntu mythfrontend.real: mythfrontend[19477]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 19 01:35:12 Mythbuntu mythfrontend.real: mythfrontend[19477]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 19 02:35:12 Mythbuntu mythfrontend.real: mythfrontend[19477]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 19 03:35:12 Mythbuntu mythfrontend.real: mythfrontend[19477]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 19 04:35:12 Mythbuntu mythfrontend.real: mythfrontend[19477]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 19 05:17:52 Mythbuntu mythfrontend.real: mythfrontend[19477]: I CoreContext mythdbcon.cpp:409 (PurgeIdleConnections) New DB connection, total: 3
Dec 19 05:35:12 Mythbuntu mythfrontend.real: mythfrontend[19477]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 19 06:35:12 Mythbuntu mythfrontend.real: mythfrontend[19477]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 19 07:35:12 Mythbuntu mythfrontend.real: mythfrontend[19477]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 19 08:35:13 Mythbuntu mythfrontend.real: mythfrontend[19477]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 19 09:35:12 Mythbuntu mythfrontend.real: mythfrontend[19477]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 19 10:35:12 Mythbuntu mythfrontend.real: mythfrontend[19477]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 19 11:35:12 Mythbuntu mythfrontend.real: mythfrontend[19477]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 19 12:35:12 Mythbuntu mythfrontend.real: mythfrontend[19477]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 19 13:35:12 Mythbuntu mythfrontend.real: mythfrontend[19477]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 19 14:35:12 Mythbuntu mythfrontend.real: mythfrontend[19477]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 19 15:35:12 Mythbuntu mythfrontend.real: mythfrontend[19477]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 19 16:35:13 Mythbuntu mythfrontend.real: mythfrontend[19477]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
Dec 19 17:35:12 Mythbuntu mythfrontend.real: mythfrontend[19477]: E CoreContext themeinfo.cpp:34 (ThemeInfo) ThemeInfo: The theme (myth://Temp@Mythbuntu/remotethemes/0.27/MythCenter-wide) is missing a themeinfo.xml file.
```

---

### Post by neutron68 on 2014-12-20
I found another report of this from a Mythbuntu 12.04 user in Spring 2014.

[http://www.gossamer-threads.com/lists/mythtv/users/567439](http://www.gossamer-threads.com/lists/mythtv/users/567439)

---

### Post by neutron68 on 2014-12-22
There was a suggested workaround for this situation posted at forum.mythtv.org:

> postby paulh » Sun Dec 21, 2014 3:48 pm

The problem is triggered by the theme update checker trying to download the themeinfo.xml files. Most of the time it works but sometimes it cause the MythDownloadManager thread to run away using 100% cpu.

The theme update checker will only run when the FE is showing the main menu so as a temporary work around you can prevent the problem by leaving Myth on a screen other than the main menu.

---

### Post by neutron68 on 2014-12-28
I tried the suggested workaround (changing to a menu screen OTHER than the Main Menu). 

Since reading the post on Dec.21, I have been leaving my screen on the Watch Recordings screen - no change. 
The mythfrontend.re process still grabs 100+% of the CPU.

Has this bug been officially logged in [https://code.mythtv.org/trac?](https://code.mythtv.org/trac?) I'm searching and have not found an entry yet.

---

### Post by neutron68 on 2015-01-24
Bug report filed.
[https://code.mythtv.org/trac/ticket/12356#ticket](https://code.mythtv.org/trac/ticket/12356#ticket)

Effected users:  Please, enter your relevant information into the ticket

In late December 2014, the behavior changed a little. mythfrontend.re still hogged 100% of one of the CPU cores, but the keyboard and IR remote still worked to control it. 
The main effect of having 100% of one CPU core occupied is slow UI response times and missed/skipped characters/numbers during the run of the IR blaster channel change script, which sends IR channel change codes to the satellite receiver.
I found that I can run the channel change script when the mythfrontend is not running, and all IR characters are recognized by the satellite receiver.
When the mythfrontend is running and taking 100% of a CPU core, not all the IR characters are sent to the satellite receiver. Often channel 355 gets sent as channel 5 (clearly the 3 was missent or never sent).

January 2015: At present, the behavior is the same as in December 2014.

Current Workaround: Exit mythfrontend at the end of every program viewing session, and only run the mythfrontend when I want to view recorded programs. By doing this, the IR blaster channel change script executes normally, without missed digits.

---

### Post by neutron68 on 2015-01-25
A new workaround for the issue was suggested in the bug tracking ticket.

The cause of the issue is believe to be the periodic background process which looks for theme updates.
You can disable this update check by going to Theme Chooser screen, click the Right Arrow key to get the Theme Chooser Menu, select Disable Theme Update Notifications.

This workaround worked on my system and has kept the CPU from getting pegged at 100%.

[IMG]http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu_12-04/ThemeChooserMenu_zps3da9fe39.jpg[/IMG]

---

### Post by neutron68 on 2015-05-06
Update:  It turned out the workaround didn't work.  mythfrontend.re still takes over CPU usage, after some period of time.

The only workaround that works for me:  Exit mythfrontend at the end of every program viewing session, and only run the mythfrontend when I want to view recorded programs. By doing this, the IR blaster channel change script executes normally, without missed digits.

Hopefully this problem with mythfrontend.re can be understood and fixed.

---

### Post by neutron68 on 2015-05-27
The trouble ticket has been worked on and closed out!
see [https://code.mythtv.org/trac/ticket/12356#comment:14](https://code.mythtv.org/trac/ticket/12356#comment:14)

The fix is in mythtv as of v0.27.4-64-g8fd277b

I pulled down updates this morning and I got v0.27.4-66-gc02d8cd

My Mythbuntu 12.04 machine with v0.27.4-66-gc02d8cd has been running for about 3.5 hours without the mythfrontend taking 100% of a CPU core!
It does appear solved!

Edit:

After 14 hours, my 12.04 machine is still working normally, without the mythfrontend taking 100% of a CPU core!  WOOO HOOO!

Thanks to the developers who coded and tested this fix!

Eric

---

