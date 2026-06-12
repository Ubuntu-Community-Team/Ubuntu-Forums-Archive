---
title: "ATI Radeon Desktop 9200 Video card driver ???????"
date: 2006-07-12
forum: Multimedia &amp; Video
---

### Post by wpshooter on 2006-07-12
After reading a goodly portion of the postings regarding the ATI drivers, I am just throughly **confused** !!!

I am going to re-install Ubuntu Dapper Drake to get the driver back to the way it is installed by the stock installation.

If I am supposed to or NOT do anything beyond this to get it to work properly, I would appreciate someone pointing me in the right direction.

Thanks.

---

### Post by Paerez on 2006-07-12
just do:
```
# sudo dpkg-reconfigure xserver-xorg
```
then pretty much hit enter through most of it, and choose the simple options.  When it asks for what video driver you want, just pick "ati".

---

### Post by wpshooter on 2006-07-12
> **Paerez said:**
> just do:
```
# sudo dpkg-reconfigure xserver-xorg
```
then pretty much hit enter through most of it, and choose the simple options.  When it asks for what video driver you want, just pick "ati".

Is it correct, that doing this will put me back exactly where I would have been after the stock installation of Dapper Drake ?

Thanks.

---

### Post by Paerez on 2006-07-12
I dont know if its exactly the same, but it will get you very close.

---

