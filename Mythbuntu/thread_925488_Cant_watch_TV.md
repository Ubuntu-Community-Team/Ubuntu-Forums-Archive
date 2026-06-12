---
title: "Cant watch TV"
date: 2008-09-20
forum: Mythbuntu
---

### Post by jeff45 on 2008-09-20
I cant "Watch TV" on mythfrontend.  When I select "Watch TV", the screen goes black for approx 3 seconds and then returns to previous menu and displays no error codes.  I've yet to be able to Watch TV on myth, so please help.  I'm a noob to linux and mythtv.  The following is my hardware configuration:

CPU: Intell PIII 900Mhz
MB:  Sony OEM, intell 815 chipset, integrated video/snd(turned off)/lan, 3 PCI/1 AGP
Mem: 512Mb PC133
HD: WD 40Gb IDE (mythbuntu OS), IBM 80Gb IDE (WindowsXP)
Vid Capture: Hauppuage WinTV PVR 150 (lost remote)
Vid: Nvidia GeForce2 MX400 64MB AGP
Snd: Crystal Fusion 4 channel
Other: generic usb PCI card, 16x DVD +/-RW/R drive, 3.5 floppy

I know its not top of the line, but this is just a starter experiment.  When booted to WindowsXP, I can watch and pause/record 1 channel using about 50% cpu, so I know my hardware is functional. Problem is I want to switch to linux based myth.

I've successfully installed Mythbuntu 8.04.1 (set up master backend and frontend on same computer), checked and installed all updates, set up backend (many, many, times),  The backend is configured as follows:

General: TV format "NTSC", Broadcast table "US bcast"

Capture cards: Card type: "MPEG-2 encoder (pvr-x50 pvr-500),  Probed info: "Hauppuage Win TV PVR-150 [ivtv]", default input "Tuner 1"

Video Sources: set up 1 source named OTA TV.  set up Schedules direct and use "Local Broadcast Listing" and "default" for channel frequency table. 


Input connections: [MPEG :/dev/video0] (Tuner 1) -> OTA TV, Input "Tuner 1", Video Source "OTA TV", starting channel "3"(WBTV, a valid staion)

Channel Editor:  All my local stations are showing up, used fetch channel info and scanner under video sources.



This is what I can do (or have tried) on the frontend:

Watch a DVD, use program guide to schedule a recording and its not empty(the SD data is getting in there)

BUT! I cant watch TV (maybe I should just stick with windows)
 
I've researched many venues for help with the issue, but to no avail.  I did, However, find one post with similar problem but the solution gave either didn't apply or I didn't understand how to do them.  the person post their mythfrontend log w/ errors and one of the solutions had to do with delete future listings from schedules direct and running mythfilldatabase.

Here the portion on mythfrontend.log that looks suspect:

2008-09-20 16:41:29.602 TV: Attempting to change from None to WatchingLiveTV
2008-09-20 16:41:29.603 Using protocol version 40
2008-09-20 16:41:35.995 GetEntryAt(-1) failed.
2008-09-20 16:41:35.998 EntryToProgram(0@Wed Dec 31 19:00:00 1969) failed to get pginfo
2008-09-20 16:41:35.999 TV Error: LiveTV not successfully started
2008-09-20 16:41:35.999 TV Error: LiveTV not successfully started
2008-09-20 16:41:36.039 TV: Deleting TV Chain in destructor
2008-09-20 16:41:36.058 DPMS Deactivated
2008-09-20 16:41:36.059 DPMS Reactivated.

Not sure how to decipher that error or a fix for it.

---

### Post by jeff45 on 2008-09-20
The problem the whole time was storage directories.  Evidently, during setup I set up directories by accident and couldn't figure out how to delete them(using keyboard and was unaware of the menu "m" keystroke.). So I just created some and enter their paths under storage directories.  The problem was their location and permisions.  The Fix:  during my research I have since learned how to somewhat navigate the myth menus using a standard keyboard and was now able to delete these directories.  Viola, it worked!!!

---

