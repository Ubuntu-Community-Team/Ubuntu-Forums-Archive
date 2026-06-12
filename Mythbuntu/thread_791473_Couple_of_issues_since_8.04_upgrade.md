---
title: "Couple of issues since 8.04 upgrade"
date: 2008-05-12
forum: Mythbuntu
---

### Post by bruk on 2008-05-12
System: Mythbuntu 64 8.04 + latest Mytthtv branch updates/fixes, Athlon 64 X2 4200+, 2 gig, 7600 GS, Hauppage Nova T-500

A) Trying to play video's with MPlayer with "-vo gl" or "-vo gl2" both open a window for a fraction of a second before failing. Playback is fine without either option.

B) LIRC stops responding on a fairly regular basis, requiring a reboot, this was a problem with 7.02/0.20 after my system had been running for a while, but now it can fail within a few hours.

C) When MythNews downloads the content from a feed, the image appears for a fraction of a second before disappearing.

Any help graciously received.

---

### Post by uncle hammy on 2008-05-13
I have been experiencing the issue with LIRC not responding as well.  It happens irregularly, but when it does, the only way I have been able to get it back is to reboot.  When it's down, Mythbuntu is still fully functional (i.e. keyboard works fine), except no remote.

Restarting LIRC does not resolve the issue either.

I can also add that on both my frontend and my backend/frontend machines, when shutting down, there is always a line visible in the console while powering down....

loading remote control daemons :lirc [fail]

---

### Post by amphibem on 2008-05-13
> **uncle hammy said:**
> 
I can also add that on both my frontend and my backend/frontend machines, when shutting down, there is always a line visible in the console while powering down....

loading remote control daemons :lirc [fail]

I can't really be of much help other than to say on my 8.04 installation I get this same error, however LIRC works perfectly for me. 

So make of that what you will :confused:

---

### Post by uncle hammy on 2008-05-14
It works fine for me too.  Just have this issue with the irregular drop outs.  By irregular, I mean the day I installed it, it dropped out within 4 hours, after rebooting it was fine for 4 days, then after an upgrade reboot, it lasted 8 hours, now it's been up 2 days.

---

### Post by trriss on 2008-05-15
> **uncle hammy said:**
> 
Restarting LIRC does not resolve the issue either.


if you restart lirc, after restarting lirc you would have to restart mythfrontend as well for the ir to work again, because only  when starting up does mythfrontend register itself to lirc to receive the ir events....


I haven't had this issue yet( and still on 7.10 atm), but I do have some issues with lirc not starting at all on boot for some reason... but once started I have never had it fail on me so far...

---

### Post by gearshifter on 2008-05-15
I am experiencing lag in my remote.  When I am watching tv, somtimes the remote works instantaneously, but sometimes it will be a delayed response.  My remote will work for a day, then the remote will no longer respond and I will have to restart the computer.

---

### Post by uncle hammy on 2008-05-20
OK, I have narrowed down the circumstances under which mine stops responding, if it helps at all...

My backend is also my frontend in my bedroom.  I usually do my updates in the morning with putty or vnc while the wife is still in bed.  A nasty side effect of being a windows person is I always reboot the system after I do the updates, and it usually gets untouched until later that night.  I have discovered that LIRC stops responding if I reboot the machine then no remote signals are sent for an extended period of time.  In fact, this is the case every time I reboot the machine, and it stays untouched all day.  If I reboot the machine, go into the bedroom and just scroll a menu on the frontend, I am fine, indefinately.

---

### Post by gearshifter on 2008-05-27
my IR reciever that connects by usb is lit up without the remote sending anything.  I can block the reciever and the light will go away.

---

