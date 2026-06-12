---
title: "video hardware autodetect"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by Macrosoft on 2007-10-27
just upgraded to 7.10, and now it tries to detect the type of video hardware i have. i have already tried setting it manually to nvidia 6 series, but it ignores those settings and uses low-graphics mode (vesa drivers). how do i stop it from autodetecting? everything was working fine on feisty fawn.

---

### Post by overdrank on 2007-10-29
> **Macrosoft said:**
> just upgraded to 7.10, and now it tries to detect the type of video hardware i have. i have already tried setting it manually to nvidia 6 series, but it ignores those settings and uses low-graphics mode (vesa drivers). how do i stop it from autodetecting? everything was working fine on feisty fawn.

Hi and you can try and reconfigure you xorg with this command In the terminal located under applications, accessories, terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` 
Then you can make sue it is using the correct driver nvidia instead of nv in your xorg with this command ```
cat /etc/X11/xorg.conf
``` Good luck!

---

### Post by Macrosoft on 2007-11-22
ok, found the problem (finally). the API version of the kernel module and the API version for the driver didnt match. i uninstalled the existing driver and module and installed versions with matching API's. now have geforce 6200 with 3d acceleration working.

---

