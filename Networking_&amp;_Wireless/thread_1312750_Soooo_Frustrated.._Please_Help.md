---
title: "Soooo Frustrated.. Please Help"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by BURMAT on 2009-11-03
I have been trying to get a cisco vpn client working on my laptop running ubuntu 9.10 and gnome 2.26.1.  I need to have it running to connect to my campus wireless.  It is NOT supported by campus, so I cannot take my problems to them.  I have tried running kvpnc instead and it works only works the very first time.  To get it to work again I have to uninstall and reinstall it and connect.  After connecting at a different time, it will say it's connected but when I open firefox I get a "Not using vpn bla bla.." page.

I guess I just need suggestions and help... This is the only reason I may have to duel boot.  I am on campus too often to not beable to connect to the internet.  I have been running Ubuntu for a couple months now but am not a genius yet.  I will post the errors I get from installing the campus vpn client.  Any suggestions on what I may need to do are GREATLY appreciated.


-Nate

---

### Post by BURMAT on 2009-11-03
USER@USER-laptop:~/Desktop/vpnclient$ sudo ./vpn_install 
 Cisco Systems VPN Client Version 4.6.00 (0045) Linux Installer 
 Copyright (C) 1998-2004 Cisco Systems, Inc. All Rights Reserved. 
  
 By installing this product you agree that you have read the 
 license.txt file (The VPN Client license) and will comply with 
 its terms. 

  
 Directory where binaries will be installed [/usr/local/bin] 
  
 Automatically start the VPN service at boot time [yes] 
  
 In order to build the VPN kernel module, you must have the 
 kernel headers for the version of the kernel you are running.  
  
 Directory containing linux kernel source code [/lib/modules/2.6.28-16-generic/build] 
  
 * Binaries will be installed in "/usr/local/bin". 
 * Modules will be installed in "/lib/modules/2.6.28-16-generic/CiscoVPN". 
 * The VPN service will be started AUTOMATICALLY at boot time. 
 * Kernel source from "/lib/modules/2.6.28-16-generic/build" will be used to build the module. 
  
 Is the above correct [y] 
  
 Making module 
 make -C /lib/modules/2.6.28-16-generic/build SUBDIRS=/home/USER/Desktop/vpnclient modules 
 make[1]: Entering directory `/usr/src/linux-headers-2.6.28-16-generic' 
   CC [M]  /home/USER/Desktop/vpnclient/linuxcniapi.o 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory 
 In file included from /home/USER/Desktop/vpnclient/Cniapi.h:15, 
                  from /home/USER/Desktop/vpnclient/linuxcniapi.c:34: 
 /home/USER/Desktop/vpnclient/GenDefs.h:114: error: conflicting types for ‘uintptr_t’ 
 include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here 
 /home/USER/Desktop/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’: 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:315: error: ‘struct sk_buff’ has no member named ‘stamp’ 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:347: error: ‘struct sk_buff’ has no member named ‘nh’ 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:348: error: ‘struct sk_buff’ has no member named ‘mac’ 
 /home/USER/Desktop/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’: 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:452: error: ‘struct sk_buff’ has no member named ‘stamp’ 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:456: error: ‘struct sk_buff’ has no member named ‘mac’ 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:457: error: ‘struct sk_buff’ has no member named ‘nh’ 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:460: error: ‘struct sk_buff’ has no member named ‘h’ 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:460: error: ‘struct sk_buff’ has no member named ‘nh’ 
 make[2]: *** [/home/USER/Desktop/vpnclient/linuxcniapi.o] Error 1 
 make[1]: *** [_module_/home/USER/Desktop/vpnclient] Error 2 
 make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-16-generic' 
 make: *** [default] Error 2 
 Failed to make module "cisco_ipsec.ko". 
 USER@USER-laptop:~/Desktop/vpnclient$

---

### Post by JorgeLarre on 2009-11-14
Burmat:

You may want to follow exactly the instructions in these two blogs (they are pretty much the same, use the one you like the most):

[http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/](http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/)

[http://www.blog.arun-prabha.com/2006/11/16/installing-cisco-vpn-and-vpnc-in-ubuntu/](http://www.blog.arun-prabha.com/2006/11/16/installing-cisco-vpn-and-vpnc-in-ubuntu/)

I suggest that first you delete any version you may have of vpn and proceed from scratch as per the instructions in these blogs.

Jorge

---

