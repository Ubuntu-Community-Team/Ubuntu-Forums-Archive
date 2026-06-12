---
title: "Setting flatscreen up !"
date: 2006-08-10
forum: Multimedia &amp; Video
---

### Post by stefangranholm on 2006-08-10
Hi, I now got installed Nvidia driver peh.

But the screen resulution is 1024*780 and 70Hz, but the screen can go to 1280*1024.

I cant change it in screen size, so is it wrong Nvidia geforce 6600 setup og becouse it dont know my Medion Flatscreen 19" screen ?

stefan

---

### Post by nightmare03 on 2006-08-10
Try running

```
sudo dpkg-reconfigure xserver-xorg
```

I think thats right!

You will be able to reconfigure everything and select 1280x1024 as a resolution.

---

### Post by MetalMusicAddict on 2006-08-10
In a terminal type: **sudo dpkg-reconfigure xserver-xorg**.

Most things you will just stay with the default on. When it askes about the "driver" press down once from "nv" and pick "nvidia". Keep with the defaults and write the config to file.

After that it should ask about your screen. You will be presented with resolution options. With the spacebar check the ones you want then hit enter. After that it will ask you about refresh rates. It will ask you to pick something like Hard-Medium-Easy. Whatever it is pick Medium. Then pick the resolution and refresh you want or know the monitor works at. ie:1280x1024@60hz

---

### Post by stefangranholm on 2006-08-10
Wow, very hard in the start, due to all the settings, but it worked.

Im ready to roll... :o)

THankz a lot.

Im also soon gonna start using/explore edubuntu on my work (Its where I look after children in age 3 - 6 years)

---

### Post by stefangranholm on 2006-08-10
I was 2 quick.

It seems it stucks at 75 htzh.

But it runs good, even my screen only support 50 and 60 hzh.

Will there happen anything to my screen if it runs at 75 hzh ?

---

