---
title: "cinelerra wont work if ati card is enabled"
date: 2008-03-01
forum: Multimedia Production
---

### Post by templa edhel on 2008-03-01
i installed cinelerra following a guide somewhere and got the problem that when i tried to open it it got c```
cinelerra: symbol lookup error: /usr/lib/libguicast.so.1: undefined symbol: glDeleteShader

```
so after some trial and error i found that when i turned off my ati accelerated graphics via the restricted drivers manager it works just fine. but i really want to be able to use my graphics card(ok fine accelerated graphics) without having to reboot. any ideas?

---

### Post by templa edhel on 2008-03-02
yay all i had to do is download it from the cinelerra site but make sure i downloaded the type without opengl drivers

---

### Post by crush304 on 2008-03-02
have you tried w/ the latest drivers from ati, a lot of progress has been made since gutsy was released

[http://ati.amd.com/support/drivers/linux/linux-radeon.html]("http://ati.amd.com/support/drivers/linux/linux-radeon.html")

---

### Post by templa edhel on 2008-03-02
thanks il check that out too

---

