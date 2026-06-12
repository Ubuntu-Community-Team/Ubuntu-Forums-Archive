---
title: "New graph-card trouble."
date: 2006-08-05
forum: Multimedia &amp; Video
---

### Post by Epikuros on 2006-08-05
I bought a new Club 3D AGP Geeforce 6600. Everything works fine during the loading screen but when I try to start X it just shows this strange 8-bit-like pattern. 

I have tried detecting it with: dpkg-reconfigure -phigh xserver-xorg 
but it still doesn't show X other than in that pattern and I can't see anything. :-( 

Can anyone help?

---

### Post by Jagot on 2006-08-05
Have you installed the Nvidia drivers?  If not that may help:

```
sudo aptitude update
sudo aptitude install nvidia-glx
sudo nvidia-glx-config enable
```

Then restart.

---

### Post by Epikuros on 2006-08-05
That worked great. Thanks! :)

---

