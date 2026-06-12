---
title: "[SOLVED] Dual monitors with nVidia"
date: 2008-10-17
forum: Multimedia Software
---

### Post by MunkyJunky on 2008-10-17
I'm trying to get dual monitors running with my nVidia 6600LE card, using a 19" as a main screen and a 15" as a secondary screen, each individual X screens. 

I can configure it this way using Nvidia-config tool, but when I click 'apply' then a message is displayed saying not everything can be applied immediately (due to the addition of a new X screen), and I have to save to xorg.conf then restart X. So I click the 'Save to xorg.conf' button, and another message comes up telling my that a cpy of xorg.conf.backup couldn't be made. Clicking ok, all seems well. I log out then in to restart X, and nothing happens - the config tool is unchanged (all settings have gone back, and my 15" monitor is set back to 'disabled'). Any pointers on getting this up and running?

---

### Post by SuperSonic4 on 2008-10-17
Do what you did before but log into nvidia-settings as root by pressing alt+f2 and typing the code below

```
gksudo nvidia-settings
```

---

### Post by MunkyJunky on 2008-10-17
Genius. Why did I not think of root? Got it going now, little bit fuzzy but that'll having something to do with the settings. Cheers!

---

### Post by SuperSonic4 on 2008-10-17
Don't be too hard on yourself, m_duck told me how to do it when I first started out

---

### Post by charlieab1 on 2009-01-28
thanx worked a treat

---

