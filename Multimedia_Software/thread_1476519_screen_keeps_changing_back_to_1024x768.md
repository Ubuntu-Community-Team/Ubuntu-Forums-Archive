---
title: "screen keeps changing back to 1024x768"
date: 2010-05-07
forum: Multimedia Software
---

### Post by TK-Tex on 2010-05-07
I have a NEC Multisync 95 monitor. I try to change the screen to 1152x864, but when I restart the computer it goes back to 1024x768. I have a nvidia GForce 6100. Plus I keep getting a message on start up stating that I have an "Error probing smb1". I don't know if this has anything to do with the change but the message also includes something about an "nforce call out search" Can anyone help?

---

### Post by wojox on 2010-05-07
Are you setting it through root?

```
gksudo nvidia-settings
```

---

### Post by TK-Tex on 2010-05-08
Yes I am Wojox. Actually I am using the Nvidia settings control in the administrative settings.

---

### Post by wojox on 2010-05-09
> **TK-Tex said:**
> Nvidia settings control in the administrative settings.

That's not quite the same. Open a terminal and run:

```
gksudo nvidia-settings
```

Configure the resolution and save it.

---

### Post by xc3RnbFO8P on 2010-05-10
> **TK-Tex said:**
> Yes I am Wojox. Actually I am using the Nvidia settings control in the administrative settings.

Did you try to change the resolution in 
Preferences> Monitors (It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?)**_ No_**
Lucid Monitors, Karmic Display.

---

