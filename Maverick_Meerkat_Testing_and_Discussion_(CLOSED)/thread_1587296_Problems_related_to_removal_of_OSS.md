---
title: "Problems related to removal of OSS?"
date: 2010-10-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by bowens44 on 2010-10-03
First the volume control Tvtime no longer works. It's looking for /dev/mixer which no longer exits.

Second problem is that I can no longer get my microphone to work in wine apps.

I have seen various posts when googling indicating that other apps have also been broken by this.

Does anyone know of any work a rounds?

The wine issue is a major problem for me and a deal breaker. It worked perfectly in 10.04

---

### Post by seeker5528 on 2010-10-04
> **bowens44 said:**
> First the volume control Tvtime no longer works. It's looking for /dev/mixer which no longer exits.

Does your TV card uses a cable to get the audio from the TV card to your audio hardware?

If so just install gnome-alsamixer, gamix or some other mixer application that uses alsa directly, figure out which channel the TV card is connected to (line in or mic usually if the cable is external, CD or AUX if it is internal) and unmute/adjust the volume there.

For Wine go on the menu to 'Applications --> Wine --> Configure Wine' or hit 'Alt'+'F2' and type 'winecfg' without the quotes, In winecfg go to the 'Audio' tab to select and configure the alsa stuff.

Later, Seeker

---

### Post by lidex on 2010-10-05
> **bowens44 said:**
> First the volume control Tvtime no longer works. It's looking for /dev/mixer which no longer exits.

Second problem is that I can no longer get my microphone to work in wine apps.

I have seen various posts when googling indicating that other apps have also been broken by this.

Does anyone know of any work a rounds?

The wine issue is a major problem for me and a deal breaker. It worked perfectly in 10.04

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

