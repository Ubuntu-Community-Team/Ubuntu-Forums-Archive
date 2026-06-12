---
title: "CinePaint 1.0.4 on Ubuntu 16.04"
date: 2017-05-04
forum: Multimedia Software
---

### Post by claus on 2017-05-04
Hi,

I want to install CinePaint 1.0.4 as a .deb file, which I found here ([https://debian.pkgs.org/8/multimedia-main-i386/cinepaint_1.0.4-dmo5_i386.deb.html](https://debian.pkgs.org/8/multimedia-main-i386/cinepaint_1.0.4-dmo5_i386.deb.html)).
I successfully installed the first three libraries, but I'm stuck with 'libcinepaint1'. The .deb file is being downloaded, but the Ubuntu Software Center doesn't
install it. The first three libraries were installed without a problem. What can I do to solve this problem? When I click on 'Install', I am briefly getting 'Is being
installed' (my interface is in German), but I'm not being prompted for the root password.

TIA,

Claus

---

### Post by howefield on 2017-05-04
If you don't mind using the terminal, try

```
sudo apt install ~/Downloads/cinepaint_1.0.4-dmo5_i386.deb
```

assuming that you have the deb package located in your ~/Downloads folder and that the name of the package is as above, if not amend to suit. If there is an error you are likely to get more of an idea what is wrong by using the terminal.

---

### Post by claus on 2017-05-04
I'm installing the libraries now using either gdebi or Synaptic, and this works.

---

