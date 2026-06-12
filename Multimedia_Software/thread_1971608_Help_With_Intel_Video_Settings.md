---
title: "Help With Intel Video Settings"
date: 2012-05-02
forum: Multimedia Software
---

### Post by ekim91 on 2012-05-02
Hello, I recently Installed Lubuntu onto a Dell Dimension 4600C. I am running an Envision 22" widescreen (1680x1050:60-native resolution), but it installed and selected 1024x768:60 as the default resolution. I checked in proprietary drivers and nothing. I was wondering if I'm stuck to running this resolution due to the graphics card? Any help is appreciated as the pixelation is growing tiresome on me.

Thanks.

```
ganymede@valhalla:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
```

---

### Post by wolfen69 on 2012-05-02
See [this]("http://askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there") page to create a xorg.conf file and manually input the resolution needed.

---

### Post by ekim91 on 2012-05-05
Thanks.

---

