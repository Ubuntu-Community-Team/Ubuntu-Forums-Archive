---
title: "line-in as surround option is missing in alsamixer"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by SuperJETT on 2007-04-21
Argh.  Ok, now here's the info.

I have sound working fine on Edgy, but am setting up a home theater with mythtv on my Shuttle sk41g which has Realtek AL650 audio with 5.1.

I do not have the 'line-in as surround' option in alsamixer (gnome alsa mixer is what I'm using), and it shows as an AL650E which may mean the driver is not configured properly?

I found
[http://alsa.opensrc.org/AlsaTips#Enabling_5.2B1_outputs_on_cards_with_line-out.2C_mic-in_and_line-in_jacks](http://alsa.opensrc.org/AlsaTips#Enabling_5.2B1_outputs_on_cards_with_line-out.2C_mic-in_and_line-in_jacks)
but am not sure if he's talking about writing a script to do that, or what.

Currently, my left/right work fine, the rear outputs using  $ speaker-test -Dsurround51 -c6 -l1  come out on the center/sub output.

Can someone point me in the right direction or explain how to do the setup in the above link?

---

### Post by sgx on 2007-04-21
alsamixergui is a separate app, install it, and stretch the window to the the far right, and use the dragbar at the bottom if needed...if your linux can find these surround ports, they will be in this gui... 
envy24control  is a specific panel for maudio/terratec/other ice1712 soundcards...

also install alsaoss, it fixes some niggly little problems that can seem baffling to someone who
just wants working A/V

hope this helps...

---

### Post by SuperJETT on 2007-04-21
> **sgx said:**
> alsamixergui is a separate app, install it, and stretch the window to the the far right, and use the dragbar at the bottom if needed...if your linux can find these surround ports, they will be in this gui... 
envy24control  is a specific panel for maudio/terratec/other ice1712 soundcards...

also install alsaoss, it fixes some niggly little problems that can seem baffling to someone who
just wants working A/V

hope this helps...

I'll do that tonight, thanks for the pointers.

---

### Post by SuperJETT on 2007-04-22
Well, after trying many more things, it all comes down to the fact that I just don't have the 'line-in as surround' option *anywhere*.

I think next I need to try to remove/reinstall the drivers for the audio completely.  It's a ALC650E on Via 8235 chip.

Currently the fronts/center/sub work, but no surrounds.

---

