---
title: "[SOLVED] How to install the nVidia video drivers"
date: 2008-06-29
forum: Multimedia Software
---

### Post by chroncile on 2008-06-29
Hi, I installed the nVidia video drivers from the restricted drivers manager, but I'm getting slow performance on games and I want to install the official drivers from the nVidia website:

[http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

I don't want to use the restricted drivers one because that one has slow performance. Please teach me how I can install the official drivers, by the way, the official ones are .run so how would I install them?

Thanks. :)

---

### Post by Tomatz on 2008-06-29
> **chroncile said:**
> Hi, I installed the nVidia video drivers from the restricted drivers manager, but I'm getting slow performance on games and I want to install the official drivers from the nVidia website:

[http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

I don't want to use the restricted drivers one because that one has slow performance. Please teach me how I can install the official drivers, by the way, the official ones are .run so how would I install them?

Thanks. :)

It is probably because you have compiz running.

Before you start a game open a terminal and type:

```
metacity --replace
```

*This will disable compiz temporarily*

Then start your game and all should be fine ;)

---

### Post by Pjotr123 on 2008-06-29
The restricted driver IS the official driver made by Nvidia. Only the version in the Ubuntu repositories is an older version.

What you want to do is use a newer version, that's all. It will be a very difficult thing to do and the result will (at best) be zero: the performance will be the same.

You can disable visual effects (Compiz), as another poster suggested. A good tip. You can also do that in the menu, as follows:
[http://ubuntutip.googlepages.com/tipsandtweaks](http://ubuntutip.googlepages.com/tipsandtweaks)
(number 5 )

---

### Post by chroncile on 2008-06-29
Nevermind, I figured it out my self, you have to shutdown the xserver then tty login and install it. 
Performance does change because nvidia is constantly improving their drivers in performance. Check the logs. :popcorn:

---

