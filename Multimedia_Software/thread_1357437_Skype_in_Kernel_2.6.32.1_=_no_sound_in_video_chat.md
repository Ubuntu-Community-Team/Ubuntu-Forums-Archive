---
title: "Skype in Kernel 2.6.32.1 = no sound in video chat"
date: 2009-12-17
forum: Multimedia Software
---

### Post by infernus_crusher on 2009-12-17
Well, actually I can hear the other person talking to me, but they can't hear me. I've tried setting everything in my volume setting to max but it doesn't work.

But if I revert to the older kernel 2.6.28.17, it magically works.

Also, both kernels seem to provide *different* volume controls. The one in the older kernel allows me to control "In-gain" which I found to be the one that adjusts my webcam to transmit sound to the other person. Is it possible to enable adjustment to this in the newer kernel?

---

### Post by saltmore on 2009-12-17
Using the one out of the mediabuntu repo or the one from skype homepage? Try the newest one from other source.

---

### Post by infernus_crusher on 2009-12-17
Yes, I'm using Skype for Ubuntu 8.10+ 32-bit from the Skype homepage.

---

### Post by infernus_crusher on 2009-12-18
bump

---

### Post by saltmore on 2009-12-18
You can uninstall the version you have, and then install the one from the mediabuntu repo. Have you made sure your mic is working? Is it muted? You may also want to uncheck let skype manage sound or whatever it is called. I would first try the newest version from mediabuntu.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Once you have removed the current version of skype. Then install the mediabuntu one from synaptics package manager.

---

### Post by fromgi on 2009-12-18
> **saltmore said:**
> 

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Once you have removed the current version of skype. Then install the mediabuntu one from synaptics package manager.

Don't see anything Skype on Medibuntu or Synaptic.  An I looking in the wrong place?

---

### Post by infernus_crusher on 2009-12-18
> **saltmore said:**
> You can uninstall the version you have, and then install the one from the mediabuntu repo. Have you made sure your mic is working? Is it muted? You may also want to uncheck let skype manage sound or whatever it is called. I would first try the newest version from mediabuntu.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Once you have removed the current version of skype. Then install the mediabuntu one from synaptics package manager.

I've done all that you said but I'm not able to unmute the microphone under kernel 2.6.32.1. It always mutes itself again.

And I think you're mistaken. Mediabuntu repository does not have Skype.

---

### Post by saltmore on 2009-12-18
[http://www.ubuntumini.com/2009/07/medibuntu-for-ubuntu-910-karmic-koala.html](http://www.ubuntumini.com/2009/07/medibuntu-for-ubuntu-910-karmic-koala.html)

---

### Post by Michael Matthews on 2010-01-08
Installed mediabuntu reps, can install dvd, codecs but no skype

$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package skype is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package skype has no installation candidate

---

