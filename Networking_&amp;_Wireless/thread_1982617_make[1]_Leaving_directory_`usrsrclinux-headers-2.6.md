---
title: "make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'"
date: 2012-05-18
forum: Networking &amp; Wireless
---

### Post by xGenius on 2012-05-18
hi all Aircrack user plzzz i'm trying to install my wireless card but i tried to do like in this tutorial [http://ubuntuforums.org/showthread.php?p=10107880](http://ubuntuforums.org/showthread.php?p=10107880) but i get errors while compiling make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
knownig that my kernel is 2.6.35-22
my wireless card : BCM4313 [14e4:4727]

i've googled it but i didn't find any solution  [IMG]http://forum.aircrack-ng.org/Smileys/default/undecided.gif[/IMG] and i know how to use patch and aircrack ...
plsss heeelp

---

### Post by chili555 on 2012-05-18
It doesn't look like an error to me. Does it say ERROR? Are there any errors when you do:```
sudo make install
```> knownig that my kernel is 2.6.35-22Is it?```
uname -r
```

---

### Post by xGenius on 2012-05-18
it always show me the same error if we can call it error ===>  
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
:/

---

### Post by chili555 on 2012-05-19
All I can say is what I already said: It doesn't look like an error to me. Does it say ERROR? What you quoted is not an error. Can you try again:```
sudo su
make clean
make
make install
exit
```Post the result or post it here and give me the link: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

What you quoted is *not* an error.

---

### Post by xGenius on 2012-05-22
Seems that i evoluated from the lasttime  i installed the last ubuntu 12.04 and i the wireless is working fine but when i'm trying to inject i get fixed channel mon0: -1 so i tried to fix it using this tutorial [http://hi.baidu.com/9linux/blog/item/113309178f220729c93d6d97.html](http://hi.baidu.com/9linux/blog/item/113309178f220729c93d6d97.html) ( i used compat-wireless-3.4-rc3-1 in the case of compat-wireless-2012-04-26)  but i can't compile, when typing make at the end i get 

make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic-pae'

@ASPj I have already istalled kernel-sources 
sudo apt-get install linux-headers-3.2.0-23-generic-pae
linux-headers-3.2.0-23-generic-pae is already the newest version.

uname -a
Linux xgeniu-PC 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686 i686 i386 GNU/Linux
@chili555 i always can't campile :/

---

### Post by xGenius on 2012-05-22
This is the result

---

### Post by chili555 on 2012-05-22
> but i can't compile, when typing make at the end i get

make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic-pae'You *DID* compile and it's *not* an error. Did you follow up with:```
sudo make install
```Can you load the wireless driver you want?```
sudo modprobe whatever
```

---

