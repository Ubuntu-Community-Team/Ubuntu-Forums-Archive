---
title: "Update Kills HDMI Sound"
date: 2010-06-30
forum: Multimedia Software
---

### Post by jda8818 on 2010-06-30
10.04 LTS.  Installed updates per update manager suggestions today (6/30/2010).  HDMI sound completely dead.

Thank you all in advance for any comments/suggestions

JA

---

### Post by jda8818 on 2010-06-30
per instructions which accompany AlsaUpgrade Script, which suggest that major OS updates might override the AlsaUpgrade script affects, i reran the previously compiled script with the -i suffix.

No Good, aplay -l no longer discovers any sound cards at all!

HELP!!

As Always,  thanks in advance for any comments or suggestions ...

JA

---

### Post by jda8818 on 2010-06-30
Analog  sound also dead, of course ...

---

### Post by Yellow Pasque on 2010-07-01
I would rerun the script with -c and then -i

---

### Post by jda8818 on 2010-07-01
Bingo!

Thanks Temujin.  Reran the script with the -c suffix (compile i suppose), then -i, then shutdown -r 0

and all is well!

many, many thanks ...

JA

---

