---
title: "[SOLVED] not envious of ENVY"
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by shalemjale on 2008-03-12
I used ENVY to try to make my compiz work but it has messed up my monitor such that it will not boot into Ubuntu.
Being a newbie, how do I reset my video card to low res graphics w/o opening up the desktop?:confused:

---

### Post by scragar on 2008-03-12
from a command line(ctrl+alt+F1) run ```
envy --uninstall-all
``` then restart(either a hard reset or from the command line:```
sudo shutdown -r now
``` to restart should be fine) to remove anything envy has done.

---

### Post by overdrank on 2008-03-12
> **shalemjale said:**
> I used ENVY to try to make my compiz work but it has messed up my monitor such that it will not boot into Ubuntu.
Being a newbie, how do I reset my video card to low res graphics w/o opening up the desktop?:confused:

Hi and have you tried to reconfigure you xorg? you can try and boot into recovery mode which is usually the second choice in the grub. Then reconfigure your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Then use the command ```
reboot
``` hopefully this will get you to a GUI, Desktop. Good luck.

---

### Post by scragar on 2008-03-12
@ overdrank : If envy caused the damage then surely it's best to let envy simply undo any changes than having xorg completely reconfigure itself? Esspecialy since it will leave the envy drivers installed(even if it's not using them).


on a side note I prefare shutdown -r over reboot, so much more control :P.

---

### Post by shalemjale on 2008-03-12
scragar,
I did as you said but the monitor is still messed up/unclear. I can get a prompt but that's all. Any other suggestions?

---

### Post by scragar on 2008-03-12
if envy couldn't clean itself up then do as overdrank said and reconfigure xorg.

---

### Post by overdrank on 2008-03-12
> **scragar said:**
> @ overdrank : If envy caused the damage then surely it's best to let envy simply undo any changes than having xorg completely reconfigure itself? Esspecialy since it will leave the envy drivers installed(even if it's not using them).


on a side note I prefare shutdown -r over reboot, so much more control :P.

Hi and I was just offering a possible solution as I have used envy several occasion and had to reconfigure the xorg after. Yes shutdown -r is a option but I would use shutdown -r now. I believe the op is trying to install the drivers for a ati 200 graphics that in itself has issue. :)

---

### Post by shalemjale on 2008-03-12
Thanks to both of you. I am writing this from Ubuntu instead of xp.=D>

---

