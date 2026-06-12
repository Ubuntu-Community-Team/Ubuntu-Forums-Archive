---
title: "I have a resolution problem."
date: 2008-09-13
forum: Multimedia Software
---

### Post by DarknessEnemy on 2008-09-13
Hello, Nice to talk in here again.

I got a problem with my laptop.

Normally I have the 1280 resolution and I tried to install another monitor, K told me to restart the x server. Now I regret it.

1.- Both of my screens have 640 resolution. Tried to restore it.

2.-I unmarked the "second screen" mark, so I disconnected my 2nd monitor and restarted it. Now when the login window should appear, appear a "like" command promt. Only the login window appears when both monitors are connected, but still in 640 resolution.

3.- I cant rise the resolution.

Please, I beg for help here. I hope you can help me.

Thanks in advance.

PD: Sorry about my bad english.

---

### Post by cariboo on 2008-09-13
In a terminal try:

```
displayconfig-gtk
```

That should let you choose the resolution you need.

Jim

---

### Post by DarknessEnemy on 2008-09-14
No, I still have the problem, I just don't know what to do.

I dont know how to tell the settings to remove the 2nd monitor and restore my previous settings T.T.

Please, I someone know how to restore it, help me.

Thanks in advance.

---

### Post by cdtech on 2008-09-14
Best to get into recovery mode and type:
sudo dpkg-reconfigure -phigh xserver-xorg

Hope this helps......

---

### Post by DarknessEnemy on 2008-09-14
It worked, thank you so much.

I Really appreciated it.

---

