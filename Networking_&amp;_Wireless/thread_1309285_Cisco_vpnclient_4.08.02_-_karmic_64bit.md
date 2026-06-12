---
title: "Cisco vpnclient 4.08.02 - karmic 64bit"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by micio on 2009-11-01
Hi all,
This is a strange and maybe stupid problem, but I can't figure out what happens...
I downloaded the last vpnclient installer, patch it correctly and I got a good installation.. however when I run 
```
vpnclient
```
or
```
sudo vpnclient
```
I got no such file or directory, but this is impossible, the files are there!! 
However below there is the full log of installation
```
# sudo ./vpn_install 
Cisco Systems VPN Client Version 4.8.02 (0030) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.                                                    


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.31-14-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.31-14-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.            
* Kernel source from "/lib/modules/2.6.31-14-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/micio/Scaricati/vpnclient modules
make[1]: ingresso nella directory «/usr/src/linux-headers-2.6.31-14-generic»                
  CC [M]  /home/micio/Scaricati/vpnclient/interceptor.o                                     
/home/micio/Scaricati/vpnclient/interceptor.c: In function &#8216;interceptor_init&#8217;:              
/home/micio/Scaricati/vpnclient/interceptor.c:140: warning: assignment discards qualifiers from pointer target type
  CC [M]  /home/micio/Scaricati/vpnclient/linuxkernelapi.o                                                         
  LD [M]  /home/micio/Scaricati/vpnclient/cisco_ipsec.o                                                            
  Building modules, stage 2.                                                                                       
  MODPOST 1 modules                                                                                                
WARNING: could not find /home/micio/Scaricati/vpnclient/.libdriver64.so.cmd for /home/micio/Scaricati/vpnclient/libdriver64.so
  CC      /home/micio/Scaricati/vpnclient/cisco_ipsec.mod.o
  LD [M]  /home/micio/Scaricati/vpnclient/cisco_ipsec.ko
make[1]: uscita dalla directory «/usr/src/linux-headers-2.6.31-14-generic»
Copying module to directory "/lib/modules/2.6.31-14-generic/CiscoVPN".
Already have group 'bin'

Creating start/stop script "/etc/init.d/vpnclient_init".
    /etc/init.d/vpnclient_init
Enabling start/stop script for run level 3,4 and 5.
Creating global config /etc/opt/cisco-vpnclient

Installing license.txt (VPN Client license) in "/opt/cisco-vpnclient/":
    /opt/cisco-vpnclient/license.txt

Installing bundled user profiles in "/etc/opt/cisco-vpnclient/Profiles/":
* New Profiles     : sample

Copying binaries to directory "/opt/cisco-vpnclient/bin".
Adding symlinks to "/usr/local/bin".
    /opt/cisco-vpnclient/bin/vpnclient
    /opt/cisco-vpnclient/bin/cisco_cert_mgr
    /opt/cisco-vpnclient/bin/ipseclog
Copying setuid binaries to directory "/opt/cisco-vpnclient/bin".
    /opt/cisco-vpnclient/bin/cvpnd
Copying libraries to directory "/opt/cisco-vpnclient/lib".
    /opt/cisco-vpnclient/lib/libvpnapi.so
Copying header files to directory "/opt/cisco-vpnclient/include".
    /opt/cisco-vpnclient/include/vpnapi.h

Setting permissions.
    /opt/cisco-vpnclient/bin/cvpnd (setuid root)
    /opt/cisco-vpnclient (group bin readable)
    /etc/opt/cisco-vpnclient (group bin readable)
    /etc/opt/cisco-vpnclient/Profiles (group bin readable)
    /etc/opt/cisco-vpnclient/Certificates (group bin readable)
* You may wish to change these permissions to restrict access to root.
* You must run "/etc/init.d/vpnclient_init start" before using the client.
* This script will be run AUTOMATICALLY every time you reboot your computer.
root@shadow:~/Scaricati/vpnclient# vpnclient
bash: /usr/local/bin/vpnclient: Nessun file o directory
root@shadow:~/Scaricati/vpnclient# /etc/init.d/vpnclient_init start
Starting /opt/cisco-vpnclient/bin/vpnclient: Done
root@shadow:~/Scaricati/vpnclient# vpnclient
bash: /usr/local/bin/vpnclient: Nessun file o directory
root@shadow:~/Scaricati/vpnclient# lsmod | grep cisco
cisco_ipsec           590344  0
 

```
```
micio@shadow:~/Scaricati/vpnclient$ ls -l /usr/local/bin/
totale 0
lrwxrwxrwx 1 root root 39 2009-11-01 13:04 cisco_cert_mgr -> /opt/cisco-vpnclient/bin/cisco_cert_mgr
lrwxrwxrwx 1 root root 33 2009-11-01 13:04 ipseclog -> /opt/cisco-vpnclient/bin/ipseclog
lrwxrwxrwx 1 root root 34 2009-11-01 13:04 vpnclient -> /opt/cisco-vpnclient/bin/vpnclient
micio@shadow:~/Scaricati/vpnclient$ls -l /opt/cisco-vpnclient/bin/
totale 4224
-rwxrwxrwx 1 root bin 1241184 2009-11-01 13:04 cisco_cert_mgr
-rwxrwxrwx 1 root bin 2181944 2009-11-01 13:04 cvpnd
-rwxrwxrwx 1 root bin  226700 2009-11-01 13:04 ipseclog
-rwxrwxrwx 1 root bin  666260 2009-11-01 13:04 vpnclient
micio@shadow:~/Scaricati/vpnclient$

```
Any suggestion? Why system can't find executable?

Thanks in advance!

Micio

---

### Post by Boynas on 2009-11-02
I have the same problem...

How did you install vpnclient?

---

### Post by Boynas on 2009-11-02
Ok my friend, I got it to work by installing lsb-core from synaptic.

Apparently there were some libraries missing. The whole problem is that we are using 64 bit, and this cisco crap is really 32 patched to compile on 64 archs... 

I am not an expert, and I can not give you more details but if you install the missing libraries from Linux Standard Base, it will probably work.

```
sudo apt-get install lsb-core
``` 

that should work too...

---

### Post by micio on 2009-11-02
> **Boynas said:**
> I have the same problem...

How did you install vpnclient?

I followed a guide from LAMNK or something similar..

However i got it solved by using an ext3 fs, but now when I go into vpn my workstation dump because of SMP.. in other words it not support multicore CPU and the only way I have to make it work is turn off other cores..
Too annoying issue for me so I switch to kvpnc.. 
Cheers

Micio

---

### Post by micio on 2009-11-02
> **Boynas said:**
> Ok my friend, I got it to work by installing lsb-core from synaptic.

Apparently there were some libraries missing. The whole problem is that we are using 64 bit, and this cisco crap is really 32 patched to compile on 64 archs... 

I am not an expert, and I can not give you more details but if you install the missing libraries from Linux Standard Base, it will probably work.

```
sudo apt-get install lsb-core
``` 

that should work too...

I will try...

Thanks

Micio

---

### Post by Rusty_1 on 2009-11-03
I found the following link quote useful to get the vpnclient installed. As I stilled expierenced errors after following the intial step in this thread of installing the lsb-core libs.

[http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/](http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/).


Just an update. After installing the client I still have an issue of the VPN Client hangs and looses the session after a couple of seconds of authenticating. This is not an SMP issue since I disable the one CPU. Still looking into this further.

---

