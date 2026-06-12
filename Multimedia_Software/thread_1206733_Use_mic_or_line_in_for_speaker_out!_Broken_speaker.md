---
title: "Use mic or line in for speaker out! Broken speaker out!!"
date: 2009-07-07
forum: Multimedia Software
---

### Post by atomhearth on 2009-07-07
Sorry for the broken english. I' ve broke my audio speaker jack. Is there a way to use line in or microphone in in it's place? Something like Realtek for XP, y' know? It is very importent for me!

Thank you all!

---

### Post by rgrodevant on 2009-07-21
I want to say that every Nvidia, Realtek, and C-Media chipset I've seen, that supports the feature you're asking about, required the vendor's Win32 driver/application. 

(That said..... Anecdotal answers are NOT always better than NO answer..)

Anyway, I can't answer that without knowing your actual chipset#... what module you're loading -- is it a stock kernel module, an ALSA module? 

There's a small chance there's an active community, FAQ, or documentation on whatever module you're using. If not, you get to look at the module source and see what options and goodies were actually written into the module. Whee!

If it's not .............

Some laptop vendors (notably Panasonic) WILL sell you the DC jacks and audio/line jacks seperately for $2-$8 (USD) if you know how to solder. Other brands sometimes have a small, easily replacable "daughter card" for the jacks.

.... Here's how I usually deal with busted DC/Audio jacks: Buy a tiny 1/8" (cabinet mount) jack from Radio Shack or Digikey. Drill a hole in the desktop case or somewhere on the side of the laptop... and then solder three tiny jumper wires from the three leads (ground) (L tip) (R tip) on the new jack, to the corresponding three leads (ground) (L tip) (R tip) from your busted jack. :-P

---

