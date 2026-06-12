---
title: "Graphics card problem"
date: 2010-02-23
forum: Multimedia Software
---

### Post by PeteUplink on 2010-02-23
I need some assistance with my graphics card on my Satellite Pro 2100 on Ubuntu. 

Well the first problem is the refresh rate at 1024x768 will only go to 60hz, but under XP it would run at 85hz, which is better on the eyes. 

The second problem is I've no clue what graphics card is actually installed on this thing. I think it's an nvidia geforce go 420. 

Third problem is that Ubuntu tells me that there is a restricted driver available and I can activate it, but the last time I did this and rebooted, all I got back was a flashing screen and I couldn't do anything.

The laptop is rather old. It was new in 2002.

---

### Post by Matthewthegreat on 2010-02-23
> **PeteUplink said:**
> 

The second problem is I've no clue what graphics card is actually installed on this thing. I think it's an nvidia geforce go 420. 

Just type this into the terminal to find your graphics card: 

```
lspci
```

> **PeteUplink said:**
> Third problem is that Ubuntu tells me that there is a restricted driver available and I can activate it, but the last time I did this and rebooted, all I got back was a flashing screen and I couldn't do anything.

 Thats strange. I don't know whats wrong there but I wouldn't bother with the restricted drivers unless you need 3d.

---

### Post by PeteUplink on 2010-02-23
Thanks for that, it is an nvidia geforce 420 go. 

So is there anything I can do about the low refresh rate? I know it goes up to 85hz, but Ubuntu isn't giving me the option.

---

