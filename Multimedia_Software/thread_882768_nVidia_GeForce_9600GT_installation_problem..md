---
title: "nVidia GeForce 9600GT installation problem."
date: 2008-08-07
forum: Multimedia Software
---

### Post by Jojan on 2008-08-07
First of all; I've searched the Internet and I've search this forum for help, but nothing has helped.

I've built me a new computer and have the nVidia GeForce 9600GT graphics grad, but I can't seem to get Ubuntu to use it as I think it should.

I've tried [FONT="Courier New"]envyng[/FONT] and I've tried the nVidia driver from their website. I've looked at the last ten pages of [Post the way you got the nVidia driver to work]("http://ubuntuforums.org/showthread.php?t=221313") but haven't got it to work either.

When I tried installing the driver from nVidia I come into low graphics mode after reboot. I don't know how to configure xorg.conf file to make everything to work.

Could someone give me a n00b step guide of how to make this work.

```
$ lspci -n | grep 0300
01:00.0 0300: 10de:0622 (rev a1)
```
```
$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation Geforce 9600 GT 512mb (rev a1)
```
```
$ lspci -n | grep 0300
01:00.0 0300: 10de:0622 (rev a1)
```

---

### Post by blazercist on 2008-08-07
1. download the driver from the website to your home folder.
2. In terminal 
```
sudo apt-get install build-essential
sudo chmod +x NV*
```
3. WRITE THE REST OF THESE INSTRCUTIONS DOWN YOU CANNOT INSTALL FROM GUI.
4. ctrl+alt+f1 (WARNING: this will drop you to virtual terminal NO GUI)
5. ```
sudo /etc/init.d/gdm stop
sudo sh NV*
```
6. ACCEPT YES ACCEPT YES YES YES ACCEPT
7. ```
sudo /etc/init.d/gdm start
```

---

### Post by TakisX on 2008-08-07
The above work for my 9600gt at 8.04 but not at 8.10

---

### Post by Jojan on 2008-08-07
I got the same massive faildown that I got when I followed other instuctions. It said that it did not find my graphic card driver and not my screen. So no I am in low graphics mode.

But worse than that, I only have a part of my desktop. I have what should be the upper half on the bottomhalf. And everything is pushed so it comes out on the other side. On the top half of my screen (what I see) it is just some colored lines. I will now reboot and make the screen useable with help of recovery mode.

---

