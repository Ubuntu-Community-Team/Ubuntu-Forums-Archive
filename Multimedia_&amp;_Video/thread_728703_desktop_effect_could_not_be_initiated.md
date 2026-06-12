---
title: "desktop effect could not be initiated"
date: 2008-03-19
forum: Multimedia &amp; Video
---

### Post by prashantkumar on 2008-03-19
I am using ATI radeon x1300 graphics card.Desktop effect in ubuntu 7.10 can not be initiated. I checked the restricted driver section and installed ATI drivers. After that, when I am trying  to initiate the effects,It is saying"The complete extension is not available" please help......

---

### Post by jan quark on 2008-03-20
I guess you have to download the xserver-xgl package
```

sudo apt-get install xserver-xgl
```

and then change the session during the login to xclient

---

