---
title: "Hamachi installation on Ubuntu 10.04"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by RTG2010 on 2010-05-07
Hi,

I've tried to install Hamachi on my Ubuntu 10.04 but it was unsuccessful. I followed the steps below based on a tutorial i found on the web: [http://supware.net/HamachiUbuntuHowto/](http://supware.net/HamachiUbuntuHowto/)

1. Made the fake module "tun", necessary for running VPN apps, which in Ubuntu 10.04 is already compiled in the kernel. Reading several forums on the web they say it was a "work around" for getting VPN apps to work...
    	 	 	 	 	 	  A - mkdir faketun
 	B - cd faketun
 	C - echo -e "#include <linux/module.h>\nstatic int start__module(void) {return 0;}\nstatic void end__module(void){return;}\nmodule_init(start__module);\nmodule_exit(end__module);">tun.c
 	D - echo -e "obj-m += tun.o\nall:\n\tmake -C /lib/modules/\$(shell uname -r)/build/ M=\$(PWD) modules\nclean:\n\tmake -C /lib/modules/\$(shell uname -r)/build/ M=\$(PWD) clean\nclean-files := Module.symvers">Makefile
 	E – make
 	F - sudo depmod -a
 	G - sudo modprobe tun


2. Extracted and installed hamachi:


   	 	 	 	 	 	  tar -zxvf hamachi-0.9.9.9-x.tar.gz
   	 	 	 	 	 	  cd hamachi-0.9.9.9-lnx/
sudo make install
sudo tuncfg


3. Created a group for hamachi and added root and my user to it...



sudo groupadd hamachi
sudo gpasswd -a "myuser" hamachi
sudo gpasswd -a root hamachi
sudo chmod 760 /var/run/tuncfg.sock
sudo chgrp hamachi /var/run/tuncfg.sock


4. According to the article i mentioned above i wrote the following commands in order to fix a possible crash report by Ubuntu:


sudo apt-get install upx-ucl
cd /usr/bin
sudo upx -d hamachi


5. Started to configure Hamachi:


sudo hamachi-init


Until here it was everything fine but when i try to start hamachi it shows the following error:


user@user-laptop:~$ hamachi start

07 13:00:37.102 [  0] [ 3554] tap: connect() failed 111 (Connection refused)


Please, if anyone can help me I would be very glad!!

---

### Post by luca219 on 2010-05-21
```
http://www.ubunturoot.com/2010/05/how-to-install-hamachi-on-ubuntu.html
```
work for my.
my pc Amd 64bit

---

### Post by tkowalski22 on 2011-02-12
I followed this link and it DID NOT WORK for me.  Still comes up with "Starting Hamachi", and never lets me get past this point.  Any other help out there?

Thanks

---

