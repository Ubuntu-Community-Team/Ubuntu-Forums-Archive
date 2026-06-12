---
title: "Ubuntu 10.04 RTL8192SU driver causing boot issues /freeze ups"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by RyuzakiTenseiga on 2010-07-10
So I have recently been making attempts at setting up my RTL8192SU chipset usb wifi . After struggling to set it up by following the steps on this link: [http://www.google.com/url?sa=t&source=web&cd=10&ved=0CEEQFjAJ&url=http%3A%2F%2Fsamiux.blogspot.com%2F2010%2F05%2Fhowto-realtek-8192su-usb-dongle.html&ei=T8Q4TM7MOYqisQPk_-RR&usg=AFQjCNGTj8NTxESTDWmqKw0jUyXQukrfIw](http://www.google.com/url?sa=t&source=web&cd=10&ved=0CEEQFjAJ&url=http%3A%2F%2Fsamiux.blogspot.com%2F2010%2F05%2Fhowto-realtek-8192su-usb-dongle.html&ei=T8Q4TM7MOYqisQPk_-RR&usg=AFQjCNGTj8NTxESTDWmqKw0jUyXQukrfIw)

After doing this I had no idea what it was supposed to look like but It did display several warnings along the lines of "*warning*: cast from pointer to *integer*  of *different* size"

not knowing what this means doesn't help . 

I continued following steps as another error occurred "cp  cannot stat autoconf.rtl8712_usb_linux.h" 
I then entered sudo modprobe 8712u and my screen went black i was forced shut down .
Upon rebooting I found it also would lock up if my usb device was plugged in 
It will boot with it unplugged but as soon as it is plugged in again it will lock up my system and send it to a black screen. 
I would really appreciate any assistance . 
If you need more info let me know and I will do my best to help

---

### Post by Allxsan on 2010-09-23
I think that you use 64bit os

this is my experience with 8192su


amd64 :

a) once compiled and loaded the Realtek driver ( downloaded from the realtek site ) the system freeze 
 ( the screen become black and keyboard leds  blinks )

b) can't connect using the staging kernel drivers 
( maybe some sensibility issue, but nothing change putting the wifi router near to the 8192su )

32bit :

a) once compiled and loaded the Realtek driver ( downloaded from the realtek site )the connection works fine&fast ( connection speed and speed ). Some issues with "netspeed" that can't detect the speed and with the reported signal strength ( goes up and down from 10% to 90% )

b) same as 64bit os

I've also tried using many kernels and linux os,  getting identical results ( gentoo, fedora, mandriva... )

---

### Post by Allxsan on 2010-09-24
hello

the problem was related to the firmware file, 

differents  .bin  that can be found in some archive  and/or on some site not always works

you need to download "rtl8192sfw.bin" from svn.debian.org 

can be done using this command 

"wget http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin"

and put it in folder 
"/lib/firmware/RTL8192SU"

( I've found other bigger rtl8192sfw.bin  also in some other folder of svn.debian site but doesn't  work )

---

