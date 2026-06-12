---
title: "ATI Radeon Xpress 200M &amp; Restricted Drivers"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by peter07 on 2007-04-25
After update to feisty, installing restricted drivers should be easy. But Restricted Divers Manager didn't show available drivers for my graphic card ATI Radeon Xpress 200M. :(  So I installed it again manually. Now I have this driver listed in manager, but I still have problems with beryl. So, I have two question:

1) Which version of Ati drivers Restricted Divers Manager installed for Radeon Xpress 200M?
2) Anybody else have the same problem? No driver for this card detected?

---

### Post by divague on 2007-05-03
I have that card and i installed the driver the restricted driver manager. It installed the 8.34.8 driver

---

### Post by kangol69 on 2007-05-04
1. I also have that card. It installed the 8.34.8 driver.
2. Did you install the beryl that is on the Ubuntu repos or from the beryl ones?

---

### Post by divague on 2007-05-04
> 2. Did you install the beryl that is on the Ubuntu repos or from the beryl ones?

You have to install beryl from the beryl repo, because the one in ubuntu repo has something wrong with xgl (i'm not sure tho but there was a problem).

---

### Post by kangol69 on 2007-05-04
Yeah, divague is right. I tried it with the Ubuntu one and it wouldn't work at all.

---

### Post by peter07 on 2007-05-09
Divague, have you updated form 6.10 or this is a fresh installation? Have you installed other drivers first?

In my situation :
```

fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6458 (8.36.5)

```
Maybe this is a problem:confused: 
> You have to install beryl from the beryl repo, because the one in ubuntu repo has something wrong with xgl (i'm not sure tho but there was a problem).
I tried packages from beryl repo (except xgl server), no results.

---

### Post by peter07 on 2007-06-21
Is there any possibility to force Restricted Drivers Manager to detect my card and install the driver??

---

### Post by Tenchi on 2007-06-22
I had the same issue to where restricted driver did not detect any drivers.

Here is how it happened:
I also installed ATI drivers manually and automatically using various how to and automated installation.
But every time I checked my flgrx info I saw mesa3d drivers.

Here is how I solved it:
I went and checked in my x11 folder and there was many (21) versions of xorg.conf files
So I went on a lim and deleted all of them except one and reconfigured my drivers manually.
And checked the restricted drivers once more and the ATI drivers were detected.

Hope this helps you as it did me :D

---

### Post by peter07 on 2007-06-27
> **Tenchi said:**
> I had the same issue to where restricted driver did not detect any drivers.

Here is how it happened:
I also installed ATI drivers manually and automatically using various how to and automated installation.
But every time I checked my flgrx info I saw mesa3d drivers.

Here is how I solved it:
I went and checked in my x11 folder and there was many (21) versions of xorg.conf files
So I went on a lim and deleted all of them except one and reconfigured my drivers manually.
And checked the restricted drivers once more and the ATI drivers were detected.

Hope this helps you as it did me :D

Ok, I've just tried you're method. What I did: deleted all of  xorg.conf except the oldest one (default)  - no result :(

What does it mean:  "reconfigured my drivers manually" ??

---

### Post by Tenchi on 2007-07-01
So delete all the Xorg.conf files except 1
Then reinstall the ATI drivers using the how to.

Hope this helps

---

