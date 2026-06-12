---
title: "alsa-tools-gui and echomixer?"
date: 2007-06-23
forum: Multimedia &amp; Video
---

### Post by voxman69 on 2007-06-23
Hi!

Installed Ubuntu Studio on my 2nd PC to give it a go and maybe get rid of XP on that one too! :-)
Installation went fine and everything seems to be where it's supposed to be.

However...I have, aside from the built-in soundcard (some Intel chip I think), an Echoaudio Gina 20 card. As far as I can see there's something called the "echomixer" inside the "alsa-tools-gui". Great! But how the f... do I start it?

I've tried in the terminal (as sudo too) but all I get is "command not found" or when going directly for "echomixer" I get "No Echoaudio cards found, sorry." That last one sounds correct since I can't see the Gina-card in any of the applications...

So, I guess my real question is how to get UbuntuStudio to recognise that there really is an Echoaudio card present?

I'm sure you'd like to see a printout of some cool Terminal-command so please tell me which one and I'll deliver! ;-)


EDIT: I should perhaps tell you that the Echoaudio-card works perfectly in XP.

---

### Post by voxman69 on 2007-06-23
Ok...I've now been surfing the ENTIRE internet (really!) and from what I understand there's supposed to be support for the Gina20 built into the kernel...I'm far from sure though. Be that as it may, I still get the "No Echoaudio cards found, sorry." error...

I also found this: [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=dd7b254d8dd3a9528f423ac3bf875e6f0c8da561](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=dd7b254d8dd3a9528f423ac3bf875e6f0c8da561)

In that list are several Gina20 related source code files, but I really wouldn't know where to start with them. Any pointers?

---

### Post by voxman69 on 2007-06-26
Hmmm...still on it. :-)

I've tried everything by now but no go...Studio just refuses to deal with my beloved Gina20....I can see it if I do a "lspci" but that's about it. However, and this feels strange, i've tried a few live-cd's;

**Dynebolic** can't handle the card either, but at least it says it's there (I can run the alsaconig but it crashes at the very end).

**Studio to Go! **by Fervent works!!! Incredible but true...it found and activated my Gina. Only downside is that it's commercial (80£). It's still cheaper than buying a new card but somehow it feels very expensive considering everything i use in it is FOSS...

Being a Linux newbie I can't really figure out what differs in **Studio to Go!** and **Ubuntu Studio** except that Studio to Go! has it's own Kernel...
Is there really no-one out there with a working Echoaudio card in Ubuntu Studio?

---

