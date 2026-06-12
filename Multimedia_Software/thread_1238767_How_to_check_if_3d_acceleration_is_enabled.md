---
title: "How to check if 3d acceleration is enabled?"
date: 2009-08-12
forum: Multimedia Software
---

### Post by pintoosingh on 2009-08-12
My admin has installed nvidia drivers, I would like to check if 3-D acceleration is working or not?

How can I check from command prompt?

I dont have mesa-utils package, and I cant install it as I am not root.

---

### Post by overdrank on 2009-08-12
> **pintoosingh said:**
> My admin has installed nvidia drivers, I would like to check if 3-D acceleration is working or not?

How can I check from command prompt?

I dont have mesa-utils package, and I cant install it as I am not root.

The command is ```
glxinfo | grep direct
``` More info [BinaryDriverHowtoNvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by pintoosingh on 2009-08-12
> **overdrank said:**
> The command is ```
glxinfo | grep direct
``` More info [BinaryDriverHowtoNvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

I dont have mesa-utils and glxinfo is part of it :)

---

### Post by mc4man on 2009-08-12
If he installed the nvidia drivers then direct rendering is in all likelihood enabled.

You could check on that without sudo (the video  driver
lshw -C display

---

### Post by pintoosingh on 2009-08-13
Well lshw is another utility which needs to be installed and I dont have root access :)

---

### Post by overdrank on 2009-08-13
> **pintoosingh said:**
> Well lshw is another utility which needs to be installed and I dont have root access :)

Well then you need to speak with the admin. :)

---

