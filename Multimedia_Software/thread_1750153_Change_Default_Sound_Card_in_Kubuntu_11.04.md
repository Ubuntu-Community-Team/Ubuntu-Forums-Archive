---
title: "Change Default Sound Card in Kubuntu 11.04"
date: 2011-05-05
forum: Multimedia Software
---

### Post by thefluffy on 2011-05-05
Hey guys/gals,

I am having difficulty changing my default sound card in Kubuntu 11.04. I am able to use Phonon to change it for KDE applications; however, I am unable to accomplish this for VLC and Chromium. 

Can anyone point me in the right direction?

Thanks,

Daniel

---

### Post by Yellow Pasque on 2011-05-05
Can you run alsa-info script so we can see your audio setup?  [http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973](http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973)

It sounds like you need to change ALSA indexes using /etc/modprobe.d/alsa-base.conf

EDIT: This is a good guide: [http://alsa.opensrc.org/MultipleCards#How_to_choose_a_particular_order_for_multiple_installed_cards](http://alsa.opensrc.org/MultipleCards#How_to_choose_a_particular_order_for_multiple_installed_cards)
Post your info if you need more help.

---

### Post by thefluffy on 2011-05-06
That alsa-info script mostly just threw a bunch of errors. The problem isn't that I want to permanently use a different sound card. I really want to be able to change between two sound cards on the fly when I want. I have a USB interface that I use occasionally as well as an internal Sound Blaster Audigy 2. Both sound cards work fine with KDE apps when selected in Phonon. I just want way to easily swap between them like in Phonon. I just want it to affect non-KDE apps like VLC and Chromium.

Thanks,

Daniel

---

