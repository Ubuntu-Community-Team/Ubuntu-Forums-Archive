---
title: "Dumb driver question: If the OSS driver is installed, will it kill ALSA?"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by samuraiCat on 2007-06-25
Once again, I will annoy you all with my dumb audio questions.

Just to update you, I have a Revolution 5.1 card. I installed Ubuntu after the card was installed, and I immediately went to the M-Audio site for drivers. They referred me to [www.opensound.com](www.opensound.com), where I found instructions regarding installation of the oss-linux_v4.0-1003_i386.deb package, which I did. Then I did an apt-get for all the recommended ALSA packages, plus Hydrogen and JACK. 

For some reason, though, the only programs related to sound that will work are the media player for music and video files. I cannot get Hydrogen to play a loop, I can't record anything, and the ALSA mixer won't even load. 

I tried to fix this by following these instructions: M-audio Revolution and upgrade Alsa ([http://ubuntuforums.org/showthread.php?t=400268](http://ubuntuforums.org/showthread.php?t=400268))

And then with this:

> Getting the ALSA drivers from a *fresh* kernel

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.

A faster way, is to just remove the problematic packages and reinstall them cleanly.

(1) Remove these packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


(2) Reinstall those same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils
[list][*]
VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm ubuntu-desktop


None of that worked. I wonder, though, if I should uninstall that oss-linux driver. I also wonder if I can do a better purge and restore Ubuntu's sound-related packages and settings to their original state.

Does anyone have any suggestions? 

Thanks!

---

### Post by samuraiCat on 2007-06-25
UPDATE: Oh, crap. From [http://www.linuxdevcenter.com/pub/a/linux/2001/05/17/drivers_2-user.html](http://www.linuxdevcenter.com/pub/a/linux/2001/05/17/drivers_2-user.html)
> You can't get the performance you desire from the current driver and want to try another one.

This is potentially the trickiest scenario to manage. Each of the available driver packages maintains a different presence in your system startup and filesystem. If your existing driver is modular you can simply remove it from /lib/modules/linux-version/sound; however, if the driver is hardcoded into the kernel you will to recompile the kernel for modular sound support. You must have a kernel set up for modular sound if you want to use the ALSA drivers (just don't select any specific driver when configuring the kernel). The 4Front package installation routine can be directed to uninstall any kernel sound modules (but not ALSA modules) before installing OSS/Linux; a reboot is not required.

I'm going to have to totally reinstall Ubuntu again, aren't I? Crap.

---

