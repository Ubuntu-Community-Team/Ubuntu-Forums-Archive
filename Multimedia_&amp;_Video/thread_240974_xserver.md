---
title: "xserver"
date: 2006-08-21
forum: Multimedia &amp; Video
---

### Post by xunq on 2006-08-21
hi,
i a newbie in linux i have installed a kubuntu but i have a problem with the xserver...
i reconfigured it with the command dpkg-reconfigure xserver-xorg
i chose the vesa and vga but this want and want work](*,) 
when i boot kubuntu i become a kubuntu logo and at this point freez...:confused: 
how can i become a xorg.conf to post it here:-k 

i have a 1,6ghz athlon(32),maxtor30gb,geforce5200,
philips 17b7cs lcd

Thnx for help 
sorry for my poor english i from slowakia

---

### Post by tseliot on 2006-08-21
> **xunq said:**
> hi,
i a newbie in linux i have installed a kubuntu but i have a problem with the xserver...
i reconfigured it with the command dpkg-reconfigure xserver-xorg
i chose the vesa and vga but this want and want work](*,) 
when i boot kubuntu i become a kubuntu logo and at this point freez...:confused: 
how can i become a xorg.conf to post it here:-k 

i have a 1,6ghz athlon(32),maxtor30gb,geforce5200,
philips 17b7cs lcd

Thnx for help 
sorry for my poor english i from slowakia

1) Boot in Recovery mode (choose it from the GRUB menu almost as soon as you turn on your computer)

2) Type:
```
sudo apt-get update
```

```
sudo apt-get install linux-386 nvidia-glx
```

```
sudo nvidia-xconfig
```

3) Restart your computer:
```
sudo reboot
```


If that doesn't work we'll try another method.


P.S. I'm moving this thread to the Video & sound section

---

### Post by linuchsan on 2006-08-21
start to look at Xorg.0.log. It is in de /var/log dir.

---

### Post by xunq on 2006-08-21
with your help guys become i a big smile on my face :mrgreen: 

IT WORKS :D 

Thnx i have a wifi card problem but i look around and will i make it - when not i ask for help

BIG BIG THNX FOR SUPPORT

---

