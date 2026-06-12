---
title: "Banshee will not detect iPod Classic 80GB"
date: 2010-01-03
forum: Multimedia Software
---

### Post by divinityofnumber on 2010-01-03
Hello all, 

I have an 80GB iPod Classic that Banshee did recognize before I made the move from Ubuntu 9.04 to 9.10, but now it will not.

The iPod is visible on my desktop, and I can mount it, eject it, open it up and browse through it, but Banshee will not detect it. 

Help!

---

### Post by boombox1387 on 2010-01-09
This is a really common issue for Ubuntu 9.10 users.  9.10 changed the way disks are mounted, and Banshee was a little behind.  The issue has been fixed in recent versions of Banshee (and, more specifically, its iPod-detecting tool called Podsleuth).

Adding [the Banshee Daily Build PPA]("https://launchpad.net/~banshee-team/+archive/banshee-daily") to your software sources will let you upgrade to a version of Banshee that doesn't have this issue.

If you don't want to do things that way, you can turn off auto-mounting.  Run (Alt-F2) gconf-editor.  Navigate to apps > nautilus > preferences and uncheck the media_automount box.  This will keep devices from automatically mounting, which will let Banshee see the iPod.

Good luck, and I hope this helps.

---

### Post by Adbekunkus on 2010-01-26
boombox: won't that keep other media to mount automatically? i have all my music on a USB drive and I really like th idea of automounting for this device... is there an option in which I can select what devices mount automatically? Thankx

---

### Post by boombox1387 on 2010-01-26
> **Adbekunkus said:**
> boombox: won't that keep other media to mount automatically? 

Unfortunately yes.  If you turn automounting off, it's off for all devices.

> **Adbekunkus said:**
> i have all my music on a USB drive and I really like th idea of automounting for this device... is there an option in which I can select what devices mount automatically? Thankx

Automounting is all or nothing.  The good news is, Banshee 1.5.3 is scheduled for release tomorrow!  Don't even worry about that whole automounting thing; just get a new Banshee that doesn't have broken iPod support. :)

---

### Post by Solarisphere on 2010-01-30
I just installed the [banshee-team ppa]("https://edge.launchpad.net/~banshee-team/+archive/ppa") and updated my system and everything works again! My god is it nice to be able to sync an ipod from Bnashee.

There's a bunch of other useful features that have been added as well (watching folders is my favourite).

---

### Post by Adbekunkus on 2010-02-05
I installed the banshee team ppa and updated Banshee and iPod is now detected, but Banshee doesn't recognize the music in it: in the graph that indicates the type and amount of data in my ipod, it's all read as "other" (I attached the screen print). Any ideas of why this happens? Thanx a lot.

---

### Post by cdeobald on 2010-02-07
I was glad to find this thread, as it fits my situation exactly (Karmic, Classic 80GB) buy I'm sorry to say that, unfortunately, none of this is working for me.  I disabled media mounting in Nautilus, installed the newest Banshee (1.5.3) and nothing.

I have even resorted to uninstalling and re-installing Banshee, rebooting several times, disconnecting and reconnecting the Ipod  several times, and no love.

Just curious, if I examine the version information under Help > Version Information, Banshee-related files report as 1.5.0.0.  Should this be?

Also, with auto-mounting of media disabled in Nautilus, the Ipod still appears in the sidebar of the Nautilus window, but as near as I can tell is not actually mounted unless I click on it.  Is this the behaviour I should be expecting?

Any help would be appreciated.

---

### Post by boombox1387 on 2010-02-07
> **cdeobald said:**
> 

Just curious, if I examine the version information under Help > Version Information, Banshee-related files report as 1.5.0.0.  Should this be?


I don't know how the versioning information there is decided, but I regularly build my Banshee from source, and most of the versions for me also say 1.5.0.0, so that shouldn't be a problem.

> **cdeobald said:**
> 
Also, with auto-mounting of media disabled in Nautilus, the Ipod still appears in the sidebar of the Nautilus window, but as near as I can tell is not actually mounted unless I click on it.  Is this the behaviour I should be expecting?

