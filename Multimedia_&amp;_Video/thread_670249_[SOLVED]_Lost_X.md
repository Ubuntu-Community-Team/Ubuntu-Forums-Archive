---
title: "[SOLVED] Lost X?"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by TomR55 on 2008-01-17
I recently purchased an Ibex machine which was configured with the Gutsy. I have an older generation Envision monitor, 19", and have been trying to get Gutsy to use 1440x900@60hz. Problems, many. No matter what I tried, the monitor always came up (note past tense here) with 2 inches or so of dead space to the right.

So, tried Plug-And-Play --now, can't start X. I

I feel pretty dumb, but am not Unbuntu literate. I know, for instance, in SuSE that I could run sax from the prompt, but I don't know what (if anything) can be done in Ubuntu, short of re-installing?

Naturally, I appreciate any suggestions.

Thanks, 


TomR

---

### Post by taurus on 2008-01-17
Boot into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure xserver-xorg
shutdown -r now
```

---

### Post by TomR55 on 2008-01-17
First things first: thank you for your response. I shall try as you suggest, assuming that I can find the Grub "menu." Presently, I've been resorting to alt-ctrl F1 to get to a window where I can type commands. Is this the right place to be when I attempt to execute those lines of code? Or, do I need to find the GRUB menu and follow your prescription as written?

Thank you again...

TomR

---

### Post by TomR55 on 2008-01-18
> **taurus said:**
> Boot into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure xserver-xorg
shutdown -r now
```

Thank you! This worked --or, at least it restored my machine to its previous (livable) state. If worse comes to worse, I can live with the wasted screen space to the left, I suppose.

Thanks, again.

TomR:)

---

