---
title: "Mythbuntu with Myth 0.23 how to install pvr 350 and 150"
date: 2012-10-21
forum: Mythbuntu
---

### Post by Chuckels550 on 2012-10-21
I mistakenly upgraded to Mythtv 0.23 in Mythbuntu 10.04.  I want to either downgrade to Mythtv 0.22 or install the pvr 350 and pvr 150 I currently am using.  All of the documentation for ivtv is out of date.  And I cannot seem to get the CD for 10.04 to be accessed by Synaptic or by the system at boot-up.  How do I resolve this issue?

---

### Post by 4partee on 2012-11-22
> **Chuckels550 said:**
> I mistakenly upgraded to Mythtv 0.23 in Mythbuntu 10.04.  I want to either downgrade to Mythtv 0.22 or install the pvr 350 and pvr 150 I currently am using.  All of the documentation for ivtv is out of date.  And I cannot seem to get the CD for 10.04 to be accessed by Synaptic or by the system at boot-up.  How do I resolve this issue?

I believe you have issues outside of MythTV.  I ran a 10.04 system with a pair of pvr-150s and never needed to look at ivtv.  Myth handled it all just fine.  

Whatever you do, avoid upgrading to 0.25 as there are problems with PVR-x50.  I did that and will be rolling back to 0.24.  The developers are aware of the problem.

HTH;
John

---

### Post by nickrout on 2012-11-22
> **Chuckels550 said:**
> I mistakenly upgraded to Mythtv 0.23 in Mythbuntu 10.04.  I want to either downgrade to Mythtv 0.22 or install the pvr 350 and pvr 150 I currently am using.  All of the documentation for ivtv is out of date.  And I cannot seem to get the CD for 10.04 to be accessed by Synaptic or by the system at boot-up.  How do I resolve this issue?Your post makes little sense. Upgrading from 0.22 to 0.23 shouldn't affect the tuner configuration, it should alll still be there.

What problem are you seeing?

---

### Post by 4partee on 2012-11-23
> **nickrout said:**
> Your post makes little sense. Upgrading from 0.22 to 0.23 shouldn't affect the tuner configuration, it should alll still be there.

What problem are you seeing?

[http://ubuntuforums.org/showthread.php?t=2086984]("http://ubuntuforums.org/showthread.php?t=2086984")

I am having problems with 0.25 and want to know if I can use MCC to roll back to 0.24.

John

---

### Post by nickrout on 2012-11-23
Yes but you will need your backed up 0.24 database

---

### Post by 4partee on 2012-11-23
> **nickrout said:**
> Yes but you will need your backed up 0.24 database

Thanks;

My prior version was 0.23 on Mythbuntu 10.04.  I have never used 0.24. 

I am now running a new install of Mythbuntu 12.04.1 per the iso.  I never had an 0.24 running as I chose 0.25 right away.

I guess this means a new install, right?

John

---

### Post by nickrout on 2012-11-23
> **4partee said:**
> Thanks;

My prior version was 0.23 on Mythbuntu 10.04.  I have never used 0.24. 

I am now running a new install of Mythbuntu 12.04.1 per the iso.  I never had an 0.24 running as I chose 0.25 right away.

I guess this means a new install, right?

JohnYou can restore your 0.23 database to 0.24. So: 

1. look at the database backup and restore page in the wiki. Read and understand, several times. Keep the page open.
2. revert to 0.24 (sudo dpkg-reconfigure mythbuntu-repos, update then upgrade in apt-get etc), then shutdown all myth related programs (mythbackend, mythfrontend, mythtv-setup etc)
3. drop the 0.25 database and restore the 0.23 database (see point 1 above). WARNING you will lose any changes to the database since the time of the 0.23 backup. This includes records of anything you recorded in that time, so thos recordings will be orphaned, let me know if you need to know what to do about those).
4. Start mythtv-setup and let it update the database from 0.23 to 0.24.

---

