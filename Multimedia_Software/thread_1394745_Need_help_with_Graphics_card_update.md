---
title: "Need help with Graphics card update"
date: 2010-01-31
forum: Multimedia Software
---

### Post by unrealjeff on 2010-01-31
Hello, i'm fairly new to ubuntu i've been using it for about year and a half maybe more. But I want to play a game called regnum but when i launch the game it and error occurs. The error says either my video card is too old, I need to upgrade my driver, or i need to install the latest version of directX. Now the graphics card i'm using is an Intel Mobile 915GM/GMS/910GML can anyone help me with this?

---

### Post by Yellow Pasque on 2010-01-31
DirectX? Are you running this game in WINE?
EDIT: The requirements aren't very hefty. Your GPU should be able to run it. Post the output of:
```
glxinfo
```

---

### Post by Ferrat on 2010-01-31
Intel Mobile 915GM/GMS/910GML can not handle Regnum, hardly even on Windows as I understand it and the Intel drivers for linux when it comes to 3D is more or less useless

ALSO regnum has a native Linux client that works well :)

---

### Post by Yellow Pasque on 2010-01-31
The Intel Linux drivers are actually better than Intel's Windows drivers for OpenGL apps, so the OP should be able to run the Linux client.

---

