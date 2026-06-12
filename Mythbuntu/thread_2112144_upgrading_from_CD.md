---
title: "upgrading from CD"
date: 2013-02-03
forum: Mythbuntu
---

### Post by neutron68 on 2013-02-03
There is supposed to be a way to upgrade Mythbuntu to the next version by downloading the installer CD ISO file, burning a CD and having the update come from the CD, rather than over the Internet.  This is to prevent an over-the-Internet upgrade which literally takes multiple hours.

My goal was to go from 11.04 to 11.10 to 12.04.

I followed this:
[http://www.liberiangeek.net/2012/04/upgrade-to-ubuntu-12-04-from-11-10-using-ubuntu-cd-dvd/](http://www.liberiangeek.net/2012/04/upgrade-to-ubuntu-12-04-from-11-10-using-ubuntu-cd-dvd/)

They instruct you to boot the pc with the CD, click Install Mythbuntu, and then choose Upgrade from XX to XX.

I backed up my boot partition with clonezilla so I could go back to a working 11.04 if the upgrade went bad.
I didn't back up the recordings partition (/var/lib/mythtv) because it is huge, and it isn't supposed to get touched during an upgrade, anyway.

I put the CD in the drive and booted up to the installer screens.  
All seemed to proceed OK and the upgrade even kept my desktop wallpaper and a few folder icons I put on the desktop.

When I got done, I found that ALL my recordings were gone!!
The "/var/lib/mythtv/pretty" folder I put in my last install is gone.

It looks like the installer wiped out the /var/lib/mythtv partition and rebuilt it!

WHAT KIND OF UPGRADE IS THAT?  

Isn't the idea of upgrading to only change the operating system files and keep your recordings, etc.???

Eric

---

### Post by tgm4883 on 2013-02-04
> **neutron68 said:**
> There is supposed to be a way to upgrade Mythbuntu to the next version by downloading the installer CD ISO file, burning a CD and having the update come from the CD, rather than over the Internet.  This is to prevent an over-the-Internet upgrade which literally takes multiple hours.

My goal was to go from 11.04 to 11.10 to 12.04.

I followed this:
[http://www.liberiangeek.net/2012/04/upgrade-to-ubuntu-12-04-from-11-10-using-ubuntu-cd-dvd/](http://www.liberiangeek.net/2012/04/upgrade-to-ubuntu-12-04-from-11-10-using-ubuntu-cd-dvd/)

They instruct you to boot the pc with the CD, click Install Mythbuntu, and then choose Upgrade from XX to XX.

I backed up my boot partition with clonezilla so I could go back to a working 11.04 if the upgrade went bad.
I didn't back up the recordings partition (/var/lib/mythtv) because it is huge, and it isn't supposed to get touched during an upgrade, anyway.

I put the CD in the drive and booted up to the installer screens.  
All seemed to proceed OK and the upgrade even kept my desktop wallpaper and a few folder icons I put on the desktop.

When I got done, I found that ALL my recordings were gone!!
The "/var/lib/mythtv/pretty" folder I put in my last install is gone.

It looks like the installer wiped out the /var/lib/mythtv partition and rebuilt it!

WHAT KIND OF UPGRADE IS THAT?  

Isn't the idea of upgrading to only change the operating system files and keep your recordings, etc.???

Eric

Did you use a 12.04 or 12.04.1 ISO? Or did you use a 11.10 ISO first to go from 11.04 to 11.10 to 12.04?

---

### Post by neutron68 on 2013-02-04
> **tgm4883 said:**
> Did you use a 12.04 or 12.04.1 ISO? Or did you use a 11.10 ISO first to go from 11.04 to 11.10 to 12.04?
I used the 11.10 32-bit ISO as my first upgrade step.  
It's my understanding that you must upgrade 1 version at a time, with no version skips.

Eric

---

### Post by tgm4883 on 2013-02-04
> **neutron68 said:**
> I used the 11.10 32-bit ISO as my first upgrade step.  
It's my understanding that you must upgrade 1 version at a time, with no version skips.

Eric

You probably got hit with this then  [https://bugs.launchpad.net/mythbuntu/+bug/992241](https://bugs.launchpad.net/mythbuntu/+bug/992241)

I didn't even know there was an upgrade from CD option back in 11.10

---

### Post by neutron68 on 2013-02-04
> **tgm4883 said:**
> You probably got hit with this then  [https://bugs.launchpad.net/mythbuntu/+bug/992241](https://bugs.launchpad.net/mythbuntu/+bug/992241)

I didn't even know there was an upgrade from CD option back in 11.10
I read the info from the link you posted.  

> When using the live cd to upgrade, it wipes /var/lib/mythtv/* (presumably /var/*) meaning you lose the database and the default storage group locations

It sounds EXACTLY what happened on my system - the /var/lib/mythtv partion was wiped - mysql database, and all recorded video files.

I downloaded the 11.10 ISO file (last night) February 03, 2013, 7:54:28 PM Central Standard Time.

:!: So, this time bomb is still out in the download folders. :!:

That 11.10 ISO needs to be DELETED IMMEDIATELY!

Eric

---

### Post by neutron68 on 2013-02-06
I've thought this for the last 4 or 5 years.

If a dangerously buggy ISO (such as 11.10) is released, it needs to be deleted from public download sites after it is discovered.  Then, after the bugs are fixed, a NEW ISO will be created and released.

Case in point:  this 11.10 release has poison in it that will delete important files during an upgrade!   The poison was reported in March of 2012 - about 6 months after the October release.  I'm suggesting that the poison ISOs should have been deleted in March 2012 so no more people would have their their working systems destroyed.

It makes sense to me that a policy like this become a matter of course in the Ubuntu/Mythbuntu community, to prevent needless damage to systems.

Eric

---

### Post by tgm4883 on 2013-02-06
> **neutron68 said:**
> I've thought this for the last 4 or 5 years.

If a dangerously buggy ISO (such as 11.10) is released, it needs to be deleted from public download sites after it is discovered.  Then, after the bugs are fixed, a NEW ISO will be created and released.

Case in point:  this 11.10 release has poison in it that will delete important files during an upgrade!   The poison was reported in March of 2012 - about 6 months after the October release.  I'm suggesting that the poison ISOs should have been deleted in March 2012 so no more people would have their their working systems destroyed.

It makes sense to me that a policy like this become a matter of course in the Ubuntu/Mythbuntu community, to prevent needless damage to systems.

Eric

Actually, the bug was reported April 30th, 2012 by me (after the 12.04 release). It was reported by me because someone either came into the Mythbuntu IRC chatroom or on the Mythbuntu mailing list and had this issue with 12.04 (I don't recall which one). The reason this bug made it to the final 12.04 release? None of the Mythbuntu developers even knew there was an upgrade from CD option (it was something added to Ubiquity by upstream). That bug report is the first we had heard about it, and was believed to be a new feature. After hearing about it the Mythbuntu developers took appropriate action to get it fixed for 12.04.1. Believe it or not, with all of our users, you are the second person to have this issue and report it(and the first on 11.10). 

When the bug was found in 12.04, Mythbuntu developers took action and fixed it in 12.04.1 (and listed it as a known issue). Once 12.04.1 was released, the 12.04 ISO was removed. When the bug was found in 11.10 (2 days ago), Mythbuntu developers had the ISO removed the next day. You lost all your recordings and MySQL database, that sucks. If you need someone to yell at to feel better, go right ahead. But we need people that run into these issues to report them so we can take action. We simply aren't clairvoyant.

---

### Post by neutron68 on 2013-02-07
> **tgm4883 said:**
> Actually, the bug was reported April 30th, 2012 by me (after the 12.04 release). It was reported by me because someone either came into the Mythbuntu IRC chatroom or on the Mythbuntu mailing list and had this issue with 12.04 (I don't recall which one). The reason this bug made it to the final 12.04 release? None of the Mythbuntu developers even knew there was an upgrade from CD option (it was something added to Ubiquity by upstream). That bug report is the first we had heard about it, and was believed to be a new feature. After hearing about it the Mythbuntu developers took appropriate action to get it fixed for 12.04.1. Believe it or not, with all of our users, you are the second person to have this issue and report it(and the first on 11.10). 

When the bug was found in 12.04, Mythbuntu developers took action and fixed it in 12.04.1 (and listed it as a known issue). Once 12.04.1 was released, the 12.04 ISO was removed. When the bug was found in 11.10 (2 days ago), Mythbuntu developers had the ISO removed the next day. You lost all your recordings and MySQL database, that sucks. If you need someone to yell at to feel better, go right ahead. But we need people that run into these issues to report them so we can take action. We simply aren't clairvoyant.

Ah!  It sounds like there already IS a policy of removing and remaking dangerous ISOs.  That is excellent.

Thanks for responding to the report quickly.  I totally understand that the 11.10 ISO could not be fixed, if it wasn't know to be dangerous.  My main goal was to be sure this got reported and that some corrective action got taken to protect other's systems.

Luckily for me, the only recording on my Mythbuntu 11.04 machine that wasn't backed up was the Hurricane Sandy Relief Concert recording.  I'm mainly bummed that the database (and some custom recording searches) got lost.

Again, thanks for the report of corrective action.  This is a good thing for the Ubuntu/Mythbuntu community.

Eric

---

### Post by tgm4883 on 2013-02-07
> **neutron68 said:**
> Ah!  It sounds like there already IS a policy of removing and remaking dangerous ISOs.  That is excellent.

Thanks for responding to the report quickly.  I totally understand that the 11.10 ISO could not be fixed, if it wasn't know to be dangerous.  My main goal was to be sure this got reported and that some corrective action got taken to protect other's systems.

Luckily for me, the only recording on my Mythbuntu 11.04 machine that wasn't backed up was the Hurricane Sandy Relief Concert recording.  I'm mainly bummed that the database (and some custom recording searches) got lost.

Again, thanks for the report of corrective action.  This is a good thing for the Ubuntu/Mythbuntu community.

Eric

A quick note. I only saw this because I happened to look at the forums the other day (I don't usually frequent the forums that often). It would be better to file a bug at [https://bugs.launchpad.net/mythbuntu/+filebug](https://bugs.launchpad.net/mythbuntu/+filebug) which means I'll get an email and it will be announced in the Mythbuntu developer channel.

---

