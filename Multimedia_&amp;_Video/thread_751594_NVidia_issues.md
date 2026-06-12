---
title: "NVidia issues"
date: 2008-04-10
forum: Multimedia &amp; Video
---

### Post by DownwWindows on 2008-04-10
Hello I have a GeForce Fx5200 and I cannot change my resolution to other than 640x800, could anyone help me out ? I have installed the nVidia driver with its control pannel and other gizmos and still I have the same problem.

---

### Post by wolfen69 on 2008-04-10
in terminal:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by DownwWindows on 2008-04-10
Thanks for answering but then, what am I supposed to do ?

---

### Post by overdrank on 2008-04-10
> **DownwWindows said:**
> Thanks for answering but then, what am I supposed to do ?

HI and this will allow you to reconfigure your xorg which you will select your graphics driver and resolution and so on.
This link may help
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by DownwWindows on 2008-04-11
Thank you all for answering, I finally got rid of my problems by finding my monitor's brand in the display list ! Then Bingo ! Everything is under control !

---

