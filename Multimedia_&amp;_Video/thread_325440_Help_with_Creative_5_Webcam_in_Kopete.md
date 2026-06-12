---
title: "Help with Creative 5 Webcam in Kopete"
date: 2006-12-25
forum: Multimedia &amp; Video
---

### Post by jolene on 2006-12-25
I have a Creative 5 Webcam, lsusb finds me: 

Bus 002 Device 003: ID 041e:400c Creative Technology, Ltd WebCam 5 [pwc]

It is visible in Device Manager and works in XawTV, but Settings > Configure > Device in Kopete shows me a green background with a black QT logo, with my webcam configuration in the boxes below. This seems to be quite a common problem, but I cannot find any kind of solution to it in any of the online literature...

I know it needs a PWC driver, so I go to [http://www.saillard.org/linux/pwc/](http://www.saillard.org/linux/pwc/) to install the latest release...

THE POINT IS - I need someone to explain this to me: [http://www.saillard.org/linux/pwc/INSTALL.en](http://www.saillard.org/linux/pwc/INSTALL.en)

(Scares the hell out of me.)

I am very grateful!

---

### Post by foolsh on 2006-12-26
that text pretty much says
```
sudo apt-get install build-essential linux-headers-`uname -r`
wget http://www.saillard.org/linux/pwc/files/pwc-10.0.9-rc1.tar.bz2
tar xjf pwc-10.0.12-rc1.tar.bz2
cd pwc-10.0.12rc1
make
sudo make install

```
here i would reboot
then
```
modprobe pwc
```
and see if it works

---

### Post by jolene on 2006-12-26
I get this message when I try to make:

```

jo@humbug:~/Desktop/pwc-10.0.12-rc1$ make
make -C /lib/modules/2.6.15-27-386/build SUBDIRS=/home/jo/Desktop/pwc-10.0.12-rc1 modules
make[1]: Entering directory `/lib/modules/2.6.15-27-386/build'
make[1]: *** No rule to make target `modules'. Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-27-386/build'
make: *** [all] Error 2
```

Foolsh, darling, what does this mean??

---

### Post by foolsh on 2006-12-26
./configure     <----------------------------put this command before make
make
sudo make install

---

### Post by jolene on 2006-12-26
```
jo@humbug:~/Desktop/pwc-10.0.12-rc1$ ./configure make
bash: ./configure: No such file or directory
```?

---

### Post by foolsh on 2006-12-26
I'll stop being lazy and download the source and take more of a look see

---

### Post by foolsh on 2006-12-26
are you sure you
sudo apt-get install build-essential linux-headers-`uname -r`
they compiled on my machine
What version of ubuntu do you use?

---

### Post by foolsh on 2006-12-26
silly me sees you're use dapper drake

try 
>  make CC=gcc-4.0

---

### Post by jolene on 2006-12-26
I use Dapper 6.06. I did everything just like you said (with the latest release of PWC - pwc-10.0.12-rc1 - that was the only difference). It took about 5 minutes or so to get the headers and there did not seem to be any error. 

I am a bit lost...

---

### Post by jolene on 2006-12-26
And same error as before! (make[1]: *** No rule to make target `modules'. Stop, et cetera...)

---

### Post by foolsh on 2006-12-26
I am stumbed too
Im using egdy 6.10 so I can't reproduce exactly what you see.

have you thought of upgrading to edgy 6.10 because it did compile on here btw i edited my previous post to reflect the 12 after i tried my own commands and they didn't work shame on me o_0

 and feisty fawn will be out early `07
every six months give or take and the whole learning process starts over again.

---

### Post by jolene on 2006-12-26
I was afraid you might say that! I think I will upgrade to Feisty next year, and in the meantime thank you for your help, you are a diamond. :mrgreen:

---

### Post by foolsh on 2006-12-26
No problem at all jolene ,happy new year

---

### Post by jolene on 2006-12-26
To yourself as well! :KS

---

### Post by OffHand on 2006-12-26
Follow my guide: [http://www.ubuntuforums.org/showthread.php?t=282748](http://www.ubuntuforums.org/showthread.php?t=282748)

That should be easy enough to follow.

---

### Post by louie1961 on 2006-12-31
Offhand,

First, let me thank you.  I followed your guide, and it worked flawlessly.  

Second, as someone who is usually a mepis fan boy, I just want to say how great my ubuntu experience has been so far.

:)

---

