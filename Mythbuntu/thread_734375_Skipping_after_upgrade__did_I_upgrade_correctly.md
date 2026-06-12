---
title: "Skipping after upgrade / did I upgrade correctly?"
date: 2008-03-24
forum: Mythbuntu
---

### Post by bblboy54 on 2008-03-24
My current network has a backend server with 2 tuners, a front end machine, and a regular ubuntu desktop machine with mythtv added via apt-get.  A few days ago I run the update manager on the desktop and it, of course, updated to the new version of mythtv.  Unfortunately, I couldn't use that because of differening versions on the backend and on that front end.  What made things worse was it also changed something on the backend database and I lost my tuners.  I decided that I would just do "apt-get dist-upgrade" on the front end and backend machines (at this point I did not realize that 8.04 was even out).  After I did the upgrade I re-ran mythtv-setup on the backend and reconfigured the tuners and everything worked.....

.... well, sorta.

The issue I am having now is that when I'm watching TV on my front end machine I often have a skipping playback.  I skimmed some of the log files and I found that on the front end machine I'm seeing complaints about the audio buffer running out.  I'm not seeing any errors on the backend that I can immediately see.  This seems to happen 95% of the time while watching live TV but a lot less when just watching recordings.  I have made no changes other than the dist-upgrade.

My questions:

1> I noticed on the website it says to use "update-manager -c -d" .... is this the same as "apt-get dist-upgrade"....  also, it held back mythvideo -- is this desired?

2> What would have changed that may be causing this skipping now?  The same exact setup functioned perfectly before doing the upgrade and all hardware is exactly identical.

For reference, my systems:

Backend:
Dual AMD Opteron 270 on Tyan S2882
4GB of PC3200 RAM
1x Hauppauge PVR150 (Retail)
1x Hauppauge PVR150MCE
3ware 9000 series 8 port SATA RAID
8x WD2500 (250GB) SATA Hard Drives

Frontend:
Pentium 3 1.2GHZ / Intel 815 Server Board
512MB PC133 RAM
40GB IDE Hard Drive
Chaintech A710 Sound Card (Using AC3/SPDIF Optical)
1x Hauppauge PVR150 (For remote control use only)

---

### Post by windexh8er on 2008-03-24
I have the same problem...  Same FE/BE setup which was working before 8.04.  I did clean installs on both the BE and the FE, no dice.  Tried disabling ACPI and APIC on the FE.  Nothin'...  Since I have AMD64 on the FE I might just try i386 for the heck of it since I can't watch live TV now.  Grrr.

The proc load on both boxes is low, so I have no idea.  Like 20% on the BE and about 50% on the FE.  Both boxes have a gig of RAM.  Picture looks "better", but I get about 4 seconds of playback, then freeze, then 4 seconds, then freeze.  The FE playback is set to "Slim" even.

If anyone figures this out it'd be much appreciated.  My stuff is mainly HD (HDTV as well as FusionGold).  But, it worked fine before.

UPDATE:
Well, I know it's not my BE at least.  Running 0.21 FE on my Macbook now and it's flawless over 802.11n.  I'll try rebuilding my FE with i386.  :(  Maybe the proc isn't up to the task (although top says otherwise).  It's an AMD 3000+ 64.  Thoughts?

---

### Post by parker13 on 2008-04-01
I have the same issue on a combined frontend/backend after an upgrade to Myth 0.21 in the gutsy backports repo, so it's probably more to do with frontend playback in 0.21 than anything in Hardy.

I don't use it for live TV, but when playing recordings it skips a few frames every minute or so.

I've played with lots of settings to no avail. I'll keep trying...

---

### Post by bblboy54 on 2008-04-28
I still havent heard any official responses regarding this issue but I was able to change some settings to get it to play ok.  Mainly I reduced the resolution on the system down to 640x480 and it seems to be ok now.  I think it may be related to the Intel i815 video (on board).  I had issues with it on the first beta of mythbuntu but they were solved later with a restricted driver.  My guess is the new distro just doesn't handle the card correctly.

---

### Post by bblboy54 on 2008-04-28
In the interest of troubleshooting and narrowing down this issue I install a GeForce2 MX video card in the system and completely reloaded from scratch.  Again I am having the huge skipping issue.  Everything was fine in 7 but it seems that after upgrading to 8.04 the system is consuming an incredible amount of CPU.  Looking at top on an SSH session while I'm watching a recording shows that xorg is using 50% and mythfrontend is using 50%.

I would really like to know what is different in 8.04 that consumes additional resources.

---

### Post by mrand on 2008-04-29
> **parker13 said:**
> 
I've played with lots of settings to no avail. I'll keep trying...

I had a well running 0.20 Mythbuntu (via apt-get) install on a 7.10/Gutsy system.  After upgrading this past weekend, I too am getting jerky playback... only a second or two of audio and video, then 5 seconds of nothing.  

I haven't had time to play with it yet, but based upon few messages I've managed to find the time to read on the mythtv-users mailing list, many people discover the "new" default video playback profile is unusable on their systems.  Probably a poor choice for a default.  There may also be a problem related to audio sync, although I haven't yet had time to understand what/how.  I don't yet know if either of these are my main playback problem.

   Marc

---

### Post by parker13 on 2008-04-29
I've still got the issue. It doesn't hog CPU, but it still skips a few frames every now and then. I have an Nvidia 5200, which has traditionally been one of the best supported cards for Myth, so I don't think that hardware is necessarily the problem here.

---

### Post by Stevi on 2008-04-29
While watching my recordings I also recognize these skipping-issues. It happens once or twice during one hour. :(

---

### Post by Stevi on 2008-05-05
No ideas??

---

### Post by superm1 on 2008-05-05
Stevi,

The general recommendation is to change to the 'slim' profile and see if that helps...

You already tried?

---

### Post by Stevi on 2008-05-06
Hi superm1,

I already used the slim profile. Now changed it to "normal". Maybe this helps!?

---

### Post by Stevi on 2008-05-20
I tried several changes but nothing solves this issue. It still skips one or two times per recordining to a random point. This is really annoying :(

---

### Post by Stevi on 2008-12-08
I'm still having this problem after upgrading to 8.10. [Here is my log](http://mythbuntu.pastebin.com/m50bdeb36) while it happened four or five times this evening. I watched a recording I had transcoded to MPEG-4. It also happens with recordings I did not transcode. Another log can be found [here](http://mythbuntu.pastebin.com/m75b59330), it happened one time while watching live-tv (at the end there's the output of mythfrontend -v playback). It's really annoying. Any help would be appreciated!

---

