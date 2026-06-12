---
title: "Atheros Wireless on ASUS EEE PC T91MT"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by Cows on 2010-02-26
Thanks. I actually reinstalled Ubuntu and for some reason it doesn't shut down at boot anymore.. weird.

Either way I installed the modules just to be sure and it's working fine now. Thank you very much.

Now all I need to do is wait for the touchscreen drivers to come out. I heard ENAC or EMAC submitted some touchscreen support for the 2.6.33 kernel.

---

### Post by Cows on 2010-02-27
I have tried blacklisting a few things for today but I have failed. 

I also installed the linux-backports-modules-karmic and that didn't stop the wireless from disabling. I also notice that sometimes when I'm downloading something, the download would stop for a few seconds and then continue. Sometimes it stops for 10-20 seconds or more and then continues.

---

### Post by Cows on 2010-02-28
I have noticed that Ubuntu 9.04 , Eeebuntu, and Easy Peasy don't shut down my wireless but Network Manager starts up disabled. Which I'm assuming is an easy fix by installing wicd.

I guess it's something with the way the 9.10 kernel was compiled.

---

### Post by hislordship on 2010-02-28
I have an atheros myself. The blacklisting thing doesn't do the trick, installing these two packages does... here's a link to where I found the fix

[http://ubuntuforums.org/showpost.php?p=8599246&postcount=5](http://ubuntuforums.org/showpost.php?p=8599246&postcount=5)

---

### Post by hislordship on 2010-02-28
to be more specific: my post referred to Atheros AR928X

---

### Post by Cows on 2010-02-28
Thanks. I actually reinstalled Ubuntu and for some reason it doesn't shut down at boot anymore.. weird.

Either way I installed the modules just to be sure and it's working fine now. Thank you very much.

Now all I need to do is wait for the touchscreen drivers to come out. I heard ENAC or EMAC submitted some touchscreen support for the 2.6.33 kernel.

---

