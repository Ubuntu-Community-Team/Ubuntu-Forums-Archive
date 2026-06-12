---
title: "Flash in 10.04"
date: 2010-03-20
forum: Multimedia Software
---

### Post by blackconan on 2010-03-20
I just finished installing a copy of 10.04 and I'm trying to install flash. Every time i download the apt file from adobe site an error said " Could not find package 'adobe-flashplugin'. Does anyone know what is going on?

---

### Post by RedSingularity on 2010-03-21
Have you enabled Multiverse and Universe repo's?

---

### Post by blackconan on 2010-03-21
I'm a total noob at ubuntu so I'm guessing I haven't enable it. Could you also tell me how to do so?

---

### Post by RedSingularity on 2010-03-21
Sure, go to....

System>Admin>Software Sources

Look and you will see "Universe" "Multiverse" "Restricted"

Make sure they are all checked except for source code.

Then close that and open a terminal

In a terminal type 

sudo apt-get install flashplugin-installer

---

