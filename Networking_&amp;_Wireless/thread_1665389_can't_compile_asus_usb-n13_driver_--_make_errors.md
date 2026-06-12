---
title: "can't compile asus usb-n13 driver -- make errors"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by kmiya100 on 2011-01-12
I am trying to install the asus usb-n13 driver, but it gives errors during the make.  Here is the end part that shows up in my terminal when I try to make.  I'm not sure how to show the entire terminal in a post.  I do have the build-essential package, and have compiled other things.  Any help would be great.  

/home/kurt/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSTaskAttach’:
/home/kurt/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/rt_linux.c:1283: warning: passing argument 1 of ‘kthread_create’ from incompatible pointer type
include/linux/kthread.h:7: note: expected ‘int (*)(void *)’ but argument is of type ‘RTMP_OS_TASK_CALLBACK’
/home/kurt/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevDetach’:
/home/kurt/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/rt_linux.c:1614: warning: initialization discards qualifiers from pointer target type
/home/kurt/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/kurt/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/rt_linux.c:1653: warning: initialization discards qualifiers from pointer target type
/home/kurt/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/rt_linux.c:1653: warning: ISO C90 forbids mixed declarations and code
  CC [M]  /home/kurt/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/rt_main_dev.o
/home/kurt/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/rt_main_dev.c: In function ‘RtmpOSIRQRequest’:
/home/kurt/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/rt_main_dev.c:951: warning: unused variable ‘net_dev’
  CC [M]  /home/kurt/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/ba_action.o
  CC [M]  /home/kurt/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/cmm_mac_usb.o
