---
title: "Will Linux ever give me sound?"
date: 2006-05-11
forum: Multimedia &amp; Video
---

### Post by shurguywutt on 2006-05-11
I have been having problems getting sound for the past week. I am pretty new to linux and I run ubuntu 5.1 "Breezy Badger" edition. I run the following command in my console...  I have a "Creative Sound Blaster Live! 24-bit (SB0410) Internal PCI - VAR" sound card.

-------------------------------------------------------------------
cat /proc/asound/cards
-------------------------------------------------------------------
and get this

0 [ICH5 ]: ICH4 - Intel ICH5
Intel ICH5 with AD1985 at 0xfebff800, irq 17
1 [CA0106 ]: CA0106 - CA0106
Live! 7.1 24bit [SB0410] at 0xb800 irq 18

--------------------------------------------------------------------

Does anyone know how to set up sound for my card? I have tried everything. Help! ](*,)

---

### Post by louis_nichols on 2006-05-11
try [here]("https://wiki.ubuntu.com/HowToConfigureSoundBlasterAudigySEinBreezy?action=show&redirect=HowToSetupSoundBlasterAudigyInBreezy"). It's a different sound blaster model, but looks like the same problem you have.

---

