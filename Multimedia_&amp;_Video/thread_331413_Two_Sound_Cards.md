---
title: "Two Sound Cards"
date: 2007-01-04
forum: Multimedia &amp; Video
---

### Post by arizcats9987 on 2007-01-04
Hi,
Im currently runniing a creative audigy 2 ZS along with the integrated sound card on my motherboard.  After installing the drivers for the creative card the motherboard card doesnt work.  Ive noticed that I can switch between the two but cant have both on at the same time.  The main reason I want both on is because my computer case (Antec 900) audio is connected to the motherboard.  Any way to have both at one time working?

---

### Post by pseudonym on 2007-01-04
How are you switiching between the two cards at the moment? If you type 'aplay -l' in a terminal you should be able to see the alsa names for each card (eg. hw0,0 and hw1,0) . you can use these names to tell different applications to output sound to different sound cards.

Also, when you say your case is connected to your motherboard, is that the front panel audio? Depending on your motherboard I think you can still use that even if you disabled your onboard sound, because it just gets re-routed via the PCI sound card. Or there may even be a connector on the sound card you can hook up to a header on the motherboard. But you'd have to check.

---

