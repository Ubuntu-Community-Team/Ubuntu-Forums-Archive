---
title: "Sound prob -- dunno whats up"
date: 2005-12-03
forum: Multimedia &amp; Video
---

### Post by nppro on 2005-12-03
hey -- SOUND WAS WORKING previously -- but I installed some drivers via automatix and installed ET and now it doesnt work -- it says this when I type alsa mixer

root@ubuntu:/home/nppro# alsamixer
alsamixer: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory
root@ubuntu:/home/nppro#   

and now when I go to sound / multimedia there is no sound options, it just prints out what it says above... any ideas ?

---

### Post by arnieboy on 2005-12-03
[QUOTE=nppro]hey -- SOUND WAS WORKING previously -- but I installed some drivers via automatix and installed ET and now it doesnt work -- it says this when I type alsa mixer

root@ubuntu:/home/nppro# alsamixer
alsamixer: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory
root@ubuntu:/home/nppro#   

and now when I go to sound / multimedia there is no sound options, it just prints out what it says above... any ideas ?[/QUOTE]
please do the following from terminal:
```
cat $HOME/automatix.log
```
and paste the results here.

---

### Post by nppro on 2005-12-04
Multimedia codecs
Firefox Plugins|Archives|gftp|Ripper and Tuner|Media Players|AUD-DVD codecs
nppro@ubuntu:~$

---

### Post by nppro on 2005-12-04
it seems that alsa is installed on my computer -- however it is not in the autoload ..... what is the module name for it so  I can put it in the autoload?

---

### Post by arnieboy on 2005-12-04
do the following:
```
sudo apt-get install libasound2 libasound2-dev

```and reboot

---

