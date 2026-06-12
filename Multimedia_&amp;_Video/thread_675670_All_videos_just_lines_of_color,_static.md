---
title: "All videos just lines of color, static"
date: 2008-01-22
forum: Multimedia &amp; Video
---

### Post by malfist on 2008-01-22
I rebooted my computer and now none of my videos work in totem. None, no matter what codec. They all show the same lines of static of random colors.

Anyone have any idea why it's doing this?

---

### Post by eye208 on 2008-01-23
Are you using the Nvidia driver?

---

### Post by malfist on 2008-01-23
Yes. Installed by envy.

---

### Post by eye208 on 2008-01-23
Press Ctrl+Alt+F1 and then Alt+F7 to switch to the text console and back to the GUI. The problem should be gone then.

---

### Post by disturbed1 on 2008-01-23
> **malfist said:**
> 

Anyone have any idea why it's doing this?

Your overlay device is in use. Most likely you're using Xv and compiz. It's a known bug in Xorg with the composite extension and/or nVidia binary driver.

Other options are to disable compiz, switch the resolution from one size then back again.

---

### Post by malfist on 2008-01-23
I am not using beryl, compiz, or compiz-fusion. Switch tty's fixed it (if that's what they are called).

---

