---
title: "ATI HD 2400 Pro not working with fglrx"
date: 2009-10-12
forum: Multimedia Software
---

### Post by sparky_odom_2005 on 2009-10-12
lspci output
```
03:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]

```
When I go to Hardware Drivers it shows fglrx driver. If I activate it, upon restart, I get tty1 rapidly flickering. Login screen never shows up. If I go into recover mode and run aticonfig --initial I get
```

Unable to open /etc/ati/control
aticonfig: No supported adapters detected

```
Removing fglrx and deleting xorg.conf fixes it but it is using the open source driver.

I checked and it looks like my adapter is supposed to be supported. Is there something I am doing wrong?

---

### Post by @ntonius on 2009-10-17
I have the exact same card.
The latest ati (fglrx) drivers work perfectly for me which you can find at the official ati-amd site.
Follow the instructions here [http://wiki.cchtml.com/](http://wiki.cchtml.com/)
and dont forget to remove the open source drivers "ati" and "radeon" from synaptic (which are pre installed by default).

---

