---
title: "Switching between soundcards"
date: 2006-07-15
forum: Multimedia &amp; Video
---

### Post by Terracotta on 2006-07-15
Hye I have a laptop with a crappy onboard soundcard (and a broken jack-gate), so I use the docking station which has a pci-porte, to install an SB LIVE!! soundcard, Kubuntu (and Ubuntu and Xubuntu, they all have the same problem) recognises them all but sometimes the sb live card is the default one, and when I shut down my laptop and restart it the onboard sound card is the default one. How can I manually tell Kubuntu to take the SB Live card as the soundcard and not the onboard one (oh PS, I tried to disable the onboard soundcard in the bios and well, it's a crappy  old bios which doesn't have many options), and I can't find a new version for it (Compaq Evo N600c Laptop).

---

### Post by jpkotta on 2006-07-15
First find out what cards are using which modules:
```
cat /proc/asound/modules
```

Then, in /etc/modprobe.d/alsa-base, add:
```
option <module> index=<num>
```
for each modules you got from the cat.  Give the one you want first an index of 0, the next one an index of 1, etc.  Example:
```
option snd_intel8x0 index=0
```

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

