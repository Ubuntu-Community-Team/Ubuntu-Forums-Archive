---
title: "unable to to access Wireless adapter AE1000"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by RyanMcD86 on 2010-12-29
so i was reading on how to install this adapter. And then i ran into a little problem with "sudo make install" it said that i was missing rt3572sta.ko. I read these two postings on this. 

[http://ubuntuforums.org/showthread.php?t=1455649](http://ubuntuforums.org/showthread.php?t=1455649)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10212285](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10212285)

and here is what it says in the terminal when i try to "sudo make install" 


"make -C /home/ryan/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/ryan/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/ryan/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.35-24-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3572sta.ko /lib/modules/2.6.35-24-generic/kernel/drivers/net/wireless/
install: cannot stat `rt3572sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/ryan/Downloads/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux'
make: *** [install] Error 2"

Anyone have any idea whats going wrong here. I have done everything i can so far. Any help would be greatly appreciated. thanks :D

---

### Post by PatchesTheCaveman on 2010-12-29
Try:
```
make clean
make
sudo make install
```
and see if it works that time.

---

### Post by RyanMcD86 on 2010-12-29
Awesome! it worked. thanks so much for your help :D

---

