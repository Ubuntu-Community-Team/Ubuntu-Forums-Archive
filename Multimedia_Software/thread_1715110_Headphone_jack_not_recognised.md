---
title: "Headphone jack not recognised"
date: 2011-03-26
forum: Multimedia Software
---

### Post by Englischdude on 2011-03-26
Hello,

have had some problems with my ASUS Laptop running Linux Mint 10 Julia. I know this is an ubuntu forum, I use ubuntu on my desktop, however I feel this forum to offer the highest chances of solving my problem.

THe initial problem was that the headphone socket was not being recognised when plugging in the headphones. I could get the headphones to work but could not get the loudspeaker to deactivate. I tried installing the Alsa script found in the signature of Lidex which solved the problem, however after this a new problem was introduced, namely the microphone was no longer recognised.

After alot of trying various methods to fix the problem I unded up reinstalling alsa using this link:

sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

which solved the mic problem, but now I have gone round in a complete circle back to the headphone jack problem.  My ALSA information can be found here:

 [http://www.alsa-project.org/db/?f=f2b2eac5aa75de0023af89a45ed0d4f298087bc3](http://www.alsa-project.org/db/?f=f2b2eac5aa75de0023af89a45ed0d4f298087bc3)

Any help would be greatly appreciated.

Please bear in mind that I am in no sense of the word a Linux WIZZ, so please give detailed directions for any solutions offered.

With many thanks in advance.
Martin

---

### Post by Perfect Storm on 2011-03-26
Hi Englischdude

There's a Linux Mint forum to get help with your distro.
You'll find it here: [http://forums.linuxmint.com/](http://forums.linuxmint.com/)


regards
A.I. Dude
Ubuntu Forum Staff

---

