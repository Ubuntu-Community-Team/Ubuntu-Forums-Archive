---
title: "SPDIF sound (two sound cards)"
date: 2008-12-02
forum: Multimedia Software
---

### Post by tjfriese on 2008-12-02
Hello,

I have a somewhat interesting situation. I have an Auzentech card hooked up to my home theatre over a digital (TOSlink/SPDIF) connection. I also have an ATI video card that has an on board sound card.

Both of these seem to show up as possible sound cards when I edit the sound preferences. However, I have multiple C-Media options (I assume that this is the Auzen card).

No matter what I choose, I cannot get any sound.

Can anyone help get me started?

Thanks,

Tim

---

### Post by tjfriese on 2008-12-02
No one has any idea? I want to disable the ATI card so that Ubuntu only sees the Auzentech. Then I need to get the digital out working.

Any thoughts, anyone?

---

### Post by element_G on 2008-12-03
I don't have this card so I can't say what will or wont work but here are some ideas:

you might need to upgrade ALSA (sound drivers) with your sound card enabled
this looks like a good place to start: [http://ubuntuforums.org/showthread.php?t=962695&highlight=build+alsa](http://ubuntuforums.org/showthread.php?t=962695&highlight=build+alsa)

also, pulse audio is good at handling multiple cards. (although it needs a quick workaround for multiple devices to show up for each card (ie the SPDIF))

---

