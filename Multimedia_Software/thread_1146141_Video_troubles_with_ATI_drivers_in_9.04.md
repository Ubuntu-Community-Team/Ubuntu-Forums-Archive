---
title: "Video troubles with ATI drivers in 9.04"
date: 2009-05-02
forum: Multimedia Software
---

### Post by Rotbartig on 2009-05-02
Hello all!

Just installed Jaunty and faced next trouble.

lspci shows wrong name of my ATI graphic card:
```
root@bunker:/home/vladimir# lspci
01:00.0 VGA compatible controller: ATI Technologies Inc M71 [Mobility Radeon X2100] (rev ce)

```while I have ATI Mobile Radeon HD 2300 in my Fujitsu-Siemens Amilo PI 2530 Laptop.
Trying to install proprietary drivers failed with error "No supported card found". Using Ubuntu 9.04 x64 version.

Using default drivers results in screen artefacts during scrolling text and web sites. Not very good as you understand.

Has anyone faced such a problem and solved this?

---

### Post by berdux on 2009-05-02
i have exactly the same problem with my laptop (amilo pi 2530, x64 ubuntu 9.04)

---

### Post by Yellow Pasque on 2009-05-02
The problem is that the mobility 2300 "HD" isn't really based on the R600 architecture like other HD parts. It technically shouldn't be called a RadeonHD, but that's deceptive marketing for you...
It's actually an older, R500 era, 90nm chip, based on the Radeon X2100. AMD/ATI has dropped support for the older products in its latest Catalyst (9.4) drivers and these are the only proprietary drivers that will work with Jaunty (or any Linux distro using Xserver 1.6.x).

Your options:
- Troubleshooting the open-source drivers
- Go back to Ubuntu 8.10 or another distro that uses Xserver 1.5.x

---

### Post by nasrat on 2009-05-05
> **Temüjin said:**
> The problem is that the mobility 2300 "HD" isn't really based on the R600 architecture like other HD parts.

K Buddy I have a HD 2400 based on the r600, shows artifacts as well with "radeon" driver. "radeonhd" doesn't work. What should i do :confused:

---

### Post by Rotbartig on 2009-05-16
Well, decided to switch to openSuSE 11.1... Pity but 9.04 is kinda crappy at this time.

---

### Post by shabazzk on 2009-05-16
> **nasrat said:**
> K Buddy I have a HD 2400 based on the r600, shows artifacts as well with "radeon" driver. "radeonhd" doesn't work. What should i do :confused:

I have an ATi 2400 HD Pro, I downloaded the Proprietary drivers from ATi/AMD's site directly, and used this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually)

Works every time for me.

---

### Post by shabazzk on 2009-05-16
> **Rotbartig said:**
> Well, decided to switch to openSuSE 11.1... Pity but 9.04 is kinda crappy at this time.

Looks like there is no support for your card in the new 9,4 drivers.
See this link: [http://wiki.cchtml.com/index.php/9.4](http://wiki.cchtml.com/index.php/9.4)

---

### Post by Yellow Pasque on 2009-05-16
> **Rotbartig said:**
> Well, decided to switch to openSuSE 11.1... Pity but 9.04 is kinda crappy at this time.
Just don't upgrade to 11.2, or you'll have the same problem.

---

