---
title: "no fglrx driver version for my card, when upgrading to 8.10"
date: 2009-01-01
forum: Multimedia Software
---

### Post by jannuk on 2009-01-01
got the following when i try to upgrade from 8.04:

"This computer is currently using the AMD 'fglrx' graphics driver. No version of this driver is available that works with your hardware in Ubuntu 8.10"

when I checked for ATI drivers on their webpage, I found this:
"ATI Catalyst™ 8.12 Proprietary Linux x86 Display Driver"

dare I go ahead and upgrade and then install the new Catalyst package or what should I do? :confused:

Cheers
JannuK

---

### Post by zika on 2009-01-01
> **jannuk said:**
> got the following when i try to upgrade from 8.04:

"This computer is currently using the AMD 'fglrx' graphics driver. No version of this driver is available that works with your hardware in Ubuntu 8.10"

when I checked for ATI drivers on their webpage, I found this:
"ATI Catalyst™ 8.12 Proprietary Linux x86 Display Driver"

dare I go ahead and upgrade and then install the new Catalyst package or what should I do? :confused:

Cheers
JannuK

i did that with my radeon HD 3650 and did not regret (several times already since there were new versions). mileage may vary. I'm not sure what will happen when Jaunty comes ...

---

### Post by jannuk on 2009-01-01
> **zika said:**
> i did that with my radeon HD 3650 and did not regret (several times already since there were new versions). mileage may vary. I'm not sure what will happen when Jaunty comes ...


zika, thanks for quick reply, will give it a try then.

which installation method did you use?
-Restricted Drivers Manager in 8.10
-Manual

/JannuK

---

### Post by zika on 2009-01-01
> **jannuk said:**
> zika, thanks for quick reply, will give it a try then.

which installation method did you use?
-Restricted Drivers Manager in 8.10
-Manual

/JannuK

go to ati.amd.com and get drivers and follow their procedure ... I have it written somewhere ... I think it's [http://ubuntuforums.org/showpost.php?p=6317627&postcount=7](http://ubuntuforums.org/showpost.php?p=6317627&postcount=7) ... I'll be on-line if You need any help.

---

### Post by jannuk on 2009-01-02
> **zika said:**
> go to ati.amd.com and get drivers and follow their procedure ... I have it written somewhere ... I think it's [http://ubuntuforums.org/showpost.php?p=6317627&postcount=7](http://ubuntuforums.org/showpost.php?p=6317627&postcount=7) ... I'll be on-line if You need any help.

hi again, took some time and I have tried so many times now, but cannot get the ATI driver loaded. Currently booted in safe-mode with restricted graphics.

when I try to initialize the driver, I get the following:
jannuk@jannuk-laptop:~/Desktop$ sudo aticonfig --initial -f
[sudo] password for jannuk: 
Uninitialised file found, configuring.
[COLOR="Red"]Segmentation fault[/COLOR]
jannuk@jannuk-laptop:~/Desktop$

any ideas?

/JannuK

---

### Post by zika on 2009-01-02
> **jannuk said:**
> hi again, took some time and I have tried so many times now, but cannot get the ATI driver loaded. Currently booted in safe-mode with restricted graphics.

when I try to initialize the driver, I get the following:
jannuk@jannuk-laptop:~/Desktop$ sudo aticonfig --initial -f
[sudo] password for jannuk: 
Uninitialised file found, configuring.
[COLOR=Red]Segmentation fault[/COLOR]
jannuk@jannuk-laptop:~/Desktop$

any ideas?

/JannuK

nothing comes to my mind at this moment. did You get the right driver? it's some sort of memory error. I would try again and, if nothing else works, as a last resort I would use ```
sudo dpkg-reconfigure -phigh xserver-org
``` to get everything as it was before installation, x-wise. then I would retry ... sorry, maybe I'll get some idea later ...

did You try:System->Administration->Hardware drivers?

---

### Post by jannuk on 2009-01-02
> **zika said:**
> nothing comes to my mind at this moment. did You get the right driver? it's some sort of memory error. I would try again and, if nothing else works, as a last resort I would use ```
sudo dpkg-reconfigure -phigh xserver-org
``` to get everything as it was before installation, x-wise. then I would retry ... sorry, maybe I'll get some idea later ...

did You try:System->Administration->Hardware drivers?

driver should be correct, followed the menus on ATI web.

I have tried several times, also following the Wiki pages:
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide")

Last resort, hmmm, the package xserver-org doesn't exist, assuming it should be xserver-xorg. Just cleaning up the xorg.conf file, but when I try to initialize the result is same.

Or do you mean I should reinstall Catalyst package from scratch again?

BTW, the driver is not visible in Hardware Drivers :(

/JannuK

---

### Post by jannuk on 2009-01-02
> **jannuk said:**
> driver should be correct, followed the menus on ATI web.

I have tried several times, also following the Wiki pages:
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide")

Last resort, hmmm, the package xserver-org doesn't exist, assuming it should be xserver-xorg. Just cleaning up the xorg.conf file, but when I try to initialize the result is same.

Or do you mean I should reinstall Catalyst package from scratch again?

BTW, the driver is not visible in Hardware Drivers :(

/JannuK


One more thing,

the packages XFree86-Mesa-libGL and XFree86-libs seems not to be installed, according to AMD installation notes it should be a prerequisite... tried to search for those for Ubuntu, but no luck. Do you know if they are needed or not?

/JannuK

---

### Post by oceanexplorer on 2009-01-02
I presume you have tried installing xorg-driver-fglrx from the repos? I installed this and jockey-gtk from the command line, then did aticonfig --initial and it created a new xorg.conf I could then get in by issuing startx.

I have a ATI HD2400 card.

Paul

---

### Post by oceanexplorer on 2009-01-02
Oh I did find that booting into safe mode and the using the option fix xserver cleared up any issues in my xorg.conf as I had manually edited it, I was then able to issue aticonfig --initial successfully

---

### Post by xc3RnbFO8P on 2009-01-02
> **jannuk said:**
> One more thing,

the packages XFree86-Mesa-libGL and XFree86-libs seems not to be installed, according to AMD installation notes it should be a prerequisite... tried to search for those for Ubuntu, but no luck. Do you know if they are needed or not?

/JannuK
In Synaptic Package Manager:
Settings> repositories> Ubuntu Software check all
Settings> repositories> Update> check all
Then reload

---

### Post by zika on 2009-01-02
> **jannuk said:**
> One more thing,

the packages XFree86-Mesa-libGL and XFree86-libs seems not to be installed, according to AMD installation notes it should be a prerequisite... tried to search for those for Ubuntu, but no luck. Do you know if they are needed or not?

/JannuK

I've just checked and I do not have them installed, do not even see them in repositories. do You have *ia32-libs *installed (I've just found my notes in a notebook I keep about all the stuff I've done to Ubuntu ;))?

---

### Post by jannuk on 2009-01-03
> **zika said:**
> I've just checked and I do not have them installed, do not even see them in repositories. do You have *ia32-libs *installed (I've just found my notes in a notebook I keep about all the stuff I've done to Ubuntu ;))?

Hi again,

back to start again. Now my card is working with open-source drivers using "ati" as driver in xorg.conf and I will make another try later to install the AMD propriety drivers.

Thanks all for your help and suggestions...

Cheers
JannuK

---

