---
title: "Alsa and SPDIF on Gibabyte mb"
date: 2010-04-29
forum: Multimedia Software
---

### Post by Kleenux on 2010-04-29
Hi,


I own a motherboard P55-ud3r from Gigabyte.
And installed the SPDIF-IN connector (to record digital input).

(this is my [sound profile]("http://www.alsa-project.org/db/?f=ccf5a27b1089c7b12b58da06695417d2181694ad"))

The SPDIF-IN (nor OUT) is not seen by Ubuntu (alsamixer shows IEC958 as off but it can be enabled - if that matters)


What is the way to get the drivers to see SPDIF IN?

Thank you.

---

### Post by lidex on 2010-04-29
Have you tried using alsamixer? Terminal="Applications->Accessories->Terminal"
```
alsamixer
```

Press F5 for all elements (or <tab> over). Scroll right with arrow keys. Look for spdif, or 'input source', probably better. Toggle the source input options with up/down keys. Also have a look at gnome-alsamixer and make sure all options are enabled in 'Edit>Soundcard Properties'. Check all the options/levels etc. If not installed:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by Kleenux on 2010-04-30
> **lidex said:**
> Have you tried using alsamixer? 
Dear lidex, thank you for your answer.

I know alsamixer for a long time, and - as I said in the 1st post - used it to enable iec958.

But it seems the input cannot be seen - this is a direct laser input S/PDIF.

Any other comment will be welcome

---

