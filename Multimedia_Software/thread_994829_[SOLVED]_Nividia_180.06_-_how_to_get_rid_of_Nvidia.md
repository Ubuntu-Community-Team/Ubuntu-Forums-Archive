---
title: "[SOLVED] Nividia 180.06 - how to get rid of Nvidia splash screen?"
date: 2008-11-27
forum: Multimedia Software
---

### Post by Sealbhach on 2008-11-27
Hi, I've installed the Nvidia Beta driver 180.06. All working fine.

However when I boot up I get the green Nvidia logo spash screen.

How do I stop it? 


.

---

### Post by overdrank on 2008-11-27
> **Sealbhach said:**
> Hi, I've installed the Nvidia Beta driver 180.06. All working fine.

However when I boot up I get the green Nvidia logo spash screen.

How do I stop it? 


.

Hi and you may try and add 
Option         "NoLogo" "True"
to you xorg

---

### Post by kpkeerthi on 2008-11-27
Add the line highlighted to your /etc/X11/xorg.cong under Devices section and reboot.
```

Section "Device"
  Identifier "Nvidia 7800 Go GTX"
  Driver     "nvidia"
**[COLOR="Red"]  Option     "NoLogo" "true"[/COLOR]**
EndSection

```

---

