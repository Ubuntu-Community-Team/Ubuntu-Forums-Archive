---
title: "No jacksupport in Ubuntu Studio"
date: 2008-12-19
forum: Multimedia Software
---

### Post by zettberlin on 2008-12-19
I was about to set pulseaudio to use jackd - it can, if the jack-sink is enabeled.

BUT: I did not find the jacksink in the settings-panel nor in synaptic.

Even though I use the thing called "Ubuntu Studio".

I was quite sceptical about the introduction of pulseaudio into Ubuntu - I thought, the jacksink would not work perfectly well in an pro-audio setup.
Now I see, that there is no such thing as Ubuntu Studio since pro-audio support is ignored by those, who make decisions for what Ubuntu can do.

No jack support for pulseaudio
No jacksupport for xinelib
No RT-Kernel

Ubuntu Studio was a big favourite in the Linux Audio scene - I guess, this is history. 
Open Suse supports all this out of the box and you can easily install the JAD-packages if you want even more...

---

### Post by markbuntu on 2008-12-19
You need to get the pulse-jack packages from the debian repos and make a little script to launch them from jack control. It is all explained here and works in both Hardy and Intrepid

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

