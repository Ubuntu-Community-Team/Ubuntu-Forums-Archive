---
title: "ERROR, Compile with V4L support to query audio inputs"
date: 2011-05-05
forum: Mythbuntu
---

### Post by sceo on 2011-05-05
I am getting the above error (ERROR, Compile with V4L support to query audio inputs) in mythtv-setup while trying to add my HD-PVR 1212 capture card.

I upgraded to Natty thinking it would help me get IR Blasting working, and it didn't, so I eventually gave up and got a USB channel changer cable setup from CoolDVR. Now that channel-changing seems to be near working, I'm trying to set up the capture card in mythtv-setup. So now I'm stuck on Natty.

This bug on launchpad :: [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/717717](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/717717)
 :: seems to indicate that the problem is fixed, but it is not fixed for me. 

To verify:

```
$ apt-show-versions mythtv
mythtv/natty uptodate 2:0.24.0+fixes.20110503.a0bb5e9-0ubuntu0mythbuntu3

```

...means I have > 2:0.24.0+fixes.20110410 (refer to bug report - that's the version it's fixed in). I got this by enabling mythbuntu-repos (I think) and updating to latest 0.24 branch (I had to manually adjust the repo path from 0.24.x to 0.24 to make it work).

I have kernel 2.6.38-8-generic (according to uname -r), which I think is the problem.

Patrick in #16 (in above Launchpad bug) apparently had to revert to 2.6.37 in addition to having this fix, but I can't readily do this in Natty, can I? Should I go farther back to 2.6.35 (the next available to me) or should I compile a custom kernel? 

(Incidentally, I think all my main underlying pieces are fine, like I've got the hdpvr driver compiled and working - I can cat /dev/video0 into a test.ts file which plays audio and video back just fine.)

Anyone have any suggestions?

---

### Post by Dan_R on 2011-05-05
I was unable to get the HDPVR working properly on Natty also, this  was on April 29th so it was not fixed as of then. Behaviors with that  bug I noticed it will still record fine in mythtv if you used the RCA inputs for  audio, but Live TV will not work. In the end, instead of waiting I  downgraded back to 10.04(personal preference) and restored my files/database.

You are correct about what the problem actually is and have done everything right, but I do not know of a proper fix, sorry.

---

### Post by LowSky on 2011-05-05
It works fine one11.04 is you install 10.04 and upgrade from there. Yeah I know it isn't perfect but it works.

---

### Post by burtm05 on 2011-05-05
@LowSky - You did your upgrade via Package Manger I assume? Did you also upgrade to Myth .24 or stay with .23?

---

### Post by LowSky on 2011-05-05
Yes upgraded from PM twice (10.04 > 10.10 > 11.04), Also to "ease" the transition I used the Mythbuntu's upgrade repo, from the Mythbuntu website. So yes I'm using .24 (w/ fixes)
here is a lint to the Mythbuntu repos:
[http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)

---

### Post by sceo on 2011-05-05
Was not seeing the behavior described, that is - recordings do work, but without any audio (not surprising).

2011-05-05 17:15:09.500 format_to_mode() does not recognize V4L1

So, now that I have channel-changing working, I'm back where I started. I don't want to come up from 10.04, since I have all my music, etc on this machine.  I will post back if I come up with anything.

EDIT: nope, I'm an idiot, actually. I had my stereo receiver off following a power outage last night. I AM getting audio out of the rear RCA, so that's good enough for me to wait around for a fix, because I can record, which is like my 90% use case. I can always watch TV directly through the passthrough input (as long as I know I'm not recording something).

---

### Post by burtm05 on 2011-05-07
Well the upgrade via PM does seem to do the trick, somewhat. I loaded 10.10, applied package updates via PM, then did an upgrade to 11.04 and also used the Mythbuntu upgrade repo's. Initially when I checked the Capture Card setup the audio input showed correctly. I then added JSON to my update packages to support my perl script for changing channels. I didn't pay close attention to all the affected packages but after installing them my Capture Card started returning the V4L message again. 

Looks like I am back to square one again (sigh)

---

### Post by e7t3 on 2011-05-07
A workaround for me was to ignore that mythtv-setup gives the error trying to query the audio input device - I installed phpmyadmin and in the mythconverg database, manually set the audio device to 2 in the capture card table. HDPVR works fine now using SPDIF.

---

### Post by burtm05 on 2011-05-10
I got mine running using 10.10 with .24+Fixes for the HD-PVR. I am capturing video and audio (I suspect) but now have to work on getting audio out via HDMI.

---

### Post by sceo on 2011-05-10
burtm05 do you nonetheless, even with it working, get the "ERROR, " message in mythtv-setup?  Does Live TV work?

---

### Post by burtm05 on 2011-05-10
Using the setup I mentioned above I do not have the "ERROR..." displaying. It actually allows me to select the Audio Input in mythtv-setup, and yes, Live TV does work sans audio until I have another chance later this week to troubleshoot further

EDIT: I suppose it is worth mentioning when I came up from 10.10 with .23 I did so via Package Manager and Mythbuntu repo's to 10.10 with .24+fixes. The exact order is a little fuzzy from several attempts but basically coming up and ignoring the upgrade to 11.04 worked for me.

---

### Post by tgm4883 on 2011-05-27
If you are experiencing this issue, or other issues regarding ivtv or hdpvr support please test the packages here
[https://launchpad.net/~mythbuntu-bugs/+archive/test4](https://launchpad.net/~mythbuntu-bugs/+archive/test4)

---

### Post by malkiri on 2011-05-30
I had this issue in a clean 11.04 install. Upgrading to those packages fixed the problem in mythtv-setup for me. After compiling the driver as per [http://www.mythtv.org/wiki/HD-PVR#HD-PVR_Driver_Compilation_Howto](http://www.mythtv.org/wiki/HD-PVR#HD-PVR_Driver_Compilation_Howto) (and turning on the cable box!) I'm able to capture video and audio just fine.

---

### Post by tgm4883 on 2011-05-31
Fix should be in the Mythbuntu-repos now. I'm removing the package from the test4 repo

---

### Post by nojstevens on 2011-09-03
> **tgm4883 said:**
> Fix should be in the Mythbuntu-repos now. I'm removing the package from the test4 repo

Hello,

I have this issue with Natty - i've done all the apt-get upgrade/updates but still have the issue. How do I install the new Mythbuntu builds that will fix this issue?

Many thanks for any advice

Jon

---

### Post by tgm4883 on 2011-09-04
> **nojstevens said:**
> Hello,

I have this issue with Natty - i've done all the apt-get upgrade/updates but still have the issue. How do I install the new Mythbuntu builds that will fix this issue?

Many thanks for any advice

Jon

[http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)

---

