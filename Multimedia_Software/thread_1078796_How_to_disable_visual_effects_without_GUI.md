---
title: "How to disable visual effects without GUI"
date: 2009-02-23
forum: Multimedia Software
---

### Post by Zuajiu on 2009-02-23
Hello,

I recently tried to use the advanced visual effects (even though i knew that my drivers where not the right ones... having problems with nvidia drivers, already in another thread),
and well when i did it it gave me a kind of blank screen, with another blank screen in the middle, then it went back to normal.

Then after i restarted well everything was blank, thought there seemed to have some blank screens in the middle again, 
the UI was probably open, but because of the visual effects I just cant do anything.

How can i disable those visual effects through the CL?

Thanks in advance for any help.

---

### Post by kerry_s on 2009-02-23
the settings should be in your home folder, so i guess renaming/deleting that should get you back to stock.

use> ls -a <to see the folders
use> cd .name <to go inside

once you locate the settings file for the program that you made the changes in rename it to something else.
example:
mv filerc stoprc

if it works out you can delete the old one from the gui, if not you can put it back.

mv stoprc filerc

---

### Post by Zuajiu on 2009-02-23
Thanks, but would you know what the name of the conf file is?
I don't have a clue, I just modified the parametre Advacned effects int the KDE Windows parametres, and that's all.
Sorry, I'm not a very experienced one at this

---

### Post by kerry_s on 2009-02-23
> **Zuajiu said:**
> Thanks, but would you know what the name of the conf file is?
I don't have a clue, I just modified the parametre Advacned effects int the KDE Windows parametres, and that's all.
Sorry, I'm not a very experienced one at this

i have no idea, i haven't used kde in a year.
it would be in the .kde folder.

if it would make it easier to do in the gui, you can do the whole .kde folder, then it will create a stock new one and you can fix it from there and move it back.

mv ~/.kde ~/.kde.old

---

