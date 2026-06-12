---
title: "Jerky playback 10.04"
date: 2011-05-15
forum: Mythbuntu
---

### Post by sqeelurgle on 2011-05-15
I just upgraded from Mythbuntu 9.10 to 10.04 (Really long story why not 11.04) and I am getting very very jerky playback.  It's like it's dropping every second frame.  Almost unwatchable.  I have checked the recorded files with VLC and they are very nice and smooth.  Just won't play back well in Myth.  I never had this problem in 9.10.  Any ideas what to do to improve it?  I already tried enabling OpenGL playback with no result.

Thanks

---

### Post by sqeelurgle on 2011-05-16
OK, I have changed the Playback profile to Slim, and that seems to mostly work.  Maybe the new Myth is more CPU sensitive.  Anyway SD plays fine, but HD still doesn't, and that is on Mythtv and on VLC, so it is more of a system issue.  Now, I know (from having 9.10 installed for a while) that my hardware, although a bit older, can play HD video fine - in fact it used to be able to play while also recording without trouble.  Any ideas where to look for the solution?

---

### Post by klc5555 on 2011-05-16
Another testimonial for the "don't upgrade a smoothly working system until the wheels fall off the hardware" school of thought.

Did you enable the proprietary video driver? If you happened to leave the open source one in place, you wouldn't notice until the HD started to stutter and stall.

Otherwise, you may have developed a bottleneck. You will want to check your frontend log to see if you're experiencing a lot of prebuffering stalls that will tend to indicate this. There is a troubleshooting document here: [http://www.mythtv.org/wiki/Troubleshooting:Prebuffering_pause](http://www.mythtv.org/wiki/Troubleshooting:Prebuffering_pause) You will also want to get VDPAU working on your machine, if your older hardware supports it. See here: [http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

Finally, of course, in the case that something went awry in the 9.10->10.04 upgrade process, you could back up your database, secure your recordings, and try a clean install of 10.04. Or, you could always reinstall what is known to work well on your machine: 9.10/myth 0.22.  In this scenario you will need to have saved a copy of your database from your previous 9.10 installation, since the one from 10.04 will likely not be of use in 9.10.

---

### Post by sqeelurgle on 2011-05-16
Thanks.  I did actually do a clean install of 10.04 over the top of 9.10.  The closed source driver for my card won't work.  It's an ATI card, and ATI doesn't seem to support older cards by updating the drivers to suit newer kernels.  It was this same ATI card and open source drivers that worked fine on the old system for HD playback. I do have an Nvidia card coming, so that might help.  I don't think that my problem is just with frontend buffering, because I can get the same problem with VLC.  It seems to me like there must be something on the system that is using a lot of CPU resources - way more than on the 9.10 system.  Is there a way in Linux to see what processes are hogging CPU time?  Maybe I can identify the problem there.

Thanks

---

### Post by agamotto on 2011-05-16
This may fall under the 'stupid' category, but do you have Myth rendering the screen and menus with OpenGL or QT?  That might be behind some of your pain...

---

### Post by sqeelurgle on 2011-05-17
I have tried both OPenGl and Qt rendering it doesn't make a difference.  It does the same thing playing HD videos through VLC though - with the frontend shut down and just running VLC through the desktop (although with the backend still running.  I used top tonight to look at CPU usage, and with a (very jerky) HD video playing, VLC was using about 40% CPU, the backend server was using about 10%, and all up all processes were using around 60-70%.  I assume therefore the problem is not a CPU resource issue, as there was some spare capacity available.  Is there a log available somewhere that might help?  There is nothing relevant in the myth frontend log 

Thanks

---

### Post by klc5555 on 2011-05-17
I didn't say the _problem_ was frontend buffering: that's just the most recognizable symptom, which can be caused by a lot of stuff. So read the doc.

While 10.04/myth 0.23 does engage more system resources than 9.10 or earlier versions, the wonder is actually that you were  _ever_  able to do HD playback on open source drivers, because it almost always does not work and is not really supposed to work. The minimum is supposed to be NVidia or ATI on their proprietary accelerated drivers. So looking further for your HD problem on 10.04 at this stage is pointless.

Your NVidia card should fix things, provided you use the proprietary driver. You indicate that your other hardware is older --VDPAU acceleration (as you may have read in the VDPAU wiki page) will require at least a GeForce 8xx card; and AGP not supported for VDPAU. However, if the older CPU has any oomph, it should still be able to do HD playback even without VDPAU, at least under the "Slim" playback profile.

All-in-all, an awful lot of work and fretting for an unnecessary software upgrade that rendered correctly functioning hardware obsolete. :)

---

### Post by sqeelurgle on 2011-05-17
Hope you're right about the new card and proprietry drivers.  There were a few issues I was having on the old setup that have been solved by the upgrade (probably 2 times in 3 on boot up the TV would just give me a back screen with no signal, and a few other things seem to be solved by the upgrade, so it's not totally wasted effort thankfully, if the new card can solve the video issue.  

Thanks

---

### Post by mymythtv on 2011-05-17
Hi

Upgraded to 10.04 about 1 month after release, and initially everything was fine, but at some point playback became jerky/freezing. it happend ramdomly - sometimes a reboot worked - sometimes not.

Followed a lot of threads, and remember someting about 10.04 kernel version (2.6.32) having problems with USB timing.
( WAF factor decreased a lot during that period )

"Downgraded" kernel to 2.6.31-21 ( as I remember off my head ) and everything were running fine again...

Currently running
Ubuntu 10.04, kernel 2.6.31-21
Myth 0.24
Nvidia GS8400
Hauppauge NOVA DVB-S2
Hauppauge T-500


I did some upgrade over the following month, but always went back to 2.6.31 because of stability...
Havent tried upgrading kernel for the last 3-4 month, so mayby I'll try upgrade kernel again :-)

---

### Post by sqeelurgle on 2011-05-17
When I installed 10.04 I had to upgrade to kernel 2.6.33.  The driver for my tuner cards was first included as part of the kernel in 2.6.33.  The stand alone driver wouldn't install under 10.04 due to some changes made for 10.04.  It would need some changes made to the source code which the developer hasn't done (I guess due it being integrated with the kernel now) and which I am not competent to do.  So I am stuck with kernel versions later than 2.6.33

Thanks

---

### Post by sqeelurgle on 2011-05-18
OK, looking at my dmesg, it looks like there is an error, and the system is booting with the AGP set to PCI mode.  I have had a search by the exact error message, and it looks like an error that appears in the radeon open source driver beyond 10.04, and I haven't found a solution yet.  There is a different open source driver out there that I could try, but seeing that I have a new card due to arrive any day, I might just wait, and limit myself to watching SD playback until then.

---

