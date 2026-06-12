---
title: "resolution problema!"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by Nando-san on 2007-11-27
I can't get UBUNTU to my resolution, it's 1680 x 1050! and when i put it in that resolution it's shorter than my monitor and foggy-like, can't really see well... what should I do?

---

### Post by Yellow Pasque on 2007-11-27
Ok, what kind of video card do you have? Run the following commands and give the output of the second one.
```
sudo update-pciids
lspci | grep "VGA"
```

Also, post your /etc/X11/xorg.conf file

---

### Post by Nando-san on 2007-11-27
ok I did the

sudo update-pciids
lspci | grep "VGA"

and something downloaded and was saved...

how can i help you with the /etc/X11/xorg.conf file   where do i find it?

---

### Post by Nando-san on 2007-11-27
BTW... the video card is INTEL GRAPHICS MEDIA ACCELERATOR 950 or so it says in the PC...

---

### Post by Nando-san on 2007-11-27
any more help:S???

---

### Post by Nando-san on 2007-11-28
???

---

