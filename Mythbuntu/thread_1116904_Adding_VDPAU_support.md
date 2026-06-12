---
title: "Adding VDPAU support?"
date: 2009-04-05
forum: Mythbuntu
---

### Post by daveisfera on 2009-04-05
Since 0.22 still doesn't have a release date, would it be possible to add VDPAU support to Mythbuntu? I know that there are [existing patch sets](http://avenard.com/media/MythTV_%26_VDPAU/MythTV_%26_VDPAU.html) that will do it, so would that be possible?

---

### Post by tgm4883 on 2009-04-05
VDPAU is not going to be added to the official .21 packages for Ubuntu.  You can add this yourself if you like to the latest packages.

We think 0.22 will be available in 9.10, but that is just speculation right now.

---

### Post by itlarson on 2009-04-05
This post covers this topic in depth:

[http://ubuntuforums.org/showthread.php?t=1063102]("http://ubuntuforums.org/showthread.php?t=1063102")

jump to post #29 for the short version.  Note: I never worked up the nerve to try this.

---

### Post by azmyth on 2009-04-05
You'll either want to compile with the patches or enable avernard's repo and do as the other posters stated. Just make sure you make a backup up of your db before you upgrade to the vdpau enabled myth. You may see some video tearing but it's an easy fix. Anytime I upgrade the nvidia drivers I do a sudo shutdown -h now since if you do restart in MB it takes you to the login screen first and with the new drivers you'll get caught in a loop and have to hit the power button.

---

### Post by AboveTheLogic on 2009-04-05
I have kde-core installed with mythbuntu 8.10 that I access remotely through FreeNX. Using that, I opened the package manager and installed nvidia-glx-180, then rebooted (sudo reboot). MythTV came up just fine on the TV and the ndivida utility showed that I was running 180.xx. I then added avenard's repo, and was eventually given the option to update my myth front end. After I did that update, I had the vpdau version.

---

