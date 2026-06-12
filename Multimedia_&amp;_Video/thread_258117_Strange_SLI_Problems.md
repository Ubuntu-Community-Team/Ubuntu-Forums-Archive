---
title: "Strange SLI Problems"
date: 2006-09-15
forum: Multimedia &amp; Video
---

### Post by ErikTheRed on 2006-09-15
I'm running 2 6800GT's in my system in SLI. They work fine in Windows, but when I enable SLI in my xorg.conf in Kubuntu I run into all sorts of issues. Sometimes my whole system will freeze, usually right after I login. Lately I've been able login okay, but when I run an OpenGL app the window for that app is totally black.

Another strange note, in Dapper if I used the stock kernel SLI would work fine, but if I compiled 2.6.17 with smp support enabled and tried to enable SLI my system would show these symptoms. Right now I'm using Edgy and I'm still running into the problem even though I'm running the stock kernel.

This seems like a fairly complicated problem, maybe I should consider contacting nvidia?

EDIT: Strange, after a couple restarts of the X server everything is working. I still find this a bit weird.

---

### Post by orangek3nny on 2006-09-15
I just noticed when i turn on "polygon-antialising" in armagetron, then the game gets nearly unresponsible and i get 100& cpu usage.
Maybe thats also the problem with tuxracer? :/

EDIT:
sorry...wrong thread..please delete

---

### Post by fatboysmith on 2006-11-11
I have the same issue.  I enable SLI in xorg.conf and I get a hang up / freeze at the NVIDIA spash screen or my monitor just goes blank / no signal.  I can login fine using the 386 non SMP kernel.  Is this an NVIDIA driver issue?  I have Nforce4-SLI w/ Opteron 180 (X2-4800+) processor.  I logged in w/ 386 kernel and rem out the SLI AUTO line in xorg.conf and it boots ok.

---

### Post by fatboysmith on 2006-11-12
I found this solution on the NVIDIA Linux Forums, it worked for me hopefully for you too. 

Add "pci=conf1" to your kernel boot parameters.  Now I get to have SLI & SMP, Quake4 runs like a beast....

---

