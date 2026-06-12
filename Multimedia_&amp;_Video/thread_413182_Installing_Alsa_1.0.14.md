---
title: "Installing Alsa 1.0.14"
date: 2007-04-18
forum: Multimedia &amp; Video
---

### Post by artooro on 2007-04-18
**This post could be related to an Ubuntu bug filed at**: [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=a58e7cb16dfae8a3c1c98a7ab7ca02a9e9b38921](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=a58e7cb16dfae8a3c1c98a7ab7ca02a9e9b38921) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello folks,

I need to upgrade my ubuntu installation (fiesty 7.04) alsa package to 1.0.14 for line-in support on my sound card.

Are there any pre-built packages available or is it absolutely required that I build the latest alsa development release from source and try to get the beast all working correctly?

Thanks for your help!

---

### Post by erothoff on 2007-04-19
As far as I know, you have to compile them. I just did that trying to get my sound card working.  (Haven't got it working yet.) But when you compile don't forget to:


sudo apt-get install build-essential

first. I didn't, and kept getting error messages.  I assume Ubuntu is waiting for  1.0.14 to be stable, instead of RC3 before they add it to the repositories.

Good luck!

---

### Post by anirban.sam on 2007-05-05
Type alsamixer and press enter in a console to launch alsamixer. Disable all ICE devices in alsamixer and unmute all muted. Save settings by typing "sudo alsactl store".

---

