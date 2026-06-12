---
title: "KORG Kaoss Pad"
date: 2007-08-29
forum: Multimedia Production
---

### Post by sprizz on 2007-08-29
Hey guys,
   Im completely new to Ubuntu/Linux period so dont make fun of me if i have no clue about anything.  I saw a video for the KORG Kaoss pad on youtube and thought wow i bet someone could make a program or something using the touchpad on a notebook and that linux is what it could be done on.  I currently have Ubuntu ...the newest version i forget the number sorry...running on a Gateway Solo Pro 9300 and if anyone knows where i could get something like that it would be much appreciated.

Thanks,
Sprizz

---

### Post by distort on 2007-09-01
The Kaoss Pad is a Midi Controller, Linux supports Midi, so hardware-wise it works.
The main problem probably is to interpret/re-route the Midi data incoming from the Kaoss pad.
You could look at a program called Pure Data, also known as pd.
It's similar to Max/MSP and takes some time to learn, but in theory it's able to do nearly anything you want with the Midi data. 
Pd is a graphical programming language primarily conceived for live performances.
There are many extensions for it freely available, and given the popularity of the Kaoss pad,
pd externals (that's what extensions for Pure Data are officially called) for that purpose might exist.

---

### Post by sprizz on 2007-09-01
thanks and what you said does make since but has anyone found something like this before? I googled it and found nothing, well nothing in the first 20 something pages...i have no idea about programing for linux so theres no way i could make something like that

---

### Post by holotone on 2008-01-20
Kaoss Tools for pD
[http://puredata.info/community/patches](http://puredata.info/community/patches)

> A few abstractions to get the most out of your Kaos Pad under PD. Send 32 different pairs of controller numbers, switchable with the Program Change knob on your hardware, and customize a named canvas which displays the current parameters being changed.

---