Yes, this is the expected - slightly less convenient - behavior that goes along with disabling media_automount.  Devices show up when you plug them in, but they aren't mounted until you click on them.  Banshee won't be able to see the device until you've mounted it.  Also, if you have Banshee 1.5.3, you don't need to have media_automount off anymore.

If Banshee still can't see your iPod, even when you've mounted it in Nautilus, you might want to open up a terminal and run 'podsleuth --rescan'.  Podsleuth is Banshee's tool for detecting iPods, so it will let you know if you find anything.  If the problem remains, post back here and I'll be happy to help as much as I can.

---

### Post by boombox1387 on 2010-02-07
> **Adbekunkus said:**
> I installed the banshee team ppa and updated Banshee and iPod is now detected, but Banshee doesn't recognize the music in it: in the graph that indicates the type and amount of data in my ipod, it's all read as "other" (I attached the screen print). Any ideas of why this happens? Thanx a lot.

Hmm, well at least it sees your iPod, so that's a good start.  Have you ever used your iPod with Banshee before?  or was it last used with iTunes?  With some iPods, Banshee won't be able to read the iTunes database format, but if that's the case, Banshee should have offered to rebuild the database for you.

---

### Post by cdeobald on 2010-02-07
Thanks for the help.  Mounting the Ipod and running podsleuth did the trick.  The Ipod had never been synced with Banshee.  I had been using Itunes running on XP within Virtualbox ever since Songbird abandoned Ipod support.  I've been looking for solution within Linux for a while now, and I'm hoping that Banshee fits the bill.

As I'm writing this, Banshee is performing a re-build on the database, so we'll see how things go from there.

If I have to run podsleuth each time, I'm OK with that, but it may be that once I've synced with Banshee once it will have a better time recognizing the beast.

Thanks again.

---

### Post by boombox1387 on 2010-02-07
> **cdeobald said:**
> Thanks for the help.  Mounting the Ipod and running podsleuth did the trick.  The Ipod had never been synced with Banshee.  I had been using Itunes running on XP within Virtualbox ever since Songbird abandoned Ipod support.  I've been looking for solution within Linux for a while now, and I'm hoping that Banshee fits the bill.

As I'm writing this, Banshee is performing a re-build on the database, so we'll see how things go from there.

If I have to run podsleuth each time, I'm OK with that, but it may be that once I've synced with Banshee once it will have a better time recognizing the beast.

Thanks again.

I'm guessing that you won't have this problem each time.  I rebuilt my iPod with iTunes on XP a week ago because something had gone wrong with the database awhile back.  When I plugged it into Banshee, Banshee didn't see the iPod until I ran manually podsleuth.  I haven't had to do this since the first run.  I figured the first time was a fluke, but apparently it's not.  I guess that means this problem may have earned itself a bug report...

---

### Post by erikacoustik on 2010-03-16
Similar problem, 
I believe it stems from lucid lynx completely removing HAL.  is there a workaround for podsleuth now that HAL is gone?

---

### Post by boombox1387 on 2010-03-16
> **erikacoustik said:**
> Similar problem, 
I believe it stems from lucid lynx completely removing HAL.  is there a workaround for podsleuth now that HAL is gone?

I haven't messed around with Lucid much yet - I'm waiting for the Beta in a couple days :) - so I can't say anything with much certainty, but here are some helpful links for you:

[https://bugzilla.gnome.org/show_bug.cgi?id=612616](https://bugzilla.gnome.org/show_bug.cgi?id=612616)
This is a Banshee bug report relating to HAL's deprecation. Not sure if/how this relates to Podsleuth, but it might.

[https://bugzilla.gnome.org/show_bug.cgi?id=612890](https://bugzilla.gnome.org/show_bug.cgi?id=612890)
This bug was filed with Motorola Droids in mind, but I would assume that much of the same thing applies to iPods as well.  If you look at comments >= 8, there's some talk about how to start HAL in Lucid.  The results (for the Droid at least) don't seem too positive yet, but it's a start.

In a couple days I'll start doing some testing on Lucid, and I have an iPod, so I'll let you know if I figure anything out.  (Likewise, if you get things working, please post back here, as I'm sure I'll run into frustrations!)

---

