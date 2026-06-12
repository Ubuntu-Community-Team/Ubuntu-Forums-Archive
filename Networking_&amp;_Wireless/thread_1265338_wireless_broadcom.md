---
title: "wireless broadcom"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by Abu Noor-Eddin on 2009-09-13
Hello all again,

After a huge success to my previous thread [http://ubuntuforums.org/showthread.php?t=1263996](http://ubuntuforums.org/showthread.php?t=1263996) I decided to do a fresh installation of Ubuntu 8.04. 

Everything went fine through the installation, and again (as expected) my wireless does not work. I did not touch anything (i.e. enable/disable add/remove) as I did in the previous time hoping that someone will guide me a step by step before I ruin it again.

p.s. it is difficult to connect to internet in wire (have to go a long distance).

p.s. (2) when I shutdown my notebook. it was writing on screen that I have to get the firmware or something.

Waiting for responses.

---

### Post by t0mppa on 2009-09-13
The firmware hint would lead towards b43, which needs firmware to be installed to work properly, but since the firmware isn't open source, it's not installed by default. [Here]("http://linuxwireless.org/en/users/Drivers/b43") are steps to take to install said firmware.

The other option is to install the STA, like people said in the earlier thread. Bottom line is that both options need you to download things and if you can't get to a wired network to get connected to Internet, then you'll have to do the downloads on another computer and move the files to your Ubuntu one via portable media.

Just check with **lshw -C network** first which driver is getting associated with the interface, so you know if you need to do some blacklisting to get whichever one you pick to work.

---

### Post by Abu Noor-Eddin on 2009-09-13
> **t0mppa said:**
> The firmware hint would lead towards b43, which needs firmware to be installed to work properly, but since the firmware isn't open source, it's not installed by default. [Here]("http://linuxwireless.org/en/users/Drivers/b43") are steps to take to install said firmware.

The other option is to install the STA, like people said in the earlier thread. Bottom line is that both options need you to download things and if you can't get to a wired network to get connected to Internet, then you'll have to do the downloads on another computer and move the files to your Ubuntu one via portable media.

either option is okay for me as long as I will be connected to wireless. it is okay, I will go for the wire connection but I need a step by step guide as I do not know much about commands and linux stuff.

Thanks for replying.

---

### Post by t0mppa on 2009-09-13
The link I posted gives a pretty thorough guide on how to install the firmware. If you start building things manually (was the only solution which worked for me), Jaunty uses 2.6.28 kernel, so you'll need to follow the instructions for version 4.150.20.5 firmware.

The STA on the other hand should be as simple as going to System / Administration / Hardware Drivers and enabling it from there (won't work unless you're connected to Internet though), but since it doesn't support my card, I'm not sure what to do if that doesn't work.

---

### Post by Abu Noor-Eddin on 2009-09-13
> **t0mppa said:**
> The link I posted gives a pretty thorough guide on how to install the firmware. If you start building things manually (was the only solution which worked for me), Jaunty uses 2.6.28 kernel, so you'll need to follow the instructions for version 4.150.20.5 firmware.

The STA on the other hand should be as simple as going to System / Administration / Hardware Drivers and enabling it from there (won't work unless you're connected to Internet though), but since it doesn't support my card, I'm not sure what to do if that doesn't work.

I will try the second option first, if it does not work, I will try your first option. I will give my feedback. 

Thanks.

---

### Post by Abu Noor-Eddin on 2009-09-13
I did not find STA, so I moved to the second option. While executing the following commands 

```

wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-012.tar.bz2
tar xjf b43-fwcutter-012.tar.bz2
cd b43-fwcutter-012
make
cd ..

``` 

I got this message after MAKE command

```
fwcutter.c:556: warning: assignment from incompatible pointer type
fwcutter.c:564: warning: implicit declaration of function ‘strcmp’
fwcutter.c:569: warning: incompatible implicit declaration of built-in function ‘printf’
fwcutter.c: In function ‘parse_args’:
fwcutter.c:606: warning: passing argument 5 of ‘cmp_arg’ from incompatible pointer type
fwcutter.c:613: warning: passing argument 5 of ‘cmp_arg’ from incompatible pointer type
fwcutter.c:620: warning: passing argument 5 of ‘cmp_arg’ from incompatible pointer type
fwcutter.c:626: warning: passing argument 5 of ‘cmp_arg’ from incompatible pointer type
fwcutter.c:633: warning: passing argument 4 of ‘cmp_arg’ from incompatible pointer type
fwcutter.c:633: warning: passing argument 5 of ‘cmp_arg’ from incompatible pointer type
fwcutter.c: In function ‘main’:
fwcutter.c:663: error: ‘FILE’ undeclared (first use in this function)
fwcutter.c:663: error: ‘fd’ undeclared (first use in this function)
fwcutter.c:663: error: invalid operands to binary *
fwcutter.c:663: warning: statement with no effect
fwcutter.c:681: warning: statement with no effect
fwcutter.c:683: warning: incompatible implicit declaration of built-in function ‘fprintf’
fwcutter.c:683: error: ‘stderr’ undeclared (first use in this function)
fwcutter.c:688: warning: implicit declaration of function ‘find_file’
fwcutter.c:688: warning: assignment makes pointer from integer without a cast
fwcutter.c:692: error: ‘const struct file’ has no member named ‘flags’
fwcutter.c:692: error: invalid operands to binary &
fwcutter.c:699: warning: incompatible implicit declaration of built-in function ‘printf’
fwcutter.c:702: warning: implicit declaration of function ‘extract_or_identify’
fwcutter.c:702: error: ‘const struct file’ has no member named ‘flags’
make: *** [fwcutter.o] Error 1

```

So what should I do now?

---

### Post by Ayuthia on 2009-09-13
Have you ran the updates in Ubuntu yet?  That might be why you cannot find the Broadcom STA module.  I am not for sure which 8.04 version you have though.  I think that there is now 8.04, 8.04.1, 8.04.2, and 8.04.3.  If you have the original, the Broadcom STA module does not exist because it was only introduced to the Broadcom 4312 rev 01 (14e4:4315) also known as the 4310 model.  Other models were added a while later.

As for the b43-fwcutter option, you will be better to install it from the repository instead of getting it from their site.  It can either be found on the liveCD or if you have a working internet connection you can get it by doing:
```
sudo apt-get update
sudo apt-get install b43-fwcutter
```

---

### Post by Abu Noor-Eddin on 2009-09-13
UPDATE

After pain, my wireless is working now (I see all wireless network around me and the wireless LED is on when I enable it and off when I disable it). 

BUT, when I try to connect to my network, it keeps asking for the passphrase. I am sure it is correct but it is still asking for it. 

Any ideas? Please.

Thanks.

---

