---
title: "How to remove video driver module, for VESA?"
date: 2010-09-16
forum: Multimedia Software
---

### Post by Moozillaaa on 2010-09-16
I'm trying to remove 3Dlabs / Oxygen gmx , and install vesa - Generic VESA-compliant video driver module.

How do I remove 3Dlabs / Oxygen gmx ?

I can click on VESA in the 'Choose By Name...' , but when I close that box, it shows No Driver.

Help? Hardy 64x (and I have another machine, same CPU, ram, same video chip, not this problem)

---

### Post by Yellow Pasque on 2010-09-16
```
sudo apt-get remove xserver-xorg-video-glint
```

---

### Post by Moozillaaa on 2010-09-16
Thanks - but I removed it from Synaptic, and to be sure, I ran the code that you posted, and it returned "Not installed".

It's still showing up in the Screen / Graphics preferences, and not allowing me to choose VESA driver...

---

### Post by Yellow Pasque on 2010-09-16
Make an xorg.conf with vesa driver?

---

### Post by Moozillaaa on 2010-09-16
I added that manually, restarted X, and got a "Nautilus can't be used right now, because of an unexpected error". The desktop did load...

???

And the Screen and Graphics dialog DID show VESA loaded, but resolution still can't be adjusted higher.

---

