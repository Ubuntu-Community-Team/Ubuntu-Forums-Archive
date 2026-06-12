---
title: "Cannot SSH"
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by NateN34 on 2010-12-23
Hi,

Well I have been having alot of problems with my new VPS  CentOS 5 installation. The problem is not on their end, as they have  reinstalled my VPS twice and moved nodes 3 times. 

The problem is  that the OS installs and runs, but I cannot externally access it  through SSH or FTP. It always says "connection timed out". Although in  the control panels console, I can do everything to the OS.

EDIT: Here is what it says in the console. 
[HTML]Natemodprobe: FATAL: Could not load /lib/modules/2.6.33.3/modules.dep: No such file or direc
tory
INIT: Entering runlevel: 3
FATAL: Could not load /lib/modules/2.6.33.3/modules.dep: No such file or directory
CRITICAL : [ipv6_test] Kernel is not compiled with IPv6 support
Bringing up loopback interface:  [  OK  ]
Bringing up interface eth0:  [  OK  ]
FATAL: Could not load /lib/modules/2.6.33.3/modules.dep: No such file or directory
CRITICAL : [ipv6_test] Kernel is not compiled with IPv6 support
Mounting other filesystems:  [  OK  ]
Starting sshd: modprobe: FATAL: Could not load /lib/modules/2.6.33.3/modules.dep: No suc
h file or directory
modprobe: FATAL: Could not load /lib/modules/2.6.33.3/modules.dep: No such file or direc
tory[/HTML]So this seems to be an SSH problem I am having.

So my question is, how do I fix this?

Thanks in advance,

---

### Post by puppywhacker on 2010-12-23
Ubuntu is based on Debian
CentOS is based on Redhat

The error message you posted indicates that you can't load kernel modules. The Linux kernel would get too big if it would contain all possible options, since you don't need most options, the linux kernel can load modules. For instance ipv6.ko is a module which may or may not need. you probably don't need IPv6, so you could also disable it in the /etc/ssh/sshd.conf file.

To load the modules there is a dependency file that knows which modules exist and if they should be loaded in a specific order. In your error message the module dependancy file for kernel 2.6.33 is missing.

```
/lib/modules/2.6.33.3/modules.dep
```

you can create the file by command (maybe you don't need the -a)
```
sudo depmod -a
```

---

