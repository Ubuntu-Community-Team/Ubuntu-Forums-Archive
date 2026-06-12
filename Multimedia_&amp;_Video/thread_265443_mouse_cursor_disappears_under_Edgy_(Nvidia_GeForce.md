---
title: "mouse cursor disappears under Edgy (Nvidia GeForce 6100)"
date: 2006-09-26
forum: Multimedia &amp; Video
---

### Post by moxfyre on 2006-09-26
Hey all, I've upgraded to the development version of Edgy and nearly everything is fine, except for one baffling problem with X.

When the computer boots and GDM comes up, everything works fine.  However, if I subsequently logout or kill the X server, and then attempt to log back in, the X cursor DOES NOT REAPPEAR!!  I have found no way to restore the mouse cursor other than totally rebooting.  Needless to say, this problem is very annoying since I can't logout without either rebooting or losing the mouse cursor.

I'm running kernel 2.6.17-8 on amd64 Edgy, with the nv Xorg driver.  Any advice?

---

### Post by tseliot on 2006-09-26
There might be a problem with the nv driver.

Try installing the Nvidia driver by following Method 1 of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by moxfyre on 2006-09-26
> **tseliot said:**
> There might be a problem with the nv driver.

Try installing the Nvidia driver by following Method 1 of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

Hey tseliot, it works fine with the nvidia driver... but I was kind of hoping to stick with the nv driver as I prefer the open-source version and I'm told it has better performance for 2D, which is all I use it for.

Has anyone else had this problem with the nv driver??  :confused:

---

### Post by jrgii on 2006-11-03
I have just installed edgy with gforce 6100 also and have the same problem, any solutions?

---

### Post by Pstevens on 2007-07-06
(Newbie posting alert)
Try this - step 9 of the "Problems" section.   I was nervous editing /etc/X11/xorg.conf but it seems to have worked for me.
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)

---

