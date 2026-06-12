---
title: "[ask] why is xorg.conf is empty in xubuntu 9.04 fresh install?"
date: 2009-08-02
forum: Multimedia Software
---

### Post by freakyjohn101 on 2009-08-02
hi, i just finish installing xubuntu 9.04. why is xorg.conf is empty in xubuntu 9.04? is it intentionally left empty? is there other file for editing device driver? the reason i'm asking is because my video card which is nvidia Geforce 4 mx 440 is somehow always incompatible with all nv driver that comes with every linux distro. the driver nv driver always make my screen frozen. usually i can fix this by change the driver to vesa and download the driver from nvidia and install it, but because the xorg.conf in xubuntu 9.04 is empty, i worried that something has change and if i write something to xorg.conf it will do some damage..

---

### Post by HappyFeet on 2009-08-02
You will have no problems installing the vesa or nvidia driver. Go for it.

---

### Post by freakyjohn101 on 2009-08-02
thx HappyFeet.. i'll try that after downloading nvidia driver...

---

### Post by xc3RnbFO8P on 2009-08-02
Sometime you get a empty xorg.conf if you do:
> gedit /etc/[COLOR="Red"]x[/COLOR]11/xorg.conf
when it should be capital X:
> gedit /etc/**[COLOR="SeaGreen"]X[/COLOR]**11/xorg.conf

---

### Post by markbuntu on 2009-08-03
xorg.conf is in the process of being deprecated by the X consortium. Do not expect to see it in the future.

---

