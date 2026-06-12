---
title: "Intel HDA 82801H Issue"
date: 2008-07-17
forum: Multimedia Software
---

### Post by Fiki on 2008-07-17
I recently bought a new Gateway laptop with an Intel HDA 82801H sound device. I installed the 64 bit version of 8.04. The sound plays, unfortunately there is no way for me to control the volume. Changing the volume using the default ubuntu mixer has no effect on the actual sound volume. Muting has no effect either. The driver seems to be installed and the device is recognized by the OS. After running alsamixer the audio just stops completely until I reboot again (this may or may not be relevant to the solution). If I can't get the audio working properly with volume control I just may cry - and not in any manly way either.

---

### Post by Fiki on 2008-07-17
Basically, the issue isn't that the sound isn't working it's that the laptop is stuck on max volume regardless of how I change the mixer. Any suggestions?

---

### Post by Fiki on 2008-07-17
I'm much dumber than I thought - although controlling the master volume has no effect (that does still seem odd to me) controlling the PCM or front sliders do effect the volume appropriately. However, an issue still remains - under system>prefrences>keyboard shortcuts I can only create a shortcut for the master volume, but not for the front volume. Is there any other way to do this so I can use my laptop's buttons to change the volume rather than using the slider?

---

### Post by wolfen69 on 2008-07-17
right click your little speaker icon and select preferences. then select "front".

---

### Post by Fiki on 2008-07-17
Yes I am aware of that, but I can't get the keyboard shortcuts to change anything other than master volume.

---

### Post by Fiki on 2008-07-17
Now, the audio actually clips out every few seconds. Does anyone know how I can get an ICH8 family card to work in 8.04?

---

