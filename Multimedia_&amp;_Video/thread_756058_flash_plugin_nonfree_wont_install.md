---
title: "flash plugin nonfree wont install"
date: 2008-04-15
forum: Multimedia &amp; Video
---

### Post by adam_123 on 2008-04-15
ia m on Kubuntu 7.10 and 64 bit and i tried to install flash plugin non-free in my terminal it did the install process says download is done and then said the flash plugin is NOT INSTALLED. Can anyone help me please

---

### Post by robertchahine on 2008-04-15
is your flash plugin for mozilla firefox?

---

### Post by wolfen69 on 2008-04-15
try:
```
sudo apt-get install flashplugin-nonfree nspluginwrapper
```
ignore if it says not installed. just go to youtube to test it.

---

### Post by adam_123 on 2008-04-15
no that doesn't work either and yes i am using firefox

---

### Post by robertchahine on 2008-04-15
so you're using firefox then do this :

go to the adobe website and download the package of the flash player (.tar.gz)

[http://www.adobe.com/shockwave/downl...getflashplayer](http://www.adobe.com/shockwave/downl...getflashplayer)

right click on the pacakge->extract here.
open the folder and click alt+F2 browse the file in the folder of the flash player and mark "run in terminal"
so you install properly the falsh player for firefox.
then restart firefox.

---

### Post by adam_123 on 2008-04-15
i do that and it comes up with permission denied

---

### Post by Ulyssus on 2008-04-15
you can do it with the terminal:

- open the terminal and with the command "cd" you can switch in the folder, where you saved the file, e.g. cd /home/user/...
- with "sudo tar xfvz [ARCHIVE].tar.gz" you can extract the file (root-password is needed)
- switch with "cd" in the next folder, which appeared during extraction
- then just type in ".flashplayer-installer"

that should work

---

### Post by ajgreeny on 2008-04-15
One other way is to find where the file (or files) libflashplayer.so are on your system and simply replace them with the new version in the file you just downloaded.  On my system they are here:-

 locate libflashplayer.so
/usr/lib/flashplugin-nonfree/libflashplayer.so
/home/user/.mozilla/plugins/libflashplayer.so
/home/user/Downloads/install_flash_player_9_linux/libflashplayer.so

I know this way can work as I have done it twice now when new versions of flash come out without problems.  You will have to replace any files in /usr/lib as root of course, so do it with sudo in the terminal, or if you prefer use gksudo nautilus and do it with nautilus running as administrator, **BUT DO BE CAREFUL**, you can do a lot of damage if you remove the wrong files.

---

