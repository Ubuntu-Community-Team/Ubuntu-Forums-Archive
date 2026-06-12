---
title: "Need Help Installing Schools VPN Client"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by kevo214 on 2009-02-26
Okay so I'm here at PSU and we need to use a VPN client to connect to our wireless network. They provide the client we need to use in all the flavors (Mac, Windows, Linux). Now I'm not the best with Ubuntu so I'm kind of winging it and doing what I can and looking up the rest. So far things were going pretty good. I'm following what looks to be a guide found here 
[http://www.hbg.psu.edu/iit/wireless/linux-choices.html](http://www.hbg.psu.edu/iit/wireless/linux-choices.html)
but instead of actually connecting to the internet to get the files I've already got them extracted and stuff on the computer. So I "cd  /home/kevin/Desktop/vpnclient". I run the ./vpn_install file and everything goes fine. I answer yes and okay to a few question and it's on a it's way. And eventually I hit the bump and get:
> 
Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.24-23-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.24-23-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.24-23-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.24-23-generic/build SUBDIRS=/home/kevin/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
  CC [M]  /home/kevin/Desktop/vpnclient/linuxcniapi.o
In file included from /home/kevin/Desktop/vpnclient/Cniapi.h:15,
                 from /home/kevin/Desktop/vpnclient/linuxcniapi.c:31:
/home/kevin/Desktop/vpnclient/GenDefs.h:113: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/home/kevin/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/kevin/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".


---

### Post by kevo214 on 2009-02-26
So I managed to copy the extracted folder and all subdirectories to /usr/src which is where the tutorial had them but it made no difference. It still hangs at the same place. >.<

---

### Post by kevo214 on 2009-02-26
Anyone?

---

### Post by kevo214 on 2009-02-26
So someone in my dorm was able to help me. He told me that I don't need to use the schools VPN client just any Cisco one. He directed me to use VPNC and hopefully I can get this one working.

---

### Post by jonobr on 2009-02-26
Hey

Did you check the following link?

[This ]("http://http://www.lamnk.com/blog/vpn/with-kernel-2624-you-will-need-a-patch-to-install-cisco-vpn-client/") was reported in Arch but its the same error message recorded?

Mentions a required patch for cisco 32 bit?

---

### Post by Karychy on 2009-03-02
Hi,

I was experiencing a similar problem. I have a cisco vpn 4.8.0.0640 and a 2.6.27 linux kernel. I read that some kernel versions required a patch, but there doesn't seem to be such for 2.6.27. 

This is what i was getting:

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.27-11-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/usr/src/linux-headers-2.6.27-11-generic/include/linux" will be used to build the module.

Is the above correct [y]y

Making module
make -C /usr/src/linux-headers-2.6.27-11-generic/include/linux SUBDIRS=/home/karychy/univpn/vpn1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic/include/linux'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic/include/linux'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

I don't remember where I read to use the '/include/linuc' part. I am sure I tried without it and it didn't work.
What I did was to install the patch from [http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24-final.diff](http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24-final.diff) .
Then I tried again, got the same error message, then tried with the path without /include/linux and it worked. I am not
sure whether the patch did it, or it was my mistake with the path from the start. I just hope this might help someone else save a similar problem!

---

