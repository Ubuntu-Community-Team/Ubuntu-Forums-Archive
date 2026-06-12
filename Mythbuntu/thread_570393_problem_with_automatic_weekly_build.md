---
title: "problem with automatic weekly build"
date: 2007-10-08
forum: Mythbuntu
---

### Post by stevetv on 2007-10-08
edit... i guess this sounds like a question.. which is probably inappropriate for a development product.  i was really just curious as to whether it was a bug in the latest build .. or a stevetv bug (im good at breaking things).

did i have a problem with the automatic weekly build?

i added the apt-key and the repository as directed.  and then sudo apt-get upgrade.  apt installed updates for most of the mythtv modules.

i use standard XvMC with bob x 2 deinterlacing.  this combination has worked well for me for several years.  

however prior to the up i was able to view tv using ffmpeg or indeed the other decoders.  after the upgrade i was ONLY able to use XvMC.  if i use something other than the standard XvMC or VIA XvMC, i cannot watch tv.. it's as if the horizontal or vertial sync is out somehow.. and i just get lines across the screen.

even with XvMC enabled, i get a garbled screen for the first second or so until the XvMC kicks in (ie the time that it would previously take for the USD to go from colour to black and white).

Sorry for my crap knowledge... the weekly builds simply updates mythtv to the latest ubuntu build correct?  

i actually reformatted and did a reinstall.  possibly i shouldve looked at the logs.  i'll do it again to see if i can repeat the problem.. and then post logs.

---

### Post by stevetv on 2007-10-08
just posting my sig.. which contains my hardware specs.

---

### Post by superm1 on 2007-10-08
> **stevetv said:**
> edit... i guess this sounds like a question.. which is probably inappropriate for a development product.  i was really just curious as to whether it was a bug in the latest build .. or a stevetv bug (im good at breaking things).

did i have a problem with the automatic weekly build?

i added the apt-key and the repository as directed.  and then sudo apt-get upgrade.  apt installed updates for most of the mythtv modules.

i use standard XvMC with bob x 2 deinterlacing.  this combination has worked well for me for several years.  

however prior to the up i was able to view tv using ffmpeg or indeed the other decoders.  after the upgrade i was ONLY able to use XvMC.  if i use something other than the standard XvMC or VIA XvMC, i cannot watch tv.. it's as if the horizontal or vertial sync is out somehow.. and i just get lines across the screen.

even with XvMC enabled, i get a garbled screen for the first second or so until the XvMC kicks in (ie the time that it would previously take for the USD to go from colour to black and white).

Sorry for my crap knowledge... the weekly builds simply updates mythtv to the latest ubuntu build correct?  

i actually reformatted and did a reinstall.  possibly i shouldve looked at the logs.  i'll do it again to see if i can repeat the problem.. and then post logs.
From what version did you upgrade?  And which weekly build did you choose?  Both trunk and 0.20-fixes are available as weekly builds.  

There shouldn't be any significant mythtv changes (mostly packaging changes) between the 0.20.2 in feisty-updates and the one on weekly-fixes.

---

### Post by stevetv on 2007-10-12
yeah sorry for my poor explanation of my problem.

i have installed Mythbuntu 7.10 Public Beta, and then added the apt-key and repos for the 0.20.2 fixes builds.  im not really a developer so stable upgrade suits me.

i just did this

```

Enabling The Repository (0.20.2 Fixes Builds)

Follow these directions to add/enable the repository if you are intending to use the release-0-20-fixes branch

    wget http://mythbuntu.org/files/EEED06D0.gpg && sudo apt-key add EEED06D0.gpg && rm EEED06D0.gpg


    echo "deb http://uk.weeklybuilds.mythbuntu.org/mythbuntu/ubuntu feisty multiverse universe restricted main" | sudo tee /etc/apt/sources.list.d/mythbuntu-feisty.list


    sudo apt-get update
    sudo apt-get upgrade


```

after this upgrade, i was only able to use XvMC to view tv.  without XvMC enables, my screen was just garbled picture.  sound was fine.

ive since reinstalled, and everything is fine.  but i havent retried the weekly update.

The final release will include a backup and restore... ill wait till then before i change too many things.  ive got a working box.. so im happy.

---

### Post by stevetv on 2007-10-12
sorry.. it was my fault and nothing to do with the weekly build.

i had selected openGL vertical sync for timing in the general playback settings menu.  with this selected, i can only get vertical sync when im using XvMC.

to me this is slightly unusual behavior?  .. i don't remember this been a problem with knoppmyth... but possibly it always was..

---

### Post by superm1 on 2007-10-12
Well this likely isn't the cause of your direct problem, but do note that those weekly builds are only for feisty.  New gutsy builds will not be introduced until gutsy is released.

---

### Post by stevetv on 2007-10-12
right... i didn't know that.  ive not used ubuntu before so naming convention didnt mean much to me.  i'm up with it now though.. probably something i shouldve read before i started upgrading.

in my most recent fresh install, ive only upgraded using the repos included by your install .. of which there are many.  so i presume thats the correct way.

thanks for the reply.

---

