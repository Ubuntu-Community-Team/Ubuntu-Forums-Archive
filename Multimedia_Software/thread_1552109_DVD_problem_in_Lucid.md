---
title: "DVD problem in Lucid"
date: 2010-08-13
forum: Multimedia Software
---

### Post by mainak_sen on 2010-08-13
I have recently installed Lucid on an Acer Aspire 5570Z laptop. It has an Optiarc DVD RW AD-7530A DVD-RAM writer. I am having trouble in playing video/movies on DVD.

When I am inserting a movie DVD, the drive is working (i.e. is busy) continuously but the disc is not being recognized and mounted. Disc Utility is showing "No Media Detected".
The same DVD discs are playing OK in my desktop (running Hardy) and on another laptop (running Lucid).

Please note, however, that Audio and data CDs are playing/reading OK in the same drive. Even blank DVDs are being recognized and mounted OK.

I shall greatly appreciate if someone can help. Thanks in advance!

===========

*-cdrom
description: DVD-RAM writer
product: DVD RW AD-7530A
vendor: Optiarc
physical id: 1
bus info: scsi@1:0.0.0
logical name: /dev/cdrom
logical name: /dev/cdrw
logical name: /dev/dvd
logical name: /dev/dvdrw
logical name: /dev/scd0
logical name: /dev/sr0
version: EX31
capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
configuration: ansiversion=5 status=busy

---

### Post by mainak_sen on 2010-08-14
can anybody please help me with this?

---

### Post by Elzigzag on 2010-08-23
> **mainak_sen said:**
> can anybody please help me with this?

Me toooo. I'm facing a similar problem... insert a DVD-R, gets mounted, but Ubuntu recognises it as a blank DVD. I just can't play movies then :(

---

### Post by Tracy177 on 2010-08-30
if you still have a problem with your optiarc thats your solution 


When i installed first time ubuntu lucid i had 2.6.32 kernel with it the  thing is that every time i booted up ubuntu udev pulled nonstop!!!!  Optiarc DVD so i had everytime i booted up to restart udev cuz it used  30 to 50% of the cpu but i found solution.

i upgraded kernel from 2.6.32 to 2.6.35.19 and dont have any more any  problems with udev and high cpu usage and thats how i did it.

first at all in synaptic u wont find 2.6.35 unless u do :

[LEFT][B]sudo add-apt-repository ppa:kernel-ppa/ppa 

&& sudo apt-get update[/B]

after that open synaptic type linux and install latest kernel linux image and linux headers or just do 
[/LEFT]
[B]
sudo  apt-get install linux-headers-2.6.35-19 linux-headers-2.6.35-19-generic

and than

sudo update-grub2 

and if u have burg installed 

sudo update-burg 

dont remove yet your old kernel restart ubuntu boot up in 2.6.35.19 and see udev doesnt pull optiarc no more.

and one more thing to people who got ati graphic card after every kernel  upgrade u need to reinstall catalyst it maybe that when u boot up in  2.6.35 it will boot up in low graphic mode if so reinstall your graphic  card. the latest catalyst for ati card is ver 10.8 get it from here 
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

if u see everything is ok remove old kernel and again sudo update-grub2 , sudo update-burg

thats all[/B]

---

