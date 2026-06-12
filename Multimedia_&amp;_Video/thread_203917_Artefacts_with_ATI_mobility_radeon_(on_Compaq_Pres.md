---
title: "Artefacts with ATI mobility radeon (on Compaq Presario 2110EA)"
date: 2006-06-26
forum: Multimedia &amp; Video
---

### Post by nocturn on 2006-06-26
I'm installing Ubuntu Dapper on a friend's laptop.  It has an ATI mobility radeon onboard.

xorg.conf uses the ati driver (auto-detected).  
Now, the buttons in applications show artefacts (a black dotted grid) which disappears when I pass the mouse over them, other screen areas are unaffected.

Is there a way to fix this?  Do I need another driver for this card (radeon)?  

Thanks

---

### Post by numb401 on 2006-06-26
Hey I have the same problem but had no luck installing the radeon drivers which supposidly WILL work with my mobility radeon. I'm also running a laptop (IBM T30), has anybody shed any light on this problem?

---

### Post by nocturn on 2006-06-26
I may trye the vesa drivers, don't know if they'll do 1024x786...

---

### Post by numb401 on 2006-06-26
I run 1400x1050, no way I could drop to anything below that! Im searching through the forums right now to see if I can find a simple way to get the radeon   drivers(which I know should work with our cards) installed.

---

### Post by nocturn on 2006-06-26
[QUOTE=numb401]I run 1400x1050, no way I could drop to anything below that! Im searching through the forums right now to see if I can find a simple way to get the radeon   drivers(which I know should work with our cards) installed.[/QUOTE]

Can you modprobe radeon?  (I'm not on the machine right now)

---

### Post by nocturn on 2006-06-26
Does this work for you?
[https://wiki.ubuntu.com/RadeonDriverHowto](https://wiki.ubuntu.com/RadeonDriverHowto)

---

### Post by numb401 on 2006-06-26
yea modprobe radeon works, I had some sucess installing the radeon drivers at [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/) but the artifacts are still there :(
the wiki did NOT work for me last night.
I untarred the file then did the ./install.sh My glxgears went up from high 100s to high 300s.

---

### Post by nocturn on 2006-06-26
A shame the the artifacts remain...  Which is my only conern right now (3D is not needed).

Do the restricted drivers work on mobility radeons?

Have you tried other themes (I haven't).

---

### Post by numb401 on 2006-06-26
I tried the older ATI restricted drivers, right off their website and it was a no-go, thank god for backups! You could give it a shot but I'm almost positive they don't work on older radeon cards. I wonder what the **** is causing these artifacts, I've even tried lowering my color depth to no avail.

---

### Post by numb401 on 2006-06-26
Fixed it! Its the simplest solution in the world. Word is on these forums that the default theme (Human) sucks, I changed to almost any other theme and voila, artifacts are gone!...now im off to fix my 3d :(

---

### Post by nocturn on 2006-06-26
[QUOTE=numb401]Fixed it! Its the simplest solution in the world. Word is on these forums that the default theme (Human) sucks, I changed to almost any other theme and voila, artifacts are gone!...now im off to fix my 3d :([/QUOTE]

I'm curious, what theme did you choose?

---

### Post by numb401 on 2006-06-26
Right now I'm running mist, ive never been into those ultra-fancy themes.

---

