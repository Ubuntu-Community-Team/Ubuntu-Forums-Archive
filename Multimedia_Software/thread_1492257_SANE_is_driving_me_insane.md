---
title: "SANE is driving me insane"
date: 2010-05-24
forum: Multimedia Software
---

### Post by alaskanime on 2010-05-24
I'm somewhat of a novice user, but I can follow instructions.

I've been trying to get my HP ScanJet 5500c to work on Jaunty Jackolope and not having any luck.  I installed new SANE backends (version 1.0.21) and managed to get them copied to the correct directory.  It worked like a champ for a few hours - then I made the mistake of powering off my computer for the night.  I installed and ran SANE troubleshoot (which apparently hasn't been updated in over 2 years) and came across this error message:

ERROR: I tried to open the test backend but it returned the following error message: "Invalid argument". Check your SANE installation. Maybe sane-backends wasn't installed completely?

After getting the scanner to work initially last night, I rebooted the machine and it worked properly, but this morning when I turned on my computer, it's like it "forgot" everything I did the night before.  Help!  What is different between a full shut-down and a reboot that it would not work any more?  The only thing I can think of is the updates I did this morning - both of them were "lib" files and one was for Kerberos (I can't for the life of me remember what the other one was - is there a log I can look at that would tell me?)

---

### Post by alaskanime on 2010-05-24
Bumping for great justice.  I'm a little frantic about this because I'm working for a client with about a million (slight exaggeration) photos that need to be scanned by the 1st of June.  Any insight is appreciated!

---

### Post by SoFl W on 2010-05-24
See if you can find help here:
[https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/428476](https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/428476)

Seems the latest libsane version causes problems.  I had a similar problem, was able to fix it but it only worked once.  After that I had a lot going on in my life I didn't worry about it and now I don't have my Scannjet 3500 anymore.  (or any scanner)

---

### Post by alaskanime on 2010-05-24
> **SoFl W said:**
> See if you can find help here:
[https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/428476](https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/428476)

Seems the latest libsane version causes problems.  I had a similar problem, was able to fix it but it only worked once.  After that I had a lot going on in my life I didn't worry about it and now I don't have my Scannjet 3500 anymore.  (or any scanner)

I can't seem to get rid of the last vestiges of the newer backends...sane-troubleshoot is still coming up as detecting version 1.0.21.  Where are the little buggers hiding? :P

---

### Post by alaskanime on 2010-05-24
> **SoFl W said:**
> See if you can find help here:
[https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/428476](https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/428476)

Seems the latest libsane version causes problems.  I had a similar problem, was able to fix it but it only worked once.  After that I had a lot going on in my life I didn't worry about it and now I don't have my Scannjet 3500 anymore.  (or any scanner)

I was finally able to nuke the bad backends from orbit.  Xsane is still not detecting my scanner, and sane-troubleshoot of course doesn't have the HP 5500c on it's list - choosing a generic USB scanner has proven fruitless as well. :confused:

---

### Post by WinterRain on 2010-05-25
If you were using ubuntu 10.04, you could try using **Simple Scan** which comes by default in lucid. Maybe you could try out the live cd of 10.04 and see if it works. Btw, simple scan is an awesome scanning app. Doesn't get any easier.

---

