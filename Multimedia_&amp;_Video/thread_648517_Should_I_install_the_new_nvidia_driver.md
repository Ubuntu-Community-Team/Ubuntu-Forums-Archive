---
title: "Should I install the new nvidia driver?"
date: 2007-12-23
forum: Multimedia &amp; Video
---

### Post by chacham23 on 2007-12-23
I have 6600 gt geforce working with gusty gibon.

do u advise me to install the new driver from the nvidia site or to stay with the one that comes with gusty? the card works well but I cant use more then 57 refresh rate, and I have greet screen(viewsonic 19" p90f)

thanks :)

---

### Post by Bliepo32 on 2007-12-23
My advice would be to make a back-up first (read [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)), and the try to install the drivers. If it fails, you will always have the back-up.

---

### Post by jrusso2 on 2007-12-23
My Policy is that if its not broke don't fix it.

Also when upgrades come through it might cause issues like kernel updates

---

### Post by chacham23 on 2007-12-23
> **Bliepo32 said:**
> My advice would be to make a back-up first (read [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)), and the try to install the drivers. If it fails, you will always have the back-up.

Good advise I think I would do that..

---

### Post by logos34 on 2007-12-23
> **chacham23 said:**
>  the card works well but I cant use more then 57 refresh rate, and I have greet screen(viewsonic 19" p90f)

Did you use system>prefs>screen resolution to try and adjust the rate or sudo nvidia-settings?

---

### Post by chacham23 on 2007-12-23
> **logos34 said:**
> Did you use system>prefs>screen resolution to try and adjust the rate or sudo nvidia-settings?

the first one..

---

### Post by logos34 on 2007-12-23
in a terminal type

sudo nvidia-settings

change the settings there and save to x config file.

(there should also be a nvidia launcher in Applications>sys tools or system>admin

---

### Post by chacham23 on 2007-12-23
> **logos34 said:**
> in a terminal type

sudo nvidia-settings

change the settings there and save to x config file.

(there should also be a nvidia launcher in Applications>sys tools or system>admin

thanks I would try it as well..

---

