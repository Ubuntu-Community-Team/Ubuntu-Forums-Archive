---
title: "Driver bt878 on Ubuntu 14.04"
date: 2015-02-10
forum: Multimedia Software
---

### Post by Koljan1970 on 2015-02-10
Hi! No problems found earlier in this manual: http: // wwww.ubuntuforums.org/showthread.php? t 882678
Having established the next distribution kit on the basis of Ubuntu 14.04 this instruction does not work

---

### Post by Yellow Pasque on 2015-02-10
The driver should be included automatically. Show output of:
```
sudo modinfo bt878
dmesg | grep 878
```

---

### Post by Koljan1970 on 2015-02-11
> **Temüjin said:**
> The driver should be included automatically. Show output of:
```
sudo modinfo bt878
dmesg | grep 878
```

k@k-775Dual-915GL ~ $ sudo modinfo bt878
[sudo] password for k: 
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/media/pci/bt8xx/bt878.ko
license:        GPL
srcversion:     84DA652879F969AE29A6318
alias:          pci:v0000109Ed00000878sv00001822sd00000026bc*sc*i*
alias:          pci:v0000109Ed00000878sv00007063sd00002000bc*sc*i*
alias:          pci:v0000109Ed00000878sv000018ACsd0000D500bc*sc*i*
alias:          pci:v0000109Ed00000878sv000018ACsd0000DB11bc*sc*i*
alias:          pci:v0000109Ed00000878sv000018ACsd0000DB10bc*sc*i*
alias:          pci:v0000109Ed00000878sv00001461sd00000771bc*sc*i*
alias:          pci:v0000109Ed00000878sv0000270Fsd0000FC00bc*sc*i*
alias:          pci:v0000109Ed00000878sv00001822sd00000001bc*sc*i*
alias:          pci:v0000109Ed00000878sv000011BDsd00000026bc*sc*i*
alias:          pci:v0000109Ed00000878sv000011BDsd0000001Cbc*sc*i*
alias:          pci:v0000109Ed00000878sv00001461sd00000761bc*sc*i*
alias:          pci:v0000109Ed00000878sv00000071sd00000101bc*sc*i*
depends:        bttv
vermagic:       3.13.0-37-generic SMP mod_unload modversions 686 
parm:           verbose:verbose startup messages, default is 1 (yes) (int)
parm:           debug:Turn on/off debugging, default is 0 (off). (int)
k@k-775Dual-915GL ~ $ dmesg | grep 878
[    0.114995] pci 0000:01:06.1: [109e:0878] type 00 class 0x048000
[   18.519878] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   19.077615] bttv: 0: Bt878 (rev 17) at 0000:01:06.0, irq: 19, latency: 32, mmio: 0xfbfff000
[   19.192618] ir-kbd-i2c: i2c IR (KNC One) detected at i2c-0/0-0030/ir0 [bt878 #0 [sw]]
k@k-775Dual-915GL ~ $

---

### Post by Yellow Pasque on 2015-02-11
Yes, the module exists and detects your card. Does it not function correctly?

---

### Post by Koljan1970 on 2015-02-11
> **Temüjin said:**
> Yes, the module exists and detects your card. Does it not function correctly?


Works well in Linux Mint 13 (Ubuntu 12.04), and in Linux Mint 17 (Ubuntu 14.04) does not work

Here's a snapshot tvtime : 

[IMG]http://smages.com/images/lzlugu.png[/IMG]

When installing the driver for this instruction :

[http://wwww.ubuntuforums.org/showthread.php?t=882678](http://wwww.ubuntuforums.org/showthread.php?t=882678)

In the sixth paragraph terminal shows:

k@k-775Dual-915GL /usr/src/v4l-dvb $ sudo make
make -C /usr/src/v4l-dvb/v4l 
make[1]: Entering directory `/usr/src/v4l-dvb/v4l'
Updating/Creating .config
Preparing to compile for kernel version 3.3.0
File not found: /lib/modules/3.3.0-37-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
make[1]: Leaving directory `/usr/src/v4l-dvb/v4l'
make: *** [all] Error 2
k@k-775Dual-915GL /usr/src/v4l-dvb $ 

Next :

k@k-775Dual-915GL /usr/src/v4l-dvb $ sudo make install
make -C /usr/src/v4l-dvb/v4l install
make[1]: Entering directory `/usr/src/v4l-dvb/v4l'
-e 
Removing obsolete files from /lib/modules/3.3.0-37-generic/kernel/drivers/media/video:

-e 
Removing obsolete files from /lib/modules/3.3.0-37-generic/kernel/drivers/media/common:

-e 
Removing obsolete files from /lib/modules/3.3.0-37-generic/kernel/drivers/media/dvb/cinergyT2:

-e 
Removing obsolete files from /lib/modules/3.3.0-37-generic/kernel/drivers/media/dvb/frontends:

Installing kernel modules under /lib/modules/3.3.0-37-generic/kernel/drivers/media/:
/sbin/depmod -a 3.3.0-37-generic 
depmod: ERROR: could not open directory /lib/modules/3.3.0-37-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
make[1]: *** [media-install] Error 1
make[1]: Leaving directory `/usr/src/v4l-dvb/v4l'
make: *** [install] Error 2
k@k-775Dual-915GL /usr/src/v4l-dvb $

---

### Post by Koljan1970 on 2015-02-16
I have understood why it is impossible, writes 3.3.0-37-generic whereas I have linux-headers--3.13.0-37-generic, what it is possible to make a kernel in the given situation?

---

### Post by Yellow Pasque on 2015-02-16
The modules are already present and installed. You should not need to build them. If you do need to build modules, you are using instructions and code that have not been updated in 4 years, so it is no surprise that it does not build with a modern kernel. It looks like linuxtv code is now here: [http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

BEFORE toying with building modules, you should try to tweak the parameters of the bttv module as the post you link to suggests:
```
echo "options bttv card=<cardnumber> tuner=<tunernumber> radio=1" | sudo tee -a /etc/modprobe.d/bttv.conf
```
You substitute the corresponding number here in place of <cardnumber>: [http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.bttv](http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.bttv)
You substitute the corresponding number here in place of <tunernumber>: [http://tldp.org/HOWTO/BTTV/modprobe.html](http://tldp.org/HOWTO/BTTV/modprobe.html)

---

### Post by Koljan1970 on 2015-02-16
> **Temüjin said:**
> The modules are already present and installed. You should not need to build them. If you do need to build modules, you are using instructions and code that have not been updated in 4 years, so it is no surprise that it does not build with a modern kernel. It looks like linuxtv code is now here: [http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

BEFORE toying with building modules, you should try to tweak the parameters of the bttv module as the post you link to suggests:
```
echo "options bttv card=<cardnumber> tuner=<tunernumber> radio=1" | sudo tee -a /etc/modprobe.d/bttv.conf
```
You substitute the corresponding number here in place of <cardnumber>: [http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.bttv](http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.bttv)
You substitute the corresponding number here in place of <tunernumber>: [http://tldp.org/HOWTO/BTTV/modprobe.html](http://tldp.org/HOWTO/BTTV/modprobe.html)

According to this list [http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.bttv](http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.bttv) my cardnumber 78 
Jetway TV/Capture JW-TV878-FBK, Kworld KW-TV878RF   [0a01:17de]

which corresponds to the fact that I introduced earlier distributions in /etc/modprobe.d/options

but according to this list [http://tldp.org/HOWTO/BTTV/modprobe.html](http://tldp.org/HOWTO/BTTV/modprobe.html) I do not see my tuner, in my previous distributions(Ubuntu 10.10 -12.04) tunernumber there was 51 (tuner=51 - Philips PAL/SECAM_D (FM 1256 I-H3)), because my file /etc/modprobe.d/options looked so:

options bttv card=78 tuner=51 radio=1

now with these settings does not work

Please forgive me I'm not really a great expert, if you can then write detailed instructions

---

### Post by Yellow Pasque on 2015-02-16
The link I gave for tuner numbers looks like it is (very) outdated. If tuner=51 worked before, then it should work now.

> my file /etc/modprobe.d/options
A few years ago, developers decided files in the /etc/modprobe.d/ directory must end in .conf to be read. If you're still using a file named "options", it's probably not being read in Ubuntu 14.04, so you would need to rename it:
```
cd /etc/modprobe.d
sudo mv options bttv.conf
```

---

### Post by Koljan1970 on 2015-02-16
> **Temüjin said:**
> The link I gave for tuner numbers looks like it is (very) outdated. If tuner=51 worked before, then it should work now.


A few years ago, developers decided files in the /etc/modprobe.d/ directory must end in .conf to be read. If you're still using a file named "options", it's probably not being read in Ubuntu 14.04, so you would need to rename it:
```
cd /etc/modprobe.d
sudo mv options bttv.conf
```

Thank works !!!

---

