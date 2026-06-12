---
title: "Mythbuntu Auto-Updates Questions"
date: 2010-01-10
forum: Mythbuntu
---

### Post by Illydth on 2010-01-10
*UPDATE: I was just answered on the MythTV list that 0.22 updates is "fixes" and 0.23 updates is "Trunk".  I would still like a confirmation of the question below about how stable -Fixes is, but this is the main answer to the question.  Sorry for the "double" post I guess.

I'm going to apologize in advance because this seems to be a very silly question to be asking...unfortunatly I'm a RedHat kind of guy and even though I've been working with Ubuntu/Mythbuntu now for a few years I am STILL a complete noob at package management and sources in Debian Distros.

My most basic question is:

I have a Mythbuntu 9.10 installation (upgraded from 9.04 which was upgraded from 8.04).  Started looking into switching up to the MythTV 0.22-Fixes branch from the MythTV 0.22 Default installation with Mythbuntu.

First, yes, I know about [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds).  I have read the FAQ and I am still completely confused I guess.

I downloaded and installed the .deb and it walked me through the setup.  At one point I told it I wanted updates to 0.22 (not 0.23) and I enabled the PPA (the one that says it does NOT contain Myth Updates).

Now for the confusion.  At no point was I ever asked whether or not I wanted to go to 0.22-Fixes or 0.22-Trunk (at least not specifically). And, of course, this bothers me because I don't want to be trying to deal with WAF problems when a new feature isn't working quite right and I'm using bleeding edge.  I also don't want to have to end up re-installing myth just to get out of that process...if I make the "wrong" choice I get stuck on fixes and can't go back.

I am ASSUMING that by selecting updates to 0.22 and not 0.23 that I have, in fact, selected the "fixes" branch and not Trunk, but really I need clarification before I send this system into bad WAF land.

Along those lines also, another question:  I ASSUME that what goes into -Fixes is actually considered stable?  Or is this just a less active "development" branch?  i.e. Am I going to run an update on 22-Fixes and find that the system gets uninstalled or doesn't work or some such?

Again, I apologize for the silly question here, this is likely VERY self explanatory, I just don't want to end up pushing the system into bleeding edge land and then spend my night on the couch when the wife or kids can't get to their shows.

--Doug

---

### Post by 365nice on 2010-01-13
I am confused about this as well - the instructions about Auto-Builds on the site are just plain wrong.

I too would like just stable fixes - and not trunk fixes.

What do I select in the Control Center to do this?

I have ticked the : Activate Auto-Builds Repo, Selected 0.22 and picked PPA (but being in the UK should I pick UK?).

I then am not sure about Activate Testing-PPA? I have it ticked.

(by the way the control panel doesn't resize properly - on my screen the right of the text is clpped by the category buttons - so it makes it hard to read)

However when I look at the updates I get the warning - Not all Updates can be installed - run a partial upgrade to install as many as possible.

This sounds wrong? (I did do a clonezilla partition backup so I suppose I can go back) - and I haven't applied any changes.

But how should all of this work?

Tim

---

### Post by Illydth on 2010-01-13
For the basics:

Enabling auto builds and then selecting the 0.22 archive (NOT 0.23) provides MythTV-0.22-Fixes NOT Trunk, this was confirmed for me on the MythTV list and upon update I find myself at the 0.22 Fixes branch, it's fine. :)

Being in the UK you should probably pick UK as your option, this only selects the closest mirror, it doesn't affect what you get, just where you get it from.

Activating the Testing PPA is ok, it controls a bunch of packages that are mythtv related but not actually mythtv...stuff like mythexport script, the mythbuntu control panel, etc.  I'm not sure the status on the packages in this PPA (whether they're considered stable or not) but in my experience the "additional" packages like this aren't an issue so I've gone ahead and added it.  

I haven't been in the Control Panel for quite some time so I'm not sure what issues you might be seeing there.

PARTIAL UPDATES ARE BAD!

When I ran mine last Sunday I didn't get a question about a Partial Upgrade, checking again just now, I didn't get any messages about that either.  I'm no debian expert, I'm not sure what to do about the partial upgrade issue.  I've heard something recently about partial upgrades in relation to the new NVidia drivers (190) but I'm not experiencing anything myself.

When you get the partial upgrade message it's possible that you just need to wait another day or two for final packages to be uploaded?  Maybe?  But the fact I'm not getting that myself says otherwise.

Good Luck to you! :)  At least you know you're setup right now.

---

### Post by novellahub on 2010-01-13
> **Illydth said:**
> 
PARTIAL UPDATES ARE BAD!

When I ran mine last Sunday I didn't get a question about a Partial Upgrade, checking again just now, I didn't get any messages about that either.  I'm no debian expert, I'm not sure what to do about the partial upgrade issue.  I've heard something recently about partial upgrades in relation to the new NVidia drivers (190) but I'm not experiencing anything myself.

When you get the partial upgrade message it's possible that you just need to wait another day or two for final packages to be uploaded?  Maybe?  But the fact I'm not getting that myself says otherwise.

See here for a explanation of the partial updates:

[http://ubuntuforums.org/showpost.php?p=8598197&postcount=177](http://ubuntuforums.org/showpost.php?p=8598197&postcount=177)

---

### Post by 365nice on 2010-01-13
Thanks guys - this all finally made sense and I was able to upgrade and finally managed to get VDPAU to work! (Although it was worth running the frontend from a terminal as the error messages are much more revealing in the upgrade - it turned out the video memory buffer in my bios wasn't set high enough).

It still seem the the Show Group Summary option for the manage recordings screen is still broken (e.g. it always shows a group summary even when off - I submitted a trac ticket) - but hopefully I will find some of the other niggles fixed (but VDPAU was really what I was after)

Tim

---

