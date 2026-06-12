---
title: "mythbuntu 14.04 and schedules direct"
date: 2014-11-16
forum: Mythbuntu
---

### Post by benlyboy on 2014-11-16
Not sure what is going on, but I installed mythbuntu 14.04 about two mounth back and all was great. Then maybe two weeks ago I noticed that I was getting no listing updates. not even if I ran them manually.
i tried everything, but had no luck, so I decided to start over with a new install, and setup. But now when I go into backend set up, and try to set up the video source, I can't.  I put in my user name and password then hit reteave lineups button a box appears and then is gone but no lineup appear in the lower line.

I know my password and username are right as I can use them to log into SD.

I  know the internet is ok as I can open pages ok on a browser on this system.

I know the account works as I have another mythtv system in the house running a very old version (not sure what verson of mythbuntu, but at least 6 years old) and it is working fine.

so really not sure where to go next? 

any help would be great thanks

---

### Post by uteck on 2014-11-16
Did you enable the .27 repository in Mythbuntu Control Center?  SD had to make a severe change to the way the data is downloaded which only works with the latest version of .27.  There is a sticky post at the top of the forum all about it. [http://ubuntuforums.org/showthread.php?t=2248599](http://ubuntuforums.org/showthread.php?t=2248599)

---

### Post by benlyboy on 2014-11-16
Yes sorry meant to say that in my post. I did switch on the 27 repository and do all updates

---

### Post by dannyboy79 on 2014-11-16
i had the same problem, i had noticed that for some reason my username and password were blank within the mythtv-setup. once i filled back in the my credentials for schedules direct everything started working again.

---

### Post by benlyboy on 2014-11-16
Hi there dannyboy, thank you for your reply.
Did you mean the username and password in the video source in the backend setup?
If so they were intact.

---

### Post by boostberry3g on 2014-11-16
I am having the same issue as OP

I have been running Mythbuntu for around 6 months now, and I knew about the Schedules Direct change, but since I was running 0.27, I thought I read it would not affect me. As of Nov 11th It no longer gets EPG details. I figured it would be a good time to upgrade the unit I was using (more ram & larger hard drive), so I installed a fresh Mythbuntu 14.04 onto the unit.  Install goes exactly as detailed in the setup guide until I get to Video Sources, I enter my SD username and password and click retrieve listings, but nothing populates. 

I am going to attempt another install, go back in and ensure that the repositories updated correctly, and then try to setup the backend again. I will report back it this works.

---

### Post by boostberry3g on 2014-11-17
I just did a complete wipe, and started fresh. Installed mythbuntu, and then went into the control center to select "update repositories". Then I was prompted for an update. It actually got hung up on preconfiguring packages, so after about an hour, I just restarted the computer. I turned it back on and went to setup the backend, and when I put the info in for SchedulesDirect, it ended up working.

---

### Post by benlyboy on 2014-11-17
Well my system is now working, I didn't change anything just retried it this morning. I'm thinking that SD had something going on with there server.

---

### Post by dannyboy79 on 2014-11-17
> **benlyboy said:**
> Hi there dannyboy, thank you for your reply.
Did you mean the username and password in the video source in the backend setup?
If so they were intact.
yes, within my source where you enter your SD credentials (username/password), for whatever reason they were completely blank.

---

