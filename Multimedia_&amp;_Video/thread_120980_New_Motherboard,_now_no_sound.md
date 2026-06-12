---
title: "New Motherboard, now no sound"
date: 2006-01-24
forum: Multimedia &amp; Video
---

### Post by synd7 on 2006-01-24
I installed a new motherboard recently and it caused my sound to stop working.
I have tried changing System>Preferences>Sound from the integrated intel sound card to mine but it reverts to the intel one as soon as i close that window.

The card is a pci soundblaster but is read by ubuntu as an ensoniq audiopci (its always been like that though)

I have had to re-install windows due to the new mobo (dw, i expected that) but this was unexpected.

any ideas on what to do?

---

### Post by FarEast on 2006-01-24
Hi,
Can you disable the integrated intel sound card by editing BIOS setting?

---

### Post by synd7 on 2006-01-24
No I cant. But i can verify that the integrated card works fine

Is there any way to re-run the tests done at installation to install the correct drivers etc?
I think that may help.

---

### Post by FarEast on 2006-01-24
OK!
Edit /etc/modprobe.d/sound as follows:
options (module for sound blaster) index=0
options (module for integrated card) index=1
Then execute 'sudo update-modules' and restart the system.

cf. Execute 'lsmod | grep snd' to know the module names.

---

