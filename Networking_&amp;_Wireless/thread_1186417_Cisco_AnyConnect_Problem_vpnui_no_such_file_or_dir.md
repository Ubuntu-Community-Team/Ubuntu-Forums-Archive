---
title: "Cisco AnyConnect Problem: vpnui: no such file or directory"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by JimmyKatz on 2009-06-13
Hello everyone,

Running Ubuntu 9.04 (upgraded from 8.0x using the "upgrade" option) I am trying to get Cisco's AnyConnect VPN client (2.3.0185) working (for the first time, never used it on Linux before).  Installation was no problem but for some reason I just can't start the client.

4yi "uname -a":

```
Linux laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
```The command used to start the client returned an "no such file or directory" error:

```
jk@laptop:/$ ls -la /opt/cisco/vpn/bin
total 5964
drwxr-xr-x 2 root root    4096 2009-06-13 17:30 .
drwxr-xr-x 6 root root    4096 2009-06-13 17:30 ..
-rwxr-xr-x 1 root root 1877992 2009-06-13 17:30 vpn
-rwsr-xr-x 1 root root 1393804 2009-06-13 17:30 vpnagentd
-r--r--r-- 1 root root  785559 2009-06-13 17:30 vpndownloader.sh
-rwxr-xr-x 1 root root 2008588 2009-06-13 17:30 vpnui
-rwxr-xr-x 1 root root    4251 2009-06-13 17:30 vpn_uninstall.sh
jk@laptop:/$ /opt/cisco/vpn/bin/vpnui 
bash: /opt/cisco/vpn/bin/vpnui: No such file or directory
```As we can see from above the files vpnui and vpn do actually exist, yet I am unable to start the client.  To verify the files I ran the file command on them:

```
jk@laptop:/opt/cisco/vpn/bin$ file vpn vpnui
vpn:   ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.5, stripped
vpnui: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.5, stripped

```I am aware that there are other issues running the 32bit client on a 64-bit system but apparently I just can't get it started.

Am I missing something?  Any assistance is highly appreciated.  Thanks.

Jimmy

---

### Post by snits on 2009-07-01
Do you have the 32-bit libraries installed? Try doing ldd ./vpnui and see if it shows a bunch of libraries that it can't find.

---

