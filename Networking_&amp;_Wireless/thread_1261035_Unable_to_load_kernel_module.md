---
title: "Unable to load kernel module"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by sirajrathore on 2009-09-08
Hi
 
 
I am using ubuntu 8.04 with kernel 2.6.24 server. The NIC (Intel PRO/1000 quad port PT server adapter) is working properly here and shows all four Interfaces.The driver modules are also loaded correctly
#lsmod | grep e1000
output:
e1000
e1000e

But when i installed openvz virtualization setup . openvz uses a kernel based on kernel 2.6.18. In openvz environment this NIC is not detected.
#uname -r
2.6.18-14-ovz-amd-smp
#lsmod | grep e1000
output:
e1000 
here it only showed e1000. And e1000e did not exists which was required driver for this card,i installed it explicitly. it installed successfull and e1000e.ko had been created. Now when i tried to load this module.It threw an error.
 
#modprobe e1000e

---------------------
output:
e1000e: version magic '2.6.18-14-ovz-amd64-smp SMP mod_unload gcc-4.2' should be '2.6.18-14-ovz-amd64-smp SMP mod_unload gcc-4.1'
FATAL:Error inserting e1000e (/lib/modules/2.6.18-14-ovz-amd64-smp/kernel/drivers/net/e1000e/e1000e.ko): Invalid module format
-----------------------------------------
gcc information: (the following gcc packages are installed on my machine)
#dpkg --get-selections |grep gcc
gcc install
gcc-3.4 install
gcc-3.4-base install
gcc-4.1 install
gcc-4.2 install
gcc-4.2-base install
libgcc1 install
-----------------------------------------
 
Can any body suggest how to handle this problem.

Thanks & Regards
Siraj Rathore

---

### Post by jerrrys on 2009-09-08
i do not use openvz, but ran across this about the 2.6 kernel

[http://www.howtoforge.com/installing-and-using-openvz-on-ubuntu-8.10](http://www.howtoforge.com/installing-and-using-openvz-on-ubuntu-8.10)

found it here

[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=c3O&num=50&q=openvz+virtualization+setup+ubuntu&aq=f&oq=&aqi=](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=c3O&num=50&q=openvz+virtualization+setup+ubuntu&aq=f&oq=&aqi=)

---

