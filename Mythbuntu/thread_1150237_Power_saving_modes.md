---
title: "Power saving modes"
date: 2009-05-05
forum: Mythbuntu
---

### Post by WrathofthePenguin on 2009-05-05
I've been using a Tivo for quite some time, and I'm wondering if Mythbuntu will spin down the drives when they are not in use.

I've been running Ubuntu for several years on most of my home PCs (and several work PCs), but I've never really noticed (or researched) if there's a way for the hard drive to spin down when it's not in use.

Are there any other power saving modes that I can take advantage of?

---

### Post by SiHa on 2009-05-06
hdparm is where you want to look, I think. The '-s' switch allows you to specify a spindown time.

Although check [[COLOR="Blue"]_this_[/COLOR]](http://ubuntuforums.org/showthread.php?t=1143795) post for some issues.

---

### Post by tobiz on 2009-05-06
> **SiHa said:**
> hdparm is where you want to look, I think. The '-s' switch allows you to specify a spindown time.

Although check [[COLOR="Blue"]_this_[/COLOR]](http://ubuntuforums.org/showthread.php?t=1143795) post for some issues.
It seems different discs behave in different ways to the hdparm command, even from the same manufacturer but different size models. So far I can get my Samsung 500GB Spinpoint discs to spindown but not to spindown again without issuing another hdparm command once spun up;  not really much use! The answer seems to be to build a daemon which forces spindown.  There is such a daemon called 'spindown' [[COLOR="Blue"]here[/COLOR]]("http://code.google.com/p/spindown/") but I've not tried it yet.

---

### Post by SiHa on 2009-05-07
Thanks for the info, I've been meaning ot have a play with spindown myself soon, I'll have a look.

---

### Post by 4dognight on 2009-05-07
Or, you can setup your system to use hibernate or suspend.

---

### Post by Meph1st0 on 2009-05-07
Isn't there a way to take this a little further? I thought I'd read about the ability for MythTV to incorporate Wake-On-LAN to turn on or off the PC when it's needed for recording a show.  If it's not recording or if a show isn't being played then it'll turn itself off, but then based on it's scheduling it'll wake itself up to record a show that's scheduled.

---

### Post by tobiz on 2009-05-07
> **Meph1st0 said:**
> Isn't there a way to take this a little further? I thought I'd read about the ability for MythTV to incorporate Wake-On-LAN to turn on or off the PC when it's needed for recording a show.  If it's not recording or if a show isn't being played then it'll turn itself off, but then based on it's scheduling it'll wake itself up to record a show that's scheduled.
Yes I've seen mention of such features and intend to try them at some point. I'm taking things one step at a time. My first requirement is backup and having the backup disc spun down most of the time seems a good idea. Ultimately I'd like to have my main myth backend/frontend server powered down until: a) it needs to record; b) run the backup. I believe mythtv has the facilities for a), provided the m/b supports it, I'm not so sure about b). As to how the myth server gets turned on, on-demand, my plan is to use a WiFi laptop and wake-on-lan to switch the server on. For now just doing the backup and the discs staying cool is but a first step in the plan.

---

### Post by laffinet on 2009-05-07
That's pretty much what I (and others have done).

My Mythbox shuts down when idle and comes up for recordings and at pre-determined times.

[Here's]("http://ubuntuforums.org/showthread.php?t=1072905") a thread that I started and hopefully explains what I've done.

Let me know if you've got any problems.

---

### Post by 4dognight on 2009-05-08
To expand, What I have is 1 MBE and 2 slave BE/FE combos.
I have configured Mythtv to Suspend/hibernate all 3 when its idle(MBE), and wakeup the MBE and Slaves for recordings( I have tuners in all 3). I have a script that will use wakeonlan to wake the others up when one is awaken. This could have been for an upcoming recording, or if I manually wake one.
Myth will stay up and running on all 3 as long as even one of them is running mythfrontend.

Mythtv has some builtin configurables for waking up the MBE , but I was unsuccesful in configuring them . I just use some scripts configured to run when being awaken from hibernate/suspend. 

If someone really wants to know the details(I left out some out for brevity, including the scripts), I will reply with them.

---

