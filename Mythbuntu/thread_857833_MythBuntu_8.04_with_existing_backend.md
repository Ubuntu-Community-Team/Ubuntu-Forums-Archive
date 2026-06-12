---
title: "MythBuntu 8.04 with existing backend"
date: 2008-07-12
forum: Mythbuntu
---

### Post by jaimesmith on 2008-07-12
I just downloaded and installed Mythbuntu 8.04 on one of my front ends and it installed beautifully.  Thanks everyone involved.  The problem is, I have a backend and two other frontends running MythTV 0.20.  What is my best option, upgrade a ton of systems to MythTV 0.21, or get MythTV 0.20 on Mythbuntu 8.04?  The one running 8.04 wouldn't install 7.10 (no video when booting from the CD).  I was recently running FC8 on it with MythTV manually installed, but I was having a lot of problems with sound drivers and it had a lot of rough edges.

---

### Post by nickrout on 2008-07-13
firstly I don't know if you can get 0.20 packages for 8.04.

0.21 has some great new feature.

I'd go with upgrading to 0.21.

---

### Post by theophile on 2008-07-13
To take the other side, I'd recommend not upgrading if your system is working. A lot of people have reported upgrades that break their systems, particularly for playback. I upgraded from .20 to .21 and I still haven't gotten playback to work without stutters, even though I never had a problem with .20.

If you have to install an old version of mythbuntu for the new frontend, I'd do that.

---

### Post by jaimesmith on 2008-07-13
But the Mythbuntu 7.10 install CD doesn't boot on the new frontend, that's why I have this choice to make in the first place.  I could throw away the hardware and try again, but how can I be sure that 7.10 will install on it?  That's how I got in this mess in the first place.  I figured anything with NVidia graphics would be good, but it turns out that the GeForce 7025 is an exception.

---

### Post by theophile on 2008-07-13
What about 6.04?

---

### Post by mrand on 2008-07-14
> **jaimesmith said:**
> But the Mythbuntu 7.10 install CD doesn't boot on the new frontend, that's why I have this choice to make in the first place.  I could throw away the hardware and try again, but how can I be sure that 7.10 will install on it?  That's how I got in this mess in the first place.  I figured anything with NVidia graphics would be good, but it turns out that the GeForce 7025 is an exception.

The only thing you can be "sure" about is death and taxes.  But if it is a new install, you can try and see without losing anything, right?  Have you tried the alternate CD for 7.10?  Then add mythbuntu with 0.20 from the repositories.

If that doesn't work, or if you really want to be on 0.21, then I'd suggest just upgrading the old systems to 0.21 and leaving the OS at 7.10.  You can do this by subscribing to the "weekly" build repository.  Doing this should greatly decrease the likelihood of an upgrade problem (I believe the majority of problems are related to Ubuntu 8.04, which appears to have introduced some video related regressions for a few configurations).

[INDENT]Marc[/INDENT]

---

### Post by superm1 on 2008-07-14
> **theophile said:**
> To take the other side, I'd recommend not upgrading if your system is working. A lot of people have reported upgrades that break their systems, particularly for playback. I upgraded from .20 to .21 and I still haven't gotten playback to work without stutters, even though I never had a problem with .20.

If you have to install an old version of mythbuntu for the new frontend, I'd do that.
The most common cause for the stuttering playback is the deinterlacer or not upgrading your kernel.  If you aren't doing your updates, please do them!

---

### Post by copycat on 2008-08-17
> **superm1 said:**
> The most common cause for the stuttering playback is the deinterlacer or not upgrading your kernel.  If you aren't doing your updates, please do them!

Hey Superm1....I had this issue too with stuttering video.  I had it from an upgrade 7.10 to 8.04 and also from a clean install. Because a lack of time (kids wanna see recordings) I've installed a clean 7.10 that works.  Sometim it crashes when previewing a recording but that's no issue.

A good friend of me started last week with a fresh 8.04.1 mytbuntu and had the same issue.  I suppose the issue isn't solved yet in the latest update?
Otherwise I'll reïnstall everything tommorow :-)

---

### Post by superm1 on 2008-08-17
> **copycat said:**
> Hey Superm1....I had this issue too with stuttering video.  I had it from an upgrade 7.10 to 8.04 and also from a clean install. Because a lack of time (kids wanna see recordings) I've installed a clean 7.10 that works.  Sometim it crashes when previewing a recording but that's no issue.

A good friend of me started last week with a fresh 8.04.1 mytbuntu and had the same issue.  I suppose the issue isn't solved yet in the latest update?
Otherwise I'll reïnstall everything tommorow :-)
If it's stuttering only during livetv with the program guide open, that's a known issue with a bug opened.

If it's other places, you need to tweak with settings.  Between the deinterlacer, opengl vsync settings, using the nvidia driver etc.

---

### Post by copycat on 2008-08-17
Ok it's  only while playing recorded tv.  I don't use live tv.
Where can I find these settings?  We both use ATI.

kind regards,

Christian

---

### Post by Archmage on 2008-08-18
> **jaimesmith said:**
> The one running 8.04 wouldn't install 7.10 (no video when booting from the CD).

Try to install it from the alternate CD.

---

### Post by superm1 on 2008-08-18
> **copycat said:**
> Ok it's  only while playing recorded tv.  I don't use live tv.
Where can I find these settings?  We both use ATI.

kind regards,

Christian
For ATI, I'm not sure these options are tweakable regarding vsync.  You can change the deinterlacer in the TV settings menu of the frontend however.

---

### Post by copycat on 2008-08-18
> **superm1 said:**
> For ATI, I'm not sure these options are tweakable regarding vsync.  You can change the deinterlacer in the TV settings menu of the frontend however.

Ok thanks for the support!

I'm going to look for another haupauge mce500 card and wil try to install it in my frontend.  

Kind regards

---

### Post by tgm4883 on 2008-08-18
> **Archmage said:**
> Try to install it from the alternate CD.

Being that there was no alternate 7.10 CD I find that would be kind of difficult. 

However, if a regular Ubuntu 7.10 CD boots he could install that and then the mythbuntu-desktop package

---

