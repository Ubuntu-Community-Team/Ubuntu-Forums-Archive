---
title: "Help! No sound with Creative SB 5.1 Live"
date: 2008-05-14
forum: Multimedia Software
---

### Post by victorche on 2008-05-14
Please, give me an idea. I have no sound with Creative SB 5.1 Live.

I've tried all the variants and options in alsamixer. No sound at all.

With 7.10 all worked fine. Now I am running an up-to-date 8.04 and there is no sound at all :(

---

### Post by MaindotC on 2008-05-14
The first advice I usually give in these types of situations is to update your BIOS if there is a later version available from the manufacturer.  If not, have you tried installing different sound modules like Pulse Audio or ESD?

---

### Post by victorche on 2008-05-14
> **strAlan said:**
> The first advice I usually give in these types of situations is to update your BIOS if there is a later version available from the manufacturer.  If not, have you tried installing different sound modules like Pulse Audio or ESD?

The short answer is... No, I don't think I will update my BIOS. I don't see the connection here. My sound card is PCI, not integrated in the motherboard. Besides, the same card works fine with Ubuntu 7.10, Slackware 12.1, Windows XP. Why I have to upgrade my BIOS at all?

I also didn't install anything. As I said it is a fresh Hardy install with all current updates. So obviously the problem is IN Hardy ;)

Any other ideas?

---

### Post by MaindotC on 2008-05-14
I advised a few others that had laptop sound issues in Hardy but not in Gutsy to upgrade their BIOS and it provided results for them so that's why I suggested it.  I don't know enough about the BIOS from an electrical standpoint to understand your point about the sound card being PCI so the BIOS should be ignored.

Did you try installing the other sound modules?  Have you tried selecting different devices in System -> Preferences -> Sound?  What happens when you test these?

---

### Post by victorche on 2008-05-15
> **strAlan said:**
> I advised a few others that had laptop sound issues in Hardy but not in Gutsy to upgrade their BIOS and it provided results for them so that's why I suggested it.  I don't know enough about the BIOS from an electrical standpoint to understand your point about the sound card being PCI so the BIOS should be ignored.

Did you try installing the other sound modules?  Have you tried selecting different devices in System -> Preferences -> Sound?  What happens when you test these?

Simply nothing... I did it and tried all the options there. No sound at all. I am able to choose ALSA, PulseAudio... And the result is always the same. No audio at all...

---

### Post by MaindotC on 2008-05-15
You can also right-click the sound icon on your menu bar and select "Open Volume Control". From there you select "Edit -> Preferences" and you can select different audio devices to enable and disable.  I hope I'm not suggesting the obvious :(  Any luck?

---

