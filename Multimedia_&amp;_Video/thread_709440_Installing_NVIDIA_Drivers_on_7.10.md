---
title: "Installing NVIDIA Drivers on 7.10"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by Ephemeral on 2008-02-27
Hello ^^

I have recently installed Ubuntu again, this new version is great, definitely giving up XP for this.
I managed to get Counter Strike running and reached a max 10.9 fps on the menu, didn't even bother trying to play. On Xp I was getting 700~900 fps on the menus at least.

So I thought the drivers might be to blame since the actual NVIDIA drivers weren't installed.
I downloaded them from the site, renamed the file to NVIDIA.run and ran this commande in console :
```
sudo sh NVIDIA.run
```

It seems to start, dots appearing, eventually a graphical installation thing comes up to tell me I need to stop the X server to install the drivers.
I pretty much looked all over to find answers but nothing helped.

I saw the pinned topic about installing NVIDIA drivers but it only covered until 7.04 and I am ussing 7.10

Any ideas ?

Thanks,
~Mark

---

### Post by logos34 on 2008-02-27
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

manually, you would do

cntl+alt+F1 (drop to console)

sudo /etc/init.d/gdm stop

then 

sudo sh NVIDIA....run

---

### Post by z0mbie on 2008-02-27
Before using any scripts or third party programs. I suggest you use this guide:

[http://www.robdian.co.uk/content/view/56/27/](http://www.robdian.co.uk/content/view/56/27/)

Use scripts for only a last resort, otherwise try to find tutorials. 

Btw, this tutorial works with latest versions of nVidia drivers & Gutsy.

---

### Post by logos34 on 2008-02-27
A lot of people have used Envy successfully.  It's not like it's some flaky, obscure script.

---

### Post by Ephemeral on 2008-02-27
Woot, thanks a lot, it's finally working :D

I now have fancy window effects when minimizing them instead of slow black squares going down to the bar :P
And Counter Strike is running beautifully !

Thanks a lot guys =D

---

