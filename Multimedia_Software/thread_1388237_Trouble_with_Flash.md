---
title: "Trouble with Flash"
date: 2010-01-22
forum: Multimedia Software
---

### Post by jhare215 on 2010-01-22
I'm new to Ubuntu and I can handle most problems myself but I am stumped when it comes to this one. When i'm on a website that uses flash i.e. youtube I can't use the pause button or the slider. I have removed flash then reinstalled it to the latest version and I'm not sure what to do from here. Thanks -Josh Hare-

---

### Post by LuridCinema on 2010-01-22
This might help .....

Go to ( on the upper panel )  System>Administration>Synaptic Package manager
Then click on Settings>Repositories
Click n the Ubuntu Software tab
Make sure Proprietary drivers (Restricted) is checked
THEN type in FLASH in the Quick Search and check the following:
Adobe-Flash Plugin
Flash-Plugin Installer
Flash Plugin - NonFree
SWFdec-Mozilla

Click Apply and you should be good to go

---

### Post by jhare215 on 2010-01-22
ok i did that but i could not locate Adobe-Flash Plugin and I still am experiencing the same problem. I installed Flash Plugin - NonFree, SWFdec-Mozilla. The others were installed.

---

### Post by lovinglinux on 2010-01-23
If you are using 64bit, then remove all flash plugins and follow [this tutorial](http://ubuntuforums.org/showthread.php?t=1358591).

If you are using 32bit, remove all flash plugins and install only flashplugin-nonfree. See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004), for detailed instructions.

---

