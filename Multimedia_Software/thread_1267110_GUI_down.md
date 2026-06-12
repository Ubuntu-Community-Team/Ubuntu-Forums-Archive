---
title: "GUI down"
date: 2009-09-15
forum: Multimedia Software
---

### Post by Feanor93 on 2009-09-15
Okay, here goes,

I have a Radeon 9600 graphics card in my computer, and recently I tried to accelerate the graphics using the  [Radeon Driver]("https://help.ubuntu.com/community/RadeonDriver"). When I restarted the computer, I got a blank screen with mouse and empty taskbars. I don't know a lot about using the terminal, but I know enough to use Ctrl + Alt + F1 to open the terminal. When I tried to edit the xorg.config file using the terminal, it said that I was making a new file.

So to wrap things up, I just want to get my computer back to normal. Accelerated graphics are my secondary objectives. If anyone could give me some help with this I'd be grateful.

Thanks,
Feanor93

---

### Post by viktara on 2009-09-15
You could try moving your xorg.conf and rebooting.

```
mv xorg.conf xorg.conf.backup
```

I think Ubuntu should create a new one for you.

HTH


Vik

---

### Post by Feanor93 on 2009-09-15
It's working now, thanks !

Feanor93

---

