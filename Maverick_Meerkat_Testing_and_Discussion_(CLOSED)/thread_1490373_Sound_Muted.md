---
title: "Sound Muted"
date: 2010-05-22
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by cecilpierce on 2010-05-22
Why is the sound muted on reboot ?
Anybody else ?

---

### Post by dino99 on 2010-05-22
you are not alone  :(

the latest updates broke everything about pcie on my end, so no sound output, cant switch window screens, window flashing, cant enter password because console is flashing and entry is zeroed each second, ...

---

### Post by dagrump on 2010-05-22
Well, if you can un-mute it & get sound, you are better off then I. Have no sound now at all. 
The joys of testing, gotta luv it!!  :) :) :)

---

### Post by chrismine on 2010-05-22
Same happened in Lucid too.

---

### Post by dino99 on 2010-05-22
> **chrismine said:**
> Same happened in Lucid too.

not related

---

### Post by dino99 on 2010-05-23
finally be able to unmute sound using gnome-alsamixer and pulse volume control

---

### Post by jppr on 2010-05-23
I don´t have any sound problem, rythmbox and youtube works fine :popcorn:

---

### Post by dino99 on 2010-05-23
> **jppr said:**
> I don´t have any sound problem, rythmbox and youtube works fine :popcorn:

dont worry about that, its normal :P

---

### Post by Pioneer5000 on 2010-05-23
Sorry, please ignore. Posted in wrong place.

---

### Post by garvinrick4 on 2010-05-23
[LIST]
[*]Mute Fix.
[*]
[*] load-module module-device-restore in [/etc/pulse/default.pa]("file:///etc/pulse/default.pa") with  #load-module module-device-restore
[/LIST]
       
        I just commented out that one line and it worked for me. Give it a try.

---

### Post by cecilpierce on 2010-05-24
> **garvinrick4 said:**
> [LIST]
[*]Mute Fix.
[*]
[*] load-module module-device-restore in [/etc/pulse/default.pa]("file:///etc/pulse/default.pa") with  #load-module module-device-restore
[/LIST]
       
        I just commented out that one line and it worked for me. Give it a try.

Thanks alot, that did the trick ! :)

---

### Post by garvinrick4 on 2010-05-24
> **cecilpierce said:**
> Thanks alot, that did the trick ! :)
Mark as solved.

---

### Post by ranch hand on 2010-05-24
I have had that problem on and off for several releases.

This does seem to fix it.  Never really bothered me a lot but this is nicer.

Thanks a bunch.

---

