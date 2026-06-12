---
title: "Geforce 8800 GTX drivers installation problem."
date: 2008-06-11
forum: Multimedia Software
---

### Post by gamer4lyf3 on 2008-06-11
Howdy everyone,
I've come across a problem when it comes to installing my Nvidia drivers. I'm following the instructions given by briandu at this post [http://ubuntuforums.org/showthread.php?t=221313&page=43](http://ubuntuforums.org/showthread.php?t=221313&page=43).  When I get to the part when the nvidia box pops up and asks me if I accept the terms & conditions all is well. But after that it says...
"no precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface from kernel from the NVIDIA ftp site?"
If I say no it makes me quit. If I say yes it can't find them :/. help me please? :).

---

### Post by Pjotr123 on 2008-06-11
Try this other, easier way of installing the right restricted driver:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)
(number 2 )

---

### Post by RESID3NT on 2008-06-11
> **gamer4lyf3 said:**
> Howdy everyone,
I've come across a problem when it comes to installing my Nvidia drivers. I'm following the instructions given by briandu at this post [http://ubuntuforums.org/showthread.php?t=221313&page=43](http://ubuntuforums.org/showthread.php?t=221313&page=43).  When I get to the part when the nvidia box pops up and asks me if I accept the terms & conditions all is well. But after that it says...
"no precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface from kernel from the NVIDIA ftp site?"
If I say no it makes me quit. If I say yes it can't find them :/. help me please? :).


Read here:
[http://ubuntuforums.org/showthread.php?t=822836](http://ubuntuforums.org/showthread.php?t=822836)

CTRL+ALT+F1 to go console, and then
sudo apt-get remove nvidia*
sudo apt-get install build-essential //to install libc
sudo /etc/init.d/gdm stop //to stop X
sudo chmod +x NVIDIA-drivers //change permissions
sudo sh NVIDIA-drivers // run the NVIDIA driver

It worked for me

---

### Post by kpkeerthi on 2008-06-11
> **gamer4lyf3 said:**
> Howdy everyone,
I've come across a problem when it comes to installing my Nvidia drivers. I'm following the instructions given by briandu at this post [http://ubuntuforums.org/showthread.php?t=221313&page=43](http://ubuntuforums.org/showthread.php?t=221313&page=43).  When I get to the part when the nvidia box pops up and asks me if I accept the terms & conditions all is well. But after that it says...
"no precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface from kernel from the NVIDIA ftp site?"
If I say no it makes me quit. If I say yes it can't find them :/. help me please? :).
 Go to System -> Admin -> Hardware Drivers and enable it.

---

### Post by gamer4lyf3 on 2008-06-12
First off thanks everyone for the responses and stuff :).
RESID3NT I tried your method but I just ended up getting the same error as before.
kpkeerthi When I went to where you told me to there wasn't anything there. Like nothing in the box :(.
Pjotr123 When I followed that I was shocked to see that it was working! I got it all installed and then after my restart I got this error.
* Running Local boot scripts (/etc/rc.local)
then it makes it go into safe graphic interface mode :(.

---

### Post by tenmoi on 2008-06-12
> **gamer4lyf3 said:**
> First off thanks everyone for the responses and stuff :).
RESID3NT I tried your method but I just ended up getting the same error as before.
kpkeerthi When I went to where you told me to there wasn't anything there. Like nothing in the box :(.
Pjotr123 When I followed that I was shocked to see that it was working! I got it all installed and then after my restart I got this error.
* Running Local boot scripts (/etc/rc.local)
then it makes it go into safe graphic interface mode :(.

Follow RESID3NT's instructions. some missing parts are:
sudo apt-get install libxft-dev 

Remove any traces of linux-restricted-modules* prior to installing the *.run driver from Nvidia site.

Now when you hit no in response to the blabla no precompiled kernel found, the installer will offer to compile one for you. Hit accept/yes.

from now on just hit yes/accept and there you go.

---

### Post by gamer4lyf3 on 2008-06-12
tenmoi After I hit no where you tell me to it says this:
The CC version failed:

The compiler used to compile the kernel (gcc 4.1) does not exactly math the current compiler (gcc 4.2). The Linux 2.6 kernel module loader rejects kernel modules built with a version of gcc that does not exactly match that of the compiler used to build the running kernel.

if you know what you doing and want to ignore the gcc version check, select "no" to continue installation. Otherwise, select "yes" to abort installation, set the CC environment variable to the name of the compiler used to compile your kernel, and restart installation. Abort now?

When I say no so I can continue with the installation it just gives me another error and makes me abort.

help anyone? :)

---

### Post by tenmoi on 2008-06-12
> **gamer4lyf3 said:**
> tenmoi After I hit no where you tell me to it says this:
The CC version failed:

The compiler used to compile the kernel (gcc 4.1) does not exactly math the current compiler (gcc 4.2). The Linux 2.6 kernel module loader rejects kernel modules built with a version of gcc that does not exactly match that of the compiler used to build the running kernel.

if you know what you doing and want to ignore the gcc version check, select "no" to continue installation. Otherwise, select "yes" to abort installation, set the CC environment variable to the name of the compiler used to compile your kernel, and restart installation. Abort now?

When I say no so I can continue with the installation it just gives me another error and makes me abort.

help anyone? :)

To solve this, you should boot your newest kernel - I mean the most recently updated one. Then  update and upgrade every thing and repeat the said steps to install.

best of luck!

Just a side note. You can enable the proposed update and update to the newest kernel of 2.6.24.19. 
Update and upgrade every thing before the install.

---

### Post by gamer4lyf3 on 2008-06-18
I'm back! still needing help. How do I go about booting my newest kernel though? :/. I don't get it.

---

### Post by Pjotr123 on 2008-06-18
Maybe your installation is polluted by unsuccesful tinkering. Consider a clean reinstallation and then apply my earlier tip.

This is the easiest way for a reinstallation:
[http://ubuntutip.googlepages.com/reinstall](http://ubuntutip.googlepages.com/reinstall)

Afterwards, do this list:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)

---

### Post by gamer4lyf3 on 2008-06-20
:o! a reinstallation :(. Is there any other option? I'm going to start backing up my stuff just encase there isn't though.

---

