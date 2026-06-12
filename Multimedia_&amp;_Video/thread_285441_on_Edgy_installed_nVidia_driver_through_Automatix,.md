---
title: "on Edgy: installed nVidia driver through Automatix, wrong resolution. help!"
date: 2006-10-26
forum: Multimedia &amp; Video
---

### Post by syxbit on 2006-10-26
I had this problem with Dapper, but would run
```
sudo dpkg-reconfigure xserver-xorg
```
and with the auto config, it would fix it (i have an Asus A8Jm 1280*800 with an nVidia 7600)
i tried the newer nvidia drivers from their website, but that crashed my X.org
any ideas ?

---

### Post by rmjb on 2006-10-26
Hi, when you execute that command to reconfigure X, run through the entire thing, usually the defaults will work but when you get to the Video modes screen, where it lists resolutions, make sure to go through the list and deselect any resolutions that wont work with your card. You say you have a 1280*800, I'd deselect any resolutions above that entry in the list.

- rmjb

---

### Post by syxbit on 2006-10-27
i often video out to my external monitor (a 24" 1920*1200)
so i just have those 2 resolutions listed
1920*1200
1200*800

---

### Post by tseliot on 2006-10-27
Try point 10 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

Then if that didn't solve the problem:

Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

