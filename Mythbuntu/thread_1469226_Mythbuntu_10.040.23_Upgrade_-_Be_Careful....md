---
title: "Mythbuntu 10.04/0.23 Upgrade - Be Careful..."
date: 2010-05-02
forum: Mythbuntu
---

### Post by colinnwn on 2010-05-02
So I had a Mythbuntu 9.10/0.22 install working quite well, and contrary to my better judgement I decided to go ahead and upgrade.

Following the guidance here
[http://www.mythbuntu.org/10.04/release](http://www.mythbuntu.org/10.04/release)
I believed I needed to enable autobuilds and upgrade to 0.23 before doing a dist upgrade. I was hoping to do this part now, and do the dist upgrade in a couple weeks. If only I could have...

[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)
I'm not sure why the autobuilds page discusses stable -fixes vs. development -trunk, because when configuring auto-builds, you don't get a choice. I still don't know which I am using. I was able to configure for US mirror, and no testing PPA.

After doing the update, it said some packages were held back, and suggested doing a partial dist upgrade. I decided to wait and check things out. Alarmingly Mythweb was borked. All pages were throwing PHP errors. And the upcoming recordings, and recorded programs pages didn't work at all. So I decided to go ahead and do the partial dist upgrade. That didn't fix anything. I wish I had checked if the frontend was working, and how well it worked, at this point, but I didn't. Does this auto-builds thing ever work without screwing up Myth?

After the fact, I discovered here
[http://www.mythbuntu.org/upgrading](http://www.mythbuntu.org/upgrading)
It looks like upgrading manually to 0.23 was unnecessary before doing a dist-upgrade to Lucid. Seems like the website gives incomplete and conflicting information.

Wanting to get my Myth working again, and since I was so committed, I decided to go ahead with the full dist upgrade. Everything seemed to upgrade normally. Of course the full upgrade lost my lirc customizations as it always does. So my remote won't work till I set it back up again. I had a little funniness with nvidia-settings because it couldn't detect my TV's correct resolutions the first time, but on a second reboot it did set it up right. It took a 3rd reboot for Mythweb to respond from the localhost or any other computer on my network.

But **worst of all, the computer has turned into a total sloth.** To launch any programs on the computer, including a terminal, firefox, mythfrontend, or the MCC, takes from 5 to 30 seconds from selecting it. There is always tons of disk churning, even when I am not doing anything on the computer. Mythweb is no longer throwing errors, but using it too is like watching paint dry on either the localhost or another computer. Pages take from 5-15 seconds to load. Watching videos on the frontend, the picture and sound freezes from a half second to several seconds regularly, before continuing to play.

Running ps -aux with nothing running on the desktop, and only the backend explicitly running, shows mysql taking 15% of the CPU and X taking 21% of the CPU always. Sometimes PHP shows up taking about 61% of the CPU, but sometimes it is below 1%. I can't say I remember from my last install, but this seems high. Sometimes Top shows X taking 37% of CPU, the new screensaver taking 35% of CPU, mysql taking 18% of CPU and PHP taking 64% of CPU and 79% of memory, but other times, the figures seem normal.

I'm not sure what is going on. But right now I am trying to decide whether I should turn Myth off for a couple weeks and see if updates fix the problems (this has sometimes worked for me in the past), or if it is worth trying to salvage the recordings I have on Myth and restore them on a fresh install (I've never tried restoring old settings and recordings on a new install), or if I'm going to not worry about my old recordings, blow everything away, and start from ground zero again.

Not fun times. Ths will teach me to never again do a dist upgrade for the first several weeks after launch, and to always do lots of research on how things are shaking out for other people. For everyone else contemplating upgrading now, I suggest learning from me.

---

### Post by tgm4883 on 2010-05-02
Please show me the conflicting website information so I can change it. Thanks.

---

### Post by colinnwn on 2010-05-02
[http://www.mythbuntu.org/10.04/release](http://www.mythbuntu.org/10.04/release)
"this release is only compatible with MythTV 0.23 systems. Previous Mythbuntu releases can be upgraded to MythTV 0.23 with the builds located at http://www.mythbuntu.org/auto-builds"

Right or wrong, this makes it sound like if you are running 9.10/0.22, you need to update to 0.23 before upgrading to 10.04.

I'd word it, assuming this is correct, something like - 
"this release comes with Myth 0.23 and can not be downgraded to 0.22. If you need 0.23 on an older release, use auto-builds, but this is unnecessary if you are upgrading to 10.04. See [http://www.mythbuntu.org/upgrading](http://www.mythbuntu.org/upgrading) regarding upgrading older releases to 10.04."


[http://www.mythbuntu.org/upgrading](http://www.mythbuntu.org/upgrading)
"You do not need to upgrade to auto-builds prior to upgrading to the next Mythbuntu release. This will be taken care of during the upgrade process."

This is pretty clear. Just have to find it, when other places on the site also talk about upgrading. At some point I think it is normal to say I've read enough, time to try it out.


[http://www.mythbuntu.org/MythTV-compatibility](http://www.mythbuntu.org/MythTV-compatibility)
"If you are looking to upgrade your Mythbuntu 9.04 (or earlier) system to 9.10, and are currently running 0.21, you do not need to upgrade to 0.22 first. MythTV will automatically be upgraded to 0.22 with the upgrade to 9.10. See Upgrading for more info.

Conversely, if you wish to stay on 9.04, you can upgrade just the MythTV related packages by enabling the Mythbuntu Repos (see Auto Builds for more details)."

This is just out of date. And rather than spread references to upgrading several places, I'd simply delete it all and have a link there to 
[http://www.mythbuntu.org/upgrading](http://www.mythbuntu.org/upgrading)


[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)
Since there is no "stable" & "development" or "-fixes" and "-trunk" option in auto-builds configure, I'd say it is premature to talk about it at the very beginning of the section. If you've done it before, it makes sense. But if it is the first time and you are trying to figure out what is going on, it is out of context. 

There is also no specific indication here when trunk becomes fixes. Not that it is really necessary, but it just doesn't help bring the section into context when there is no indication what version is currently fixes and trunk. If you feel it is necessary to start the section off this way, then in that first section I'd link to the much clearer reference that is currently only in the FAQ - [http://www.mythbuntu.org/auto-builds-explained](http://www.mythbuntu.org/auto-builds-explained)

---

### Post by wolowina on 2010-05-02
i did dist upgrade : 
[http://www.mythbuntu.org/upgrading](http://www.mythbuntu.org/upgrading) -> Upgrading between Mythbuntu Releases

it upgraded to 10.04 but still with 0.22 mythtv, and from what i understood i supposed to upgrade all ?

---

### Post by gslug79 on 2010-05-02
> Alarmingly Mythweb was borked. All pages were throwing PHP errors. And the upcoming recordings, and recorded programs pages didn't work at all.

I had the same problem after upgrading to Mythtv 0.23 on Ubuntu 9.10. I noticed that where Mythweb is complaining about protocol version, the Mythtv version shown is older than the Mythweb one - it appears that the upgrade has not restarted mythtv-backend so although 0.23 has now been installed, 0.22 is still running. Restarting the backend fixed Mythweb for me.

I'll probably find other issues, but things seem OK at the moment.

---

### Post by LowSky on 2010-05-02
MythTV 0.23 isn't working well for me either.
My issues include TV station data not being entered correctly by mythconverge, Live TV crashing when changing channels, and HDMI sound has to be hacked to work.

I'm going back to Mythbuntu 9.10

---

### Post by tgm4883 on 2010-05-02
> **colinnwn said:**
> [http://www.mythbuntu.org/10.04/release](http://www.mythbuntu.org/10.04/release)
"this release is only compatible with MythTV 0.23 systems. Previous Mythbuntu releases can be upgraded to MythTV 0.23 with the builds located at http://www.mythbuntu.org/auto-builds"

Right or wrong, this makes it sound like if you are running 9.10/0.22, you need to update to 0.23 before upgrading to 10.04.

I'd word it, assuming this is correct, something like - 
"this release comes with Myth 0.23 and can not be downgraded to 0.22. If you need 0.23 on an older release, use auto-builds, but this is unnecessary if you are upgrading to 10.04. See [http://www.mythbuntu.org/upgrading](http://www.mythbuntu.org/upgrading) regarding upgrading older releases to 10.04."

While that statement is correct, it is not the info that is trying to be conveyed there. 

"this release is only compatible with MythTV 0.23 systems. Previous Mythbuntu releases can be upgraded to MythTV 0.23 with the builds located at http://www.mythbuntu.org/auto-builds"

This means that in multi-system environments, you will need to be on the same version of MythTV on all of them (not the same version of Mythbuntu). IE. you could have a 10.04 system (0.23) and a 9.10 system (0.22) and they would not be compatible unless you upgraded your 9.10 system to 0.23. Please let me know a better way of saying that without writing a book.

> **colinnwn said:**
> 
[http://www.mythbuntu.org/upgrading](http://www.mythbuntu.org/upgrading)
"You do not need to upgrade to auto-builds prior to upgrading to the next Mythbuntu release. This will be taken care of during the upgrade process."

This is pretty clear. Just have to find it, when other places on the site also talk about upgrading. At some point I think it is normal to say I've read enough, time to try it out.


It's pretty clear because I rewrote it at 2AM this morning after reading your post :P


> **colinnwn said:**
> 
[http://www.mythbuntu.org/MythTV-compatibility](http://www.mythbuntu.org/MythTV-compatibility)
"If you are looking to upgrade your Mythbuntu 9.04 (or earlier) system to 9.10, and are currently running 0.21, you do not need to upgrade to 0.22 first. MythTV will automatically be upgraded to 0.22 with the upgrade to 9.10. See Upgrading for more info.

Conversely, if you wish to stay on 9.04, you can upgrade just the MythTV related packages by enabling the Mythbuntu Repos (see Auto Builds for more details)."

This is just out of date. And rather than spread references to upgrading several places, I'd simply delete it all and have a link there to 
[http://www.mythbuntu.org/upgrading](http://www.mythbuntu.org/upgrading)


Fixed, let me know if that is still confusing

> **colinnwn said:**
> 
[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)
Since there is no "stable" & "development" or "-fixes" and "-trunk" option in auto-builds configure, I'd say it is premature to talk about it at the very beginning of the section. If you've done it before, it makes sense. But if it is the first time and you are trying to figure out what is going on, it is out of context. 

There is also no specific indication here when trunk becomes fixes. Not that it is really necessary, but it just doesn't help bring the section into context when there is no indication what version is currently fixes and trunk. If you feel it is necessary to start the section off this way, then in that first section I'd link to the much clearer reference that is currently only in the FAQ - [http://www.mythbuntu.org/auto-builds-explained](http://www.mythbuntu.org/auto-builds-explained)

Removed. Also, I have added some stuff to debconf/MCC for configuring mythbuntu-repos. Check that out if you want and let me know if it is confusing as well.

:EDIT:

Forgot to add that version of Mythbuntu-repos is 7.5

---

### Post by kja999 on 2010-05-02
Although everyone should be careful on this upgrade (as any other), I think the upgrade (to myth .23) before changing to 10.04 is sensible as I have been burnt by the same during the 9.10 upgrade.
Its only logical to update to the new myth version on a known platform and then update. The main reason is to get a working version and get a decent backup of that database schema.

I have had no issues with the upgrade, took around an hour max to have a working system back up.

---

### Post by colinnwn on 2010-05-02
> **gslug79 said:**
> \it appears that the upgrade has not restarted mythtv-backend so although 0.23 has now been installed, 0.22 is still running. Restarting the backend fixed Mythweb for me.
I'm pretty sure I restarted the whole computer after the auto-build update, but before the upgrade, and Mythweb still didn't work.

> **LowSky said:**
> I'm going back to Mythbuntu 9.10
Was yours a fresh install, or an upgrade? Wondering if I should try a fresh 10.04 install, or go back to 9.10.

---

### Post by colinnwn on 2010-05-12
Wanted to update the situation. 

After seeing a post on EIT scanning bringing another user's Mythbox to its knees after 10.05 update, and disabling it fixed all his issues, I tried disabling EIT scan on mine. The computer seems about 50% better (as compared to how it was on 9.10), but there was still significant sluggishness in all apps, and playback had regular video and audio stuttering. 

I then did a package update and it seemed about 80% better. Apps seemed to run at mostly the normal speed, and I only experienced one playback stutter in an hour show. Mythweb loaded fast enough to be tolerable, but slower than it used to. Finally I added auto-builds for 0.23, but that didn't seem to make a difference either way. Thinking that was good enough to live with, I was going to wait and see if subsequent updates improved it even more. 

Last night it was scheduled recording 2 shows, and I tried to watch another show. There was constant long and painful playback stuttering. This never happened on 9.10. I could record 2 shows, and I'd never know the difference watching a 3rd show. Load averages in 9.10 would run 1-1.6, in 10.04 for me they run 2.3-3.5. It isn't a worthwhile PVR in this condition. 

So it looks like I will have to blow the install and reload 10.04 from scratch. I hope I have time to do it this weekend, and that a fresh load will work as well as 9.10 did for me. Otherwise I'll have to try to figure out how to downgrade.

---

### Post by bwatson on 2010-05-12
I'll 2nd the OP's sentiments with regards to the upgrade.  I recently (4 days ago) upgraded my 9.10/0.22 backend (which I regarded as nearly bullet proof and a great work horse) to 10.04/0.23.  In doing so, I've run into the screen resolution issue mentioned.  Annoying but an easy fix.  I've got 1xHauppage PVR-350 and 2xHauppage PVR-500 (yeah I like to be able to record lots of channels at once).  At random times, all of my encoders are missing, so upcoming recordings are blank and will be missed.  I restart the backend and the encoders come back, but again this is annoying and means I can't leave my system unattended for long periods of time.  My Hauppage remote still doesn't work.  I don't recall having to customize anything to get it to work in 9.10 or the previous versions of Mythbuntu.  It always "just worked", which I loved.  Again, kind of annoying to be forced to "remote desktop" or use a wireless keyboard, but I'm hopeful a future upgrade will resolve this.  My major point of concern isn't so much performance related, as this appears to be working decently on old hardware (AMD XP 2500+ with 1GB RAM).  I continually run into this "Video frame buffer could not fill in a timely manner" (or something like that error).  I get this error while playing certain DVDs locally on the backend via the DVD-ROM and always run into the error when trying to use the internal player to play Videos stored on a NAS.  I've I could get the Hauppage remote functional again and cure this mysterious video buffering issue, I'd be a happy camper overall.  Ben

---

### Post by optimusprime8 on 2010-05-13
My system is completely borked after trying to upgrade a 9.10 ubuntu system to .23 also.  

I also did the "partial upgrade" mentioned above, when it wouldn't do a full upgrade.  Through Ubuntu's Update Manager.

It doesn't start mythtvbackend after a reboot.  I can start the backend manually, but when I try to play a video the frontend crashes.

I was able to successfully upgrade the database as I can see all my old content, it just won't play it.  It also looks like I may not have gained any new features.  Am I maybe still running the old frontend?

How do I fix this without blowing everything away?  This PVR was a real pain to setup when I originally built it some time ago, I'm not really wanting to start from scratch.

---

### Post by tgm4883 on 2010-05-13
> **optimusprime8 said:**
> My system is completely borked after trying to upgrade a 9.10 ubuntu system to .23 also.  

**I also did the "partial upgrade"...**

Don't do partial upgrades ](*,)

---

### Post by colinnwn on 2010-05-13
> **tgm4883 said:**
> Don't do partial upgrades ](*,)

Well after enabling autobuilds in 9.10 and updating, Synaptic suggests a partial upgrade. 

I didn't do it at first. Since Myth quit working after enabling autobuilds, I think reasonably assumed Synaptic knew what it was talking about, or at least I had nothing to lose. If partial upgrades are such a head banging no-no, I think that should be boldly noted on the MythBuntu website under enabling auto-builds.:confused:

---

### Post by tgm4883 on 2010-05-13
> **colinnwn said:**
> Well after enabling autobuilds in 9.10 and updating, Synaptic suggests a partial upgrade. 

I didn't do it at first. Since Myth quit working after enabling autobuilds, I think reasonably assumed Synaptic knew what it was talking about, or at least I had nothing to lose. If partial upgrades are such a head banging no-no, I think that should be boldly noted on the MythBuntu website under enabling auto-builds.:confused:

Maybe they should rename it to something that clarifies that it will not be a full upgrade?

When it states that it is going to do a partial update, you might want to check what it is going to uninstall

---

### Post by colinnwn on 2010-05-13
Well it was pretty clear it wasn't a full upgrade, and it was suggested by Synaptic, so I don't know if it is something MythBuntu could control? 

My impression from the MythBuntu website was that before you upgraded to 10.04, you needed to enable autobuilds and get on Myth 0.23. I later found out that was not necessary. But another poster in this thread said they felt like it was good practice anyway. 

Since autobuilds broke my MythBuntu 9.10, I was hoping doing the Synaptic recommended partial upgrade would fix it, maybe cure a depends or something. After I got 9.10/0.23 working, I was planning to do the full 10.04 upgrade anyway. But at every step things got worse and not better.

Not sure that if the partial upgrade uninstalled anything, that it is the root cause of my problem. Everything is working, it is just working like the computer is smoking pot. Things happen slowwwwwwwly.

---

