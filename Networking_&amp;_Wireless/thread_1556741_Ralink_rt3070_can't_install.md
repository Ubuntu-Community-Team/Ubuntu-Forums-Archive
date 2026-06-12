---
title: "Ralink rt3070 can't install"
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by ronbrooks on 2010-08-19
I am trying to get my usb wireless to work on Ubuntu 10.4 I found a how to and followed it but when I did a Make install this is what I got. 

make -C /home/ronald/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/ronald/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp /home/ronald/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/RT3070STA.dat /etc/Wireless/RT3070STA/.
install -d /lib/modules/2.6.32-24-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3070sta.ko /lib/modules/2.6.32-24-generic/kernel/drivers/net/wireless/
install: cannot stat `rt3070sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/ronald/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux'
make: *** [install] Error 2

could anyone help me on this.

---

### Post by ronbrooks on 2010-08-20
Bump

---

### Post by Gaygerbil on 2010-10-07
I'm getting the same error, help would be appreciated.

---

### Post by dineshs on 2010-10-08
[http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)

---

### Post by Gaygerbil on 2010-10-08
I got it to work yesterday, I used a guide similar to that which told me to blacklist some other drivers also and it worked for me, thanks though! :]

---

### Post by dineshs on 2010-10-08
Can you please post how you solved the problem?

---

