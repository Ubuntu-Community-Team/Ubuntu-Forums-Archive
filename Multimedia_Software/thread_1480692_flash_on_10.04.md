---
title: "flash on 10.04"
date: 2010-05-11
forum: Multimedia Software
---

### Post by travistey on 2010-05-11
so i upgraded to lucid lynx, and the flash player turned into a jerk. all pluggins are installed and up to date, and any flash item on a web page appears to load, but never actually loads. some sites inform me that "an error has occurred" whilst others will have a "click here to reload" button that never works. Any suggestions?

---

### Post by WinterRain on 2010-05-11
Try completely removing flash, then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
then reinstall flash. If that doesn't work, rename your .mozilla file to .mozilla_bak or something and restart firefox. It could be your config file borking up.

---

