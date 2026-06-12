---
title: "Trying to tether HTCHD Winmobile 6.1 but failed many time now and before"
date: 2010-08-12
forum: Networking &amp; Wireless
---

### Post by amin7 on 2010-08-12
I'm using Ubuntu 10 at the office. It's connected with office network but it is very very slow most and all the time. The reason i want to tether is that office network very slow all the time and i have winmobile 6.1 phone with unlimitted broadband. When I use my windows laptop, I always use tethering to escape slow network but always failed to use with my ubuntu sun workstation. Today is my 3rd attemp still failed after following some previous post on the same subject.  I hope I could do this. I tried to champion the use of linux in my office BUT even I myself can not solved this problem. Any master here could help me

--I follow the following precedure--
svn co [https://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite/](https://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite/)
cd usb-rndis-lite/
make
sudo ./clean.sh
sudo make install
--I got this error during 'make'--
amin@aminu10:~$ ls
Desktop    Downloads         MCNP5  Pictures  Templates       Videos
Documents  examples.desktop  Music  Public    usb-rndis-lite  zimbra
amin@aminu10:~$ cd usb-rndis-lite/
amin@aminu10:~/usb-rndis-lite$ ls
cdc_ether.c  Kbuild    ndis.h     rndis_host.c  usbnet.h
clean.sh     Makefile  reload.sh  usbnet.c
amin@aminu10:~/usb-rndis-lite$ make
make -C /lib/modules/2.6.32-24-generic/build SUBDIRS=/home/amin/usb-rndis-lite modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/amin/usb-rndis-lite/usbnet.o
Assembler messages:
Fatal error: can't create /home/amin/usb-rndis-lite/.tmp_usbnet.o: Permission denied
/home/amin/usb-rndis-lite/usbnet.c: In function ‘usbnet_probe’:
/home/amin/usb-rndis-lite/usbnet.c:1199: error: ‘struct net_device’ has no member named ‘change_mtu’
/home/amin/usb-rndis-lite/usbnet.c:1200: error: ‘struct net_device’ has no member named ‘get_stats’
/home/amin/usb-rndis-lite/usbnet.c:1201: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
--------------------------------------

---

