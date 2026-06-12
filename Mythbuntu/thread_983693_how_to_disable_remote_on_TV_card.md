---
title: "how to disable remote on TV card"
date: 2008-11-15
forum: Mythbuntu
---

### Post by 4dognight on 2008-11-15
I have a problem with my remote. I have both the PVR350 and Kworld115 installed in the same server. I want to use the PVR350 remote. 
Problem is it is very unresponsive. 

I have the "useoptions" set in my xorg.conf. This is not the problem.
I beleive it is conflicting with the other remote on the other card. 

If I disable the saa7134 driver, then my PVR350 remote works fine.

Does anyone know how to disable just the remote on the kworld115 card?

I tried to blacklist  ir_kbd_i2c, but it didnt seem to work. It still loaded.

---

### Post by ian dobson on 2008-11-16
Hi,

Maybe you can try creating a file in /etc/modprobe.d that contains the following text "options saa7134 card=90 disable_ir=1"

something like

echo "options saa7134 card=90 disable_ir=1" > /etc/modprobe.d/Kworld115.conf

Then rebooting.

Regards
Ian Dobson

---

### Post by 4dognight on 2008-11-16
OK, I have now tried that. So far it seems better than before, but not really responsive. I will give it a few days. As it sometimes seems to take a while before it gets worse. This server is running a P4 1.6. While playing back it is only using about 30% CPU, but it still hesitates when I press a button on the remote. It even causes the video to stutter on each press of a button. When I test it using irw, it is very responsive.

---

