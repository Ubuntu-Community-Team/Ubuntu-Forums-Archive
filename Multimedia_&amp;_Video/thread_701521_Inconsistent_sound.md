---
title: "Inconsistent sound"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by StubbDan on 2008-02-19
I recently got a new HD and installed Gutsy on it (this is my first experience with Linux).  I think I have now got almost everything working as it should be, except for my sound.  I have on-board sound and a PCI sound card.  I've been trying to get my sound to be played exclusively through one or the other.  In windows I could just go to sound options and select which one to use for output, but when I do the same in Ubuntu, it occasionally works correctly, but sometimes not.  I'm not sure what the card is, but I believe it's a fairly old creative one.

Sound always works for things like RhythmBox and Pidgin, but about half of the time there is no system noise such as the login sound, and when this happens, flash also makes no sound.  This also affects DVD playback in Totem.

I have the following sound drivers blacklisted (I can't really remember what I was trying to achieve when I did this though...):

> blacklist snd-ak4531-codec
blacklist snd-ac97-codec
blacklist ac97_codec
blacklist ac97_bus
blacklist snd-via82xx
blacklist snd-via82xx-modem
blacklist via82cxxx_audio

I've tried removing these from the blacklist but if anything it only makes it worse. At first I thought that it was working quite happily with these settings, but when I restart, half of the time the sound works incompletely.  Anyone know how to fix this? Thx.

---

### Post by kyphi on 2008-02-19
If you have both onboard sound chip as well as a sound card installed the first instructions your computer receives when you switch it on is from your BIOS setup (onboard sound) and the next instruction is from your operating system (sound card).

You need to go into the BIOS setup and disable the onboard sound.  Your motherboard manual will tell you how to do that.

---

### Post by chipants on 2008-02-19
well, i certainly wouldn't 'blacklist' any sound drivers. unless you *absolutely* need both soundcards to work simultaneously, i would highly recommend disabling the onboard sound via your computer's bios.

i, too, have had trouble with multiple soundcards. when disabling onboard sound, my pci soundcard worked flawlessly.

---

### Post by StubbDan on 2008-02-19
Well the problem is I'm dual booting windows and I use the sound card and on-board for recording from when I load to XP, but I guess I'll just have to change the bios each time.  I'll try it once I've found the manual - thanks.

---

### Post by kyphi on 2008-02-21
You only need one sound device regardless of dual booting.

I dual boot, Ubuntu and XP (not for much longer).  My onboard sound chip is disabled and my Soundblaster Live handles all sound very competently.

A separate sound card gives better sound than an onboard chip.

---

### Post by arimaniac on 2008-03-03
Hi there

I would recommend disabling the on board sound card to prevent conflicts...

Complete HOWTO:

[http://ubuntuforums.org/showthread.php?t=712908]("http://ubuntuforums.org/showthread.php?t=712908")

Please reply with your
comments to improve the HOW TO...

Hope it helps....

---

