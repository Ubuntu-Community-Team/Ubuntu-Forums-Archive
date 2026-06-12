---
title: "fglrx drivers broke my kdetv"
date: 2006-06-19
forum: Multimedia &amp; Video
---

### Post by fluid_motion on 2006-06-19
After successfully updating the ATI drivers found at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI), I realised my kdetv kept giving me the V4L2 plugin error. I can hear sound but there is no video feed. Now I am contemplating whether to to reinstall everything and forego the fglrx driver. 

Anybody faced similar problem? Is there a solution to this? I really hate it when I break something after I upgrade something. :(

---

### Post by x64Jimbo on 2006-06-19
You shouldn't need to do a full reinstall. Any time you install the drivers, it should be making a backup of your xorg.conf file. Since you can't get into the GUI, you should hit Ctrl+Alt+F4 to get into the terminal w/o a GUI. Login, then have a look in your /etc/X11 directory and see if there's a file that looks like an xorg.conf backup file. If there is, delete your xorg.conf and rename the backup file to xorg.conf. Hopefully that will get you back in working order.

---