/home/kurt/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitRecv’:
/home/kurt/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/cmm_mac_usb.c:83: error: implicit declaration of function ‘usb_buffer_alloc’
/home/kurt/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/cmm_mac_usb.c:83: warning: assignment makes pointer from integer without a cast
/home/kurt/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/cmm_mac_usb.c:112: error: implicit declaration of function ‘usb_buffer_free’
make[2]: *** [/home/kurt/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/kurt/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2
kurt@Kurt:~/Desktop/RT3070_LinuxSTA_V2.3.0.1_20100208$

---

### Post by chili555 on 2011-01-12
I just downloaded, extracted and made the later version 2.4.0.1 and it makes without error.

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

---

### Post by kmiya100 on 2011-01-13
Chili555, thanks for sending the link.  I did get it to make with no problems.  I'll go back to your other posts to see how to get the device working.

By the way, how do I list this as solved?

---

### Post by chili555 on 2011-01-13
Select thread tools at the top and select Mark as Solved.

---

### Post by kmiya100 on 2011-01-13
Thanks for all your help.  I am all connected via wireless.

---

### Post by nickbodd on 2011-03-01
sorry for posting in a solved thread.. 

but I tried compiling railink 2870 USB 2.4.0.1 version and I get the compile error. 

```

/home/nick/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:610: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/nick/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/nick/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:628: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/nick/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘UCHAR **’
make[2]: *** [/home/nick/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/nick/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-27-generic'
make: *** [LINUX] Error 2


```

I am struggling to get the wireless drivers working. Someone Plz help me..

---

### Post by chili555 on 2011-03-02
> **nickbodd said:**
> sorry for posting in a solved thread.. 

but I tried compiling railink 2870 USB 2.4.0.1 version and I get the compile error. 
--- snip ---
I am struggling to get the wireless drivers working. Someone Plz help me..rt2870sta is included in the later kernels; why is it not working out of the box for you? Please post:```
lsusb
modinfo rt2870sta
lsmod | grep rt2
```Thanks.

---

### Post by nickbodd on 2011-03-02
Hey..
Here is the output from the terminal.

ASUS USB N13 is my wireless adapter.. So its detected at least I think?

```

nick@ubuntu:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:071d Microsoft Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 056a:00d1 Wacom Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 001 Device 002: ID 03f0:8007 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
nick@ubuntu:~$ modinfo rt2870sta
filename:       /lib/modules/2.6.35-27-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        2.1.0.0
license:        GPL
description:    RT2870/RT3070 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
firmware:       rt3071.bin
firmware:       rt3070.bin
firmware:       rt2870.bin
srcversion:     93E93E3E336F412601AF0FA
alias:          usb:v0411p015Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED14d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p016Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp935Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp935Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp825Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        crc-ccitt
staging:        Y
vermagic:       2.6.35-27-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)
nick@ubuntu:~$ lsmod |grep rt2
nick@ubuntu:~$ 

```

---

### Post by chili555 on 2011-03-02
> ID [COLOR="Red"]0b05:1784[/COLOR] ASUSTek Computer, Inc. 802.11n Network Adapter
> modinfo rt2870sta
filename:       /lib/modules/2.6.35-27-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        2.1.0.0
license:        GPL
description:    RT2870/RT3070 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
--- snip ---
alias:          usb:v[COLOR="Red"]0B05[/COLOR]p[COLOR="Red"]1784[/COLOR]d*dc*dsc*dp*ic*isc*ip*
Unfortunately, the device is also claimed by rt2800usb. Let's blacklist it and its family:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines at the end:```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Now let's load rt2870sta:```
sudo su
echo rt2870sta >> /etc/modules
modprobe rt2870sta
exit
iwconfig
```Is your wireless working?

---

### Post by nickbodd on 2011-03-02
I was doing what you said but I get this error message for some reason.

```

root@ubuntu:/home/nick# echo rt2870sta >> /etc/modules
root@ubuntu:/home/nick# modprobe rt2870sta
sh: /: Permission denied
sh: cannot create /: Is a directory
FATAL: Error running install command for rt2870sta

```

---

### Post by chili555 on 2011-03-02
Hmmm, that's a new one on me. Please try this:```
exit
```Make sure you are now an ordinary user; that is, your command prompt shows your user name, not root. Also be sure you are in the correct directory ~.```
cd
```Now, the command prompt should be something like:> nick@ubuntu:~$Now do:```
sudo modprobe rt2870sta
iwconfig
```Post any errors.

---

### Post by nickbodd on 2011-03-02
I get the same error..

```

nick@ubuntu:~$ sudo modprobe rt2870sta
sh: /: Permission denied
sh: cannot create /: Is a directory
FATAL: Error running install command for rt2870sta

```

---

### Post by chili555 on 2011-03-02
Weird. I think something is wrong but I've never seen it before so I haven't much of a clue what to do to fix it. May I see:```
cat /etc/udev/rules.d/network_drivers.rules
cat /etc/modprobe.d/network_drivers.conf
modinfo rt2870sta | grep -i version
```Other than trying to compile this downloaded file, what else have you tried?

---

### Post by nickbodd on 2011-03-02
I have looked at other thread, well your solution that previously worked for others..

Here is the output..
```

nick@ubuntu:~$ cat /etc/udev/rules.d/network_drivers.rules
ACTION == "add", SUBSYSTEM == "usb", ATTR {idVendor} == "0b05", ATTR {idProduct} == "1784", RUN + = "/ sbin / modprobe-qba rt2870sta"
nick@ubuntu:~$ cat /etc/modprobe.d/network_drivers.conf
install rt2870sta / sbin / modprobe - ignore-install rt2870sta $ CMDLINE_OPTS; / bin / echo "0b05 1784"> / sys/bus/usb/drivers/rt2870/new_id
nick@ubuntu:~$ modinfo rt2870sta |grep -i version
version:        2.1.0.0
srcversion:     93E93E3E336F412601AF0FA
vermagic:       2.6.35-27-generic SMP mod_unload modversions 
nick@ubuntu:~$ 


```

---

### Post by chili555 on 2011-03-02
> **nickbodd said:**
> I have looked at other thread, well your solution that previously worked for others..

Here is the output..
```

nick@ubuntu:~$ cat /etc/udev/rules.d/network_drivers.rules
ACTION == "add", SUBSYSTEM == "usb", ATTR {idVendor} == "0b05", ATTR {idProduct} == "1784", RUN + = "/ sbin / modprobe-qba rt2870sta"
nick@ubuntu:~$ cat /etc/modprobe.d/network_drivers.conf
install rt2870sta / sbin / modprobe - ignore-install rt2870sta $ CMDLINE_OPTS; / bin / echo "0b05 1784"> / sys/bus/usb/drivers/rt2870/new_id
nick@ubuntu:~$ modinfo rt2870sta |grep -i version
version:        2.1.0.0
srcversion:     93E93E3E336F412601AF0FA
vermagic:       2.6.35-27-generic SMP mod_unload modversions 
nick@ubuntu:~$ 


```This part is not needed if the native driver claims your device. The latest version does. Moreover, this part, and other parts, are mis-typed:> "/ sbin / modprobe-qba rt2870sta"Since it's not needed at all, let's eliminate it:```
sudo rm /etc/udev/rules.d/network_drivers.rules
sudo rm /etc/modprobe.d/network_drivers.conf
```Reboot and let me know how your wireless is working.

---

### Post by nickbodd on 2011-03-02
omg... cant believe.. its actually working..

THANKS A LOTTTT!!:D

I have wasted 2 days figuring this. Thanks again..

---

### Post by rayjonesy on 2011-06-18
This is what fixed my problem, after trying all of Chili's solutions in numerous threads on here, yes I searched. ;)

[http://www.linuxcrew.de/blog/2010/10/11/rt2870-compile-error-under-kubuntu-maverick-10-10/?lang=en](http://www.linuxcrew.de/blog/2010/10/11/rt2870-compile-error-under-kubuntu-maverick-10-10/?lang=en)

The cause for these errors is that the driver makes use of the  functions usb_buffer_alloc() and usb_buffer_free() which got renamed in  kernel 2.6.35. This is stated in the [Changelog]("http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.35"):
    USB: rename usb_buffer_alloc() and usb_buffer_free() users
    For more clearance what the functions actually do,
      usb_buffer_alloc() is renamed to usb_alloc_coherent()
      usb_buffer_free()  is renamed to usb_free_coherent()So to  get rid of the error messages all you have to do is to rename the  function in include/os/rt_linux.h. To make it easier you can download a  patch [here]("http://www.linuxcrew.de/blog/2010/10/11/wp-content/uploads/2010/10/rt2870sta_usb_kernel2635.patch"). Just run the following command in the driver directory:
patch -ul -p0 -i path/to/patchOr use the one-liner:
wget -qO- [http://www.linuxcrew.de/wp-content/uploads/2010/10/rt2870sta_usb_kernel2635.patch](http://www.linuxcrew.de/wp-content/uploads/2010/10/rt2870sta_usb_kernel2635.patch) | patch -ul -p0

----------------------

After patching the file include/os/rt_linux.h I was able to make with no issues.
Before that I kept getting this error:
make[2]: *** [/root/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/root/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [LINUX] Error 2

The patch fixed it!

---

### Post by borromeotlhs on 2011-06-23
WOW,
The post about blacklisting the other drivers seemed to be the thing that worked.  I am on ubuntu 11.04, and i just bought this thing because it said it worked for linux.  i downloaded the newest drivers from your link, and i still got errors on make.  Once i blacklisted and rebooted, i saw the green light, and i was done (I am not even sure inputting all the pertinent data into the RT2070STA.dat file even helped, but who cares as it works now!)

Thanks for being awesome! :guitar:

---

