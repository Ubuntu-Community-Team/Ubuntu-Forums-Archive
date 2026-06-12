---
title: "ISO mount how to?  help"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by PokieCarlwin_is_borked on 2008-01-06
hi,  

First I wanted to appologise for adding another thread that seems to be  covered in five previous threads, but they left me wondering what I was doing wrong :confused: 

I would like to 
mount "iso" in a terminal, but i get the response
mount: can't find /home/eek/Azureus Downloads/SASUKE_FALL_2007.ISO in /etc/fstab or /etc/mtab

why & what do "/etc/fstab or /etc/mtab" have to do w/ mounting an ISO?  I'm LOST :sad: please help.

---

### Post by taurus on 2008-01-06
Is there a SASUKE_FALL_2007.ISO in /home/eek/Azureus Downloads/SASUKE_FALL_2007.ISO?

```
ls -la /home/eek/"Azureus Downloads"
```
Remember, Unix/Linux is CaSe SenSiTive so capital letters are not the same as non-capital letters.

---

### Post by PokieCarlwin_is_borked on 2008-01-06
yes.

there is "SASUKE_FALL_2007.ISO" in ~/Azureus Downloads, but  there is NO dir "SASUKE_FALL_2007.ISO"

---

### Post by taurus on 2008-01-06
```
sudo mkdir /media/iso
sudo mount -t iso9660 /home/eek/"Azureus Downloads"/SASUKE_FALL_2007.ISO /media/iso -o loop
ls -la /media/iso
```

---

