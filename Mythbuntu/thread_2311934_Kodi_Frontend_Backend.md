---
title: "Kodi? Frontend? Backend?"
date: 2016-01-31
forum: Mythbuntu
---

### Post by jrh74 on 2016-01-31
I have cut cord and now rely on over the air signal for my TV viewing.  Untill recently I used Windows    Media Center to allow me to pause shows, backup and replay shows and to record one show while watching another.  It also allowed me to look at a schedule of programs currently showing and to select future programs for recording.  Now I have upgraded to windows 10 and must find an alternative to WMC since it is not supported by windows 10.  To this end I have downloaded the relevant files for MythTV and am working up the courage to install and configure it to replace WMC.  In the meantime, I keep seeing “Kodi” as to most frequently mentioned alternative to Windows Media Center.  My question is: Should I be Using “Kodi” or “MythTV” or a combination of both to accomplish my goals?  Also, could anyone clarify the distinction between “frontend and backend” and the relevancy of these terms to the issues described above?    
 
 
 My system
 Mother board: ASRock Z77 Pro 4 with integrated sound and video  
 Hard Drive 1: WDOEM  WD1TB BLUE SATA6.0 HD (1000 Gb) w/Ubuntu 14.04.3 Desktop OS
 Hard Drive 2: Toshiba (500 GB) w/Windows 10 OS
 Memory: CRUCIAL 8GB 4X2D3 1333 DIMM CL
 TV tuner: Hauppauge WinTV-HVR-2250 (two tuners)
 
 
 I assembled this system in order to better understand computer hardware.  And to learn something about linux.

---

### Post by aelfric55 on 2016-01-31
Re. backend and frontend, no better place to start reading than here: [https://www.mythtv.org/detail/mythtv](https://www.mythtv.org/detail/mythtv)

Mythtv is a (mostly) complete application suite for media which schedules/records from one or more backends, and plays back through a user interface on one or more frontends. The learning curve is fairly significant. Kodi by itself is a frontend/viewer for a lot of formats, but if TV is your interest, it requires a 3rd-party backend to do all its scheduling and recording. This can be the backend half of a mythtv installation, or the TVHeadend backend application, or a few other backends. See [http://kodi.wiki/view/PVR_recording_software](http://kodi.wiki/view/PVR_recording_software).

Your hardware is well-supported on Linux. Your tuner cards should basically "just work" for digital TV with just about any TV software; analog from a cable box or what have you will require a bit of kernel firmware. (providing your Hauppauge 2250s are actual 2250s and not 2255s. 2255s work well, but are still "digital-only" on Linux, and will require a driver patch or a kernel upgrade to run on Ubuntu 14.04) See [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2250](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2250) and [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2255](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2255) if you need additional information on it. 

All necessary packages for Mythtv, Kodi, and most other video-related software are ready-to-go for all flavors of Ubuntu. When you decide which television applications you wish to run, installation will be straightforward. Configuration may be a bit more challenging; you'll be spending a fair amount of time reading from the wikis for the applications you decide you want to use.

---

