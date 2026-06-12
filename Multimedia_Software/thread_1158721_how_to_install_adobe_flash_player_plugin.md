---
title: "how to install adobe flash player plugin"
date: 2009-05-13
forum: Multimedia Software
---

### Post by camino3701 on 2009-05-13
I need adobe flash player plugin to play my games. I was able to download it ok but when I go to install it the "Package Installer" window says "Error: Dependency is not satisfiable: libcurl3" can any one help me on installing the plugin?

Thank You,
RLB

---

### Post by oldos2er on 2009-05-14
Which version of Ubuntu are you using?

   Open a terminal and run
```
sudo apt-get update && sudo apt-get install flashplugin-nonfree
```
 If any errors come up, please copy and paste them here.

---

### Post by gandaran on 2009-05-14
> **camino3701 said:**
> I need adobe flash player plugin to play my games. I was able to download it ok but when I go to install it the "Package Installer" window says "Error: Dependency is not satisfiable: libcurl3" can any one help me on installing the plugin?

Thank You,
RLB
run **sudo apt-get update** before installing the package.

---

### Post by camino3701 on 2009-05-15
Thank you both after I installed sudo-apt update it installed fine.

Thanks again,
RLB

---

