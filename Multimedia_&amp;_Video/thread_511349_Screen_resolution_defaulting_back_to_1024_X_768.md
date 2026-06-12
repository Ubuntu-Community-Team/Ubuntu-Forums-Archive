---
title: "Screen resolution defaulting back to 1024 X 768"
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by iplom on 2007-07-27
Screen resolution defaulting back to 1024 X 768

Hello:

I have installed Automatix and the NVidia drivers from within Automatix.

My monitor is an Acer AL2017, the resolution should be 1400 X 1050.

I can set the resolution to  1400 X 1050 by going into the NVidia display properties and changing it to the desired resolution, this works well until I re-boot or shut down the PC. Once I turn on the computer and login to UBuntu (7.04) the resolution has been re-set to 1024 X 768!!

How can I get Ubuntu to remember the settings I want so that I do not have to manually change the screen size every time I start Ubuntu? I tried saving to xconfiguration file in the NVidia control panel , that does not work.

Thanks for your help

---

### Post by wolfen69 on 2007-07-27
in terminal:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by iplom on 2007-07-27
> **wolfen69 said:**
> in terminal:
```
sudo dpkg-reconfigure xserver-xorg
```

Yes, running through all the prompts then setting resolution  to 1400 X 1050 and saving solved this problem. Thanks!!

---

