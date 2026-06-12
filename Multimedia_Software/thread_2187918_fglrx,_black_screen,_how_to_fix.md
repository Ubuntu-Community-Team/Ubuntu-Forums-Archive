---
title: "fglrx, black screen, how to fix?"
date: 2013-11-14
forum: Multimedia Software
---

### Post by yCAxYRA on 2013-11-14
I installed fglrx-installer-13 and played around a bit with two displays, then suddenly laptop display went black and stayed black although i tryed to change settings on other display. When i rebooted, problem remained but then i realised that actually laptop display WAS working but backlight was off. When intense light at certain angle illuminates display you can see barely that actually display is working. I think there is a bug with that new fglrx energysaving backlight setting. When i reverted to opensource driver display works... Now i am trying to reset fglrx settings.

---

### Post by QIII on 2013-11-14
Moved to a new thread.

---

### Post by yCAxYRA on 2013-11-14
Tryed:
sudo aticonfig --adapter=all --initial and some other recommendations but nothing works. Any ideas how to manually delete 
all fglrx settings? There must be settings somewhere else than xorg.conf .

---

### Post by yCAxYRA on 2013-11-15
Looks like i am not only one - [http://ati.cchtml.com/show_bug.cgi?id=939](http://ati.cchtml.com/show_bug.cgi?id=939). /etc/ati/amdpcsdb supposedly contains amdcccle settings but i didnt even have that file. And yet removeing driver doesnt help and settings remain... Looks like i have to stick with opensource driver. :(

---

### Post by nisko666 on 2013-12-01
I have the same problem on Asus k52ju with 6370m with the last beta driver. Here I take a photo [https://www.dropbox.com/s/gpaeuupt7w215r0/IMG_20131201_175125.jpg](https://www.dropbox.com/s/gpaeuupt7w215r0/IMG_20131201_175125.jpg)

---

### Post by yCAxYRA on 2013-12-22
I just found out that this bug isnt linux exclusive, latest driver for windows has same issue, had to use old drivers that came with laptop.

---

