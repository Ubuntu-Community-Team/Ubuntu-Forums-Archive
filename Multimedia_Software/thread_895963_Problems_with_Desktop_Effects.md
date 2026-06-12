---
title: "Problems with Desktop Effects"
date: 2008-08-20
forum: Multimedia Software
---

### Post by RolandFlagg on 2008-08-20
Hi, I cannot enable my visual effects in the "appearance preferences" to "normal" or "extra", whenever I try it, it says "Desktop effects could not be enabled". I know this is a pretty common problem, and have searched all over the internet, but no one seems to have the same graphic card, so it kind of doesn't help me.
I'm using an Intel 82852/82855. Prior to this my entire resolution was incredibly low, and I had to do ```
sudo apt-get install 915resolution
``` to get a good resolution.
Any ideas to get my desktop effects working as well? thanks a lot!

---

### Post by Shippou on 2008-08-20
Try a full system update, and try installing Xgl.

```

sudo apt-get install xserver-xgl

```

This worked for me. :)

---

### Post by RolandFlagg on 2008-08-20
That didn't work, apparently "[B]xserver-xgl is already the newest version.
[/B]"
thanks though

---

### Post by RolandFlagg on 2008-08-20
Oh yeah, and I forgot to mention, I also seem to have problems with anything 3D, so I think it still all comes back to the computer not recognizing my graphic card.

---

### Post by RolandFlagg on 2008-08-21
OK never mind, I decided to reinstall everything from a hardy live cd, everything works now, I think something screwed up when I originally updated to hardy from feisty

---

