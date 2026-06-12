---
title: "Tuner 'lost' when all in use"
date: 2009-11-23
forum: Mythbuntu
---

### Post by Barry_IA on 2009-11-23
Hi Folks!

Fresh install of Mythbuntu 9.10; Hauppauge HVR-1600 and HVR-2250, the latter using LowSky's instructions (thank you!!).

Only have the digital portion of the HVR-1600 running; both digital tuner halves of the HVR-2250 work fine BUT won't put a display (video nor audio) if all three tuners are used concurrently.  If the HVR-1600 and half of the HVR-2250 record concurrently there doesn't seem to be a problem.

Additionally, the recordings on the HVR-2250 were not made (if all three tuners recording concurrently).  The Recordings screen does list the programmes but gives a file not found type of messege.  (If only do two concurrent recordings records properly.)

(I've repeated the tests a couple of times and have the same results, so not an isolated incident.)

I have not tested what happens if I try recording using both halves of the HVR-2250 but not the HVR-1600.  Current configuration is Tuner #1 is the HVR1600 Digital, Tuner #4 is the HVR-2250-0 and Tuner #6 is the 2250-1.

I looked at the Mythbuntu log and have next to no idea what I'm looking at(!).  Looks like its posted at [http://mythbuntu.pastebin.com/f1ff2d88e](http://mythbuntu.pastebin.com/f1ff2d88e).  Some notes and important-looking lines:

I tested to see if the HVR-2250 tuners 'worked' (displayed programming) after the thee concurrent recordings test -- they did not.  Did give me the show title, station channel, and "Signal 0% | BE 0 | (1___) No Lock".  

I then exited MythTV to the Desktop, then re-entered MythTV -- same problem with the HVR-2250 tuners.

I exited MythTV, rebooted the system (clicked on the icon); all three tuners display Live TV now.  However, as noted above, if I do three concurrent recordings I'll have the same problem again.


Extracts from the Log.  I may have the capitalization wrong.

In /var/log/syslog:
   s5h1411_readreg: reading error (ret == -5)
   saa7164_cmd_send() no free sequences
   saa7164_api_i2c_read() error, ret(1) = 0xc
 (the log repeats these three lines over and over)

In /var/log/mythtv/mythfrontend.log
   VideoOutputXv error: XvMC output requested, but is not supported by display
   XLib: extension "XVideo_MotionCompensation" missing on display ":0.0".
   /usr/lib/libXvMC.so.1: undefined symbol: XvMCCreateContext
   Error in my_thread_global_end(): 1 threads didn't exit

(As I typed that I semi-realized the FrontEnd probably isn't the problem.)

FWIW I am fairly certain this problem occurred with Mythbuntu v. 9.04 (same computer).

TIA!

---

### Post by dedrooster on 2009-11-29
I'm curious if you have found a solution to this problem yet. I'm getting the same errors you are finding in syslog, but I only have an HVR-2250.  I can't isolate the conditions that create the error.  In fact, the error seems to occur at times when neither HVR-2250 tuner is in use.

---

### Post by Barry_IA on 2009-11-30
> **dedrooster said:**
> I'm curious if you have found a solution to this problem yet. I'm getting the same errors you are finding in syslog, but I only have an HVR-2250.  I can't isolate the conditions that create the error.  In fact, the error seems to occur at times when neither HVR-2250 tuner is in use.

Hi dedrooster, and welcome, since that appeared to be your first post.

No, unfortunately haven't found a solution.  I'm thinking (hoping) it's a quirk in the motherboard as no one else seems to be having the problem (except you and I <g>), plus I ordered a new mb.  Reasonings: the same problem occurs with both versions of Mythbuntu; I added a second HVR-1600 (digital + analog) which would give me a total of four digital tuners and and now the HVR-2250's don't load at all.  :(    (All of the cards show up with the lspci command.)

---

### Post by jeremycobert on 2009-12-09
im also using the hvr-2250 tuner and am also having this problem. i have tried several ways to replicate it, but i cant. yesterday i was recording on both of the 2250 tuners and my pvr-150 then i switched to mythmusic and into the 3rd song the system locked up.

other times its when im watching a recorded show  and recording  on the 2250, it will lock up.

---

### Post by honsch on 2009-12-12
I too get this problem.  After a recording from an HVR-2250 tuner I can no longer get a lock when trying to watch TV,  If I exit the frontend and restart the backend all is well.

---

### Post by Barry_IA on 2009-12-16
> **honsch said:**
> I too get this problem.  After a recording from an HVR-2250 tuner I can no longer get a lock when trying to watch TV,  If I exit the frontend and restart the backend all is well.
[FONT=Palatino Linotype]
Hi Honsch!

Welcome to Mythbuntu Forums!   At least I know I'm not alone with this problem -- wonder if it's a quirk in the programming (and whose?).   FWIW I'd be willing to help test out this problem -- right now getting the new system together.  (Wonder who gets contacted for volunteering for this type of thing?)

...Sorry for delay in responding: low battery in the UPS, we had a storm, power flickered, power supply in this computer failed.  :(  Not all bad news: found out the case fan had seized and the dust bunnies were growing up!

[/FONT]

---

