---
title: "Low mic volume"
date: 2009-11-07
forum: Multimedia Software
---

### Post by catch22 on 2009-11-07
Hi

When i first installed 9.10 on my mums acer aspire one all was fine, but now the mic volume on skype is really low, there is no longer an option to change the connector for input in the sound options (there is no connector option at all), tried alsamixer from the terminal and everything is at 100%, only one input source i-mic low sound tried changing to e-mic but got nothing but white noise.
Downloaded skype from mediubuntu and package from site but only have option to use pulse for mic.

Any help please mums is in OZ and missing talking to the grand children

Cheers

---

### Post by catch22 on 2009-11-08
anyone ???

---

### Post by Piscium on 2009-11-08
I had a similar problem (or so it seems).

You can download with Synaptic the package gnome-alsamixer. After installation you will find it in Applications/Sound and Video. Call it and tick the box that says Mic Boost (+20 dB). 

That solved the problem for me.

With Jaunty this application was somehow installed automatically, but not with Karmic.

---

### Post by xc3RnbFO8P on 2009-11-08
> When i first installed 9.10 on my mums acer aspire one all was fine, but now the mic volume on skype is really low
Do you dual boot (XP)?

---

### Post by catch22 on 2009-11-09
> **Ringi said:**
> Do you dual boot (XP)?

No clean install, it was fine for a day, included an attachment of the sound prefs and the missing connector option

---

### Post by catch22 on 2009-11-09
> **Piscium said:**
> I had a similar problem (or so it seems).

You can download with Synaptic the package gnome-alsamixer. After installation you will find it in Applications/Sound and Video. Call it and tick the box that says Mic Boost (+20 dB). 

That solved the problem for me.

With Jaunty this application was somehow installed automatically, but not with Karmic.

Cheers mate that worked kind of had to change the input balance all the way to the right

---

### Post by batarce on 2009-12-27
Sorry but I couldn't find that box

---

