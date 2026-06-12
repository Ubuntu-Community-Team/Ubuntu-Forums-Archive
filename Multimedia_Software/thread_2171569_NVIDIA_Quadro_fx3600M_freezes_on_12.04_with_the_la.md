---
title: "NVIDIA Quadro fx3600M freezes on 12.04 with the latest drivers"
date: 2013-08-31
forum: Multimedia Software
---

### Post by blz on 2013-08-31
Hi all,

The problem is that my system (12.04) freezes a minute after logging in. The mouse can be moved but the UI and everything else is absolutely not responding.

I've already lost almost a day trying to find the drivers for my graphic card that will NOT freeze the system. I've know this problem for a while and had it solved in Windows with the 275.33 version. But now I cannot solve it in Ubuntu 12.04. 

[B]My graphic card is: NVIDIA Quadro(Notebook) fx3600M 
My laptop: HP Compaq 8710w
OS: Ubuntu 12.04 LTS x64[/B]

Please help me find the drivers that work!

Thank you in advance!

---

### Post by blz on 2013-09-04
**Version: 304.88**
And setting the **PowerMizer** setting "Preferred Mode" to "**Prefer Maximum Performance**" in the **nvidia-settings** panel **fixed it for me.**
(P.S. The nvidia-settings panel has a bug and doesn't save/load the configuration you make. Because of that I had to create a script that sets that value manually:
(sleep 10 && DISPLAY=":0.0" nvidia-settings -a [gpu:0]/GPUPowerMizerMode=1) &

---

### Post by mickee384 on 2013-12-04
where did you put the script?

---

