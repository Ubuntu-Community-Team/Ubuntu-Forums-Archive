---
title: "Sound issues and sound profile issues"
date: 2010-05-28
forum: Multimedia Software
---

### Post by Oblivionsfate on 2010-05-28
I am having issues with my sound on the latest version of Ubuntu. My computer is a desktop and i don't have an actual sound card just the built in on on the mother board. But either way on to the problem,  every time i launch wine, or firefox i have to go into the sound prefences and change what type of sound profile that i am using otherwise the sound doesn't work.  any ideas as to why this is happening and how to fix it?

Sorry if this has already been covered before but i didn't see it.

---

### Post by lidex on 2010-05-30
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by aleb on 2010-05-30
> **Oblivionsfate said:**
> every time i launch wine, or firefox i have to go into the sound prefences and change what type of sound profile that i am using otherwise the sound doesn't work.
Where exactly do you change the type of sound profile?

---

