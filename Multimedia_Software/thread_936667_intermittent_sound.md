---
title: "intermittent sound?"
date: 2008-10-03
forum: Multimedia Software
---

### Post by heiNey on 2008-10-03
hi all,

im having an odd problem with my sound.  sometimes when i boot up, i get sound, but more often than not, i cant get any sound from my speakers.  the only thing i can do to resolve this is to keep rebooting my computer until the sound finally works.  i had this problem in gutsy, and i just upgraded to hardy thinking it would be fixed, but it is still the same.  any ideas on what i could do?

i have a creative sb live! card...this is the relevant output from: lspci

```

01:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)

```

also, i have onboard sound that is from nVidia:

```

00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)

```

not sure if that will affect it, but any help would be appreciated...thanks!

---

### Post by markbuntu on 2008-10-03
Your cards are probably not being assigned the same positions on every reboot so the default sound card keeps changing. I have recently posted a guide to using multiple sound cards here:

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

Do not believe those people who tell you you must disable one of the cards in the bios, they don't know what they are talking about.

---

### Post by heiNey on 2008-10-04
oh i see...well looks like disabling the onboard sound is the quickest way...so ill just do that since i never use it...but thanks for letting me know what was happening!

---

