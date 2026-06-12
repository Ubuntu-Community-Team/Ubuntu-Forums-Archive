---
title: "Can Nvidia 9800GTX be drived and CompizFusion enabled successfully?"
date: 2008-04-21
forum: Multimedia &amp; Video
---

### Post by lemonicetea on 2008-04-21
Thank you all for your reply.

---

### Post by lemonicetea on 2008-04-22
Does anybody know that?

---

### Post by revpfil on 2008-04-22
Yes. Currently you need the proprietary beta drivers for full functionality. These can be found at [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) and support the nVidia 9 series cards. To install the driver, you must stop the xserver, then run the install script as root. When it asks to use the nvidia xorg.conf configuration tool, decline. After installation, open your xorg.conf by hand and change the driver from "nv" to "nvidia". After this, restart the xserever, and you should see the nVidia beta splash screen.

---

### Post by Amshu on 2008-04-23
Been having quite a nightmare of a time getting it to work myself.:mad:

---

### Post by lemonicetea on 2008-05-14
> **Amshu said:**
> Been having quite a nightmare of a time getting it to work myself.:mad:


Could you please post your method? Thank you so much!

---

