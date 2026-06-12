---
title: "TVTime updates (holding)"
date: 2012-02-14
forum: Multimedia Software
---

### Post by JerryReed on 2012-02-14
I finally have TVTime working on my AMD64 machine (although there is still an issue with sound. There is no sound option showing in Pulse Volume Control). However, I have an analog workaround using the aux input on my soundcard.  
The real issue now is staying with the installed version and not updating. Is there a way to force Ubuntu to keep the installed version instead of suggesting a newer version in the update manager? Right now I have to manually uncheck the box every time I run an update. Otherwise, the new version gets installed and TVTime stops working. I currently have 1.0.2-6.1ubuntu1+ppa1 installed. The update manager always wants to install 1.0.2-7ubuntu1.  I need to force the system to stay with the currently installed version.  Anyone have any idea how to do this?

---

### Post by Derek Karpinski on 2012-02-14
Find 'synaptic' in the software center and install it.
 
After you install synaptic, search for tvtime, and you can lock the version that you have installed.
 
[https://help.ubuntu.com/community/PinningHowto#Apt/Dpkg](https://help.ubuntu.com/community/PinningHowto#Apt/Dpkg)

---

### Post by JerryReed on 2012-02-14
Thanks... got it. I appreciate the tip.  TVTime is now locked down.

---

