---
title: "Winmodem..Help please."
date: 2006-01-28
forum: Networking &amp; Wireless
---

### Post by Jeckel on 2006-01-28
I have a lucent winmodem that has lucent/agree DSP and i've tried everything I could think of to get drivers for it..but it just won't work. (i'm on my winXP partition now.)

could you guys please help me? I've tried the wiki..i've tried getting drivers from the linmodem site...but they won't compile right..

---

### Post by ddtmsa on 2006-01-28
Not sure what you mean by 'won't compile right' but have you installed the following packages from the CD?

sudo apt-get install build-essential
sudo apt-get install linux-headers2.6.12-9-386  


You may also have to download some complier packages to compile the driver, I did this for my Intel modem, no idea if you need it for the Lucent modem ... but they won't do any harm 

[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.4-6ubuntu8_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.4-6ubuntu8_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.4-6ubuntu8_i386.deb)
 

and then copy over to your ubuntu files and install them

dpkg -i cpp-3.4_3.4.4-6ubuntu8_i386.deb gcc-3.4-base_3.4.4-6ubuntu8_i386.deb gcc-3.4_3.4.4-6ubuntu8_i386.deb
 

and then make an appropriate link for compiling:

ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc
 
Hope this is of help.

---

