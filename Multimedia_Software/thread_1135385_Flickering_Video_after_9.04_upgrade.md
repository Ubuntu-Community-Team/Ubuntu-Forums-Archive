---
title: "Flickering Video after 9.04 upgrade"
date: 2009-04-24
forum: Multimedia Software
---

### Post by welsh_sponger on 2009-04-24
Hi, 

After upgrading to Ubuntu 9.04 when streaming video from the web the picture is flicking and missing frames, and is therefore out of sync.

I didn't have this problem before the upgrade...

Any ideas on a solution to this?

Regards.

---

### Post by mharry on 2009-04-26
I'm seeing the exact smae behavior after upgrading to 9.04.  Any information about my system I can share to help debug this?

---

### Post by SphereX253 on 2009-04-27
I also am having this issue. I have the correct video drivers installed. When I stream the video in windows it runs flawlessly, however streaming the same video in jaunty gets my flickering video and low fps. There has got to be a way to fix this.

---

### Post by SphereX253 on 2009-04-28
Bumpity Bump!

UPDATE: I am running the 64 bit edition. I have read several posts that confirm the 64 bit streaming in jaunty blows. Is there really not a workaround for this? I find that hard to believe.

---

### Post by welsh_sponger on 2009-04-30
I have not found a solution...

I'm running the 32 bit version.

Anyone else experiencing this issue?

---

### Post by welsh_sponger on 2009-05-01
I found this earlier, and will try this fix later on today...

"I found out that flash didn't handle the upgrade well to ubuntu 9.04. I fixed it by going into Synaptic package manager, searching for flash then uninstalling all the installed instances of flash software. At this point I rebooted then installed flash 10 for jaunty from the same synaptic flash search I did previously and everything was fixed. Good luck!"

---

### Post by ChiVampir on 2009-05-01
I have the same problem and I'm running Ubuntu 9.04, 32bit.

---

### Post by pro003 on 2009-05-01
Did any of you tried to reinstall the driver?

---

### Post by ChiVampir on 2009-05-01
> **pro003 said:**
> Did any of you tried to reinstall the driver?

I did, but I still got the same problem.

And I know that it's just flash since I have played games and seen DVD's without the same flickering.

---

### Post by pro003 on 2009-05-01
> **ChiVampir said:**
> I did, but I still got the same problem.

And I know that it's just flash since I have played games and seen DVD's without the same flickering.

Try to remove your driver and do the upgrade again:

```
# sudo apt-get update
# sudo apt-get full-upgrade
```

and then check for the latest driver for your card and install it.

See if that helps.

I guess that your old driver was not compiled with the new kernel properly and that is why you have experiencing graphic problems..

---

### Post by ChiVampir on 2009-05-01
> **pro003 said:**
> ....and then check for the latest driver for your card....
How can it be the card when I just have problems with flash and **not** anything else?

---

### Post by pro003 on 2009-05-01
> **ChiVampir said:**
> How can it be the card when I just have problems with flash and **not** anything else?

then do this:

# sudo apt-get update
# sudo apt-get remove ubuntu-restricted-extras --purge
 
reboot

# sudo apt-get update
# sudo apt-get install ubuntu-restricted-extras

see if that helps...

---

### Post by ChiVampir on 2009-05-01
Thank you, but this didn't work either... 
I have heard that this: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) Guide may help, but since I'm not comfortable with using the Terminal yet (I'm new to Ubuntu) I haven't tried jet.

---

### Post by fletchoid on 2009-05-01
Had similar problem when I first installed upgrade.  Not exactly sure how I fixed it because while trying to fix it, I broke the whole graphics system.
See bug: [https://bugs.launchpad.net/ubuntu/+bug/366529](https://bugs.launchpad.net/ubuntu/+bug/366529)
On my system, it was related to the ATI proprietary drivers and Xorg.  I had to:
1. uninstall the proprietary drivers. (see bug report)
2. Reinstall linux-image-generic 2.6.28.11.15
3. reboot into recovery mode (2.6.28.11)
4. use recovery mode menu choice to fix broken packages
5. use recovery mode menu choice to try to fix X server
6. use recovery mode menu choice to boot normally
7. install proprietary ATI drivers again.
8. Right clik desktop to change Visual Effects and select Extra.
This may not be everything that I did.  I also went into Synaptic and chose to install or reinstall numerous graphics related packages.  But, I must have hit the right combo.  Now, I have full 3D Compiz effects, non flickering video, and during bootup, a clean bootscreen (it was all buggered up for a while, and in the wrong resolution).  The only other problem I had with flicker was when I installed Google Earth.  After fiddling for a while, I gave up trying to fix the Google Earth flicker, and installed the Compiz Fusion Icon, so I could just switch to the Metacity window manager when I used Google Earth.

---

### Post by ChiVampir on 2009-05-01
I have finally run this guide [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) And now flash seems to work as it always have :)

Thank your for all your help :)

---

### Post by pro003 on 2009-05-01
glad you made it, anyway...

good luck

---

