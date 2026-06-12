---
title: "intel 3945abg unusable upgrading from hardy to intrepid"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by Nareto on 2009-02-26
Hello, i found much of this on the web, many bug reports and forum threads but actually i still haven't been able to solve the problem, which is on an Acer Aspire 5630, currently, because of this very issue, unable to being easily connected to the internet. I'm copying output of commands "by hand" on another computer - if more precise output is needed please ask i'll somehow get it 

So here it is:

Upgrading from hardy to intrepid has brought up this problem (which seems to be common): at boot the computer stops for approximately 2 minutes on "Congiguring network interfaces" then boots up (normally it seems). This is totally indipendent of the hardware switch for the wireless card.

In gnome, clicking on nm-applet gives me greyed out menu (where usually i would see avaiable networks) saying: device is unmanaged.

"sudo ifconfig wmaster0 up" gives "SIOCSIFFLAGS: Operation not supported" but, if i try "sudo ifconfig eth1 up" (note that eth1 and wmaster0 in ifconfig have the same hwaddr) both eth1 and wmaster0 go up, then
sudo ifconfig eth1 192.168.2.13 
works but finally 
sudo dhclient eth1
complains with "wmaster0: unknown hardware address type 801" , then makes several useless attempts of connecting to my router

in various places, i have found and tried (unsuccessfully):
- installing linux-backports-modules-2.6.27-11-generic
- sudo rmmod iwl3945 and then sudo modprobe iwl3945
- disabling and renabling "Enable Wireless" option in nm-applet (right click)

kernel is 2.6.27-11; modinfo iwl3945 gives version: 1.2.26ks; wifi card, as in subject, is 3945ABG [Golan] rev 02

what could be the problem? 
Is there a patch for compiling ipw3945 with this kernel? 
Alternatively would reinstalling an older kernel work (i'm not concerned of having the latest kernel, just want it working)?

---

### Post by nixscripter on 2009-02-27
I would explain one thing first: wireless card interfaces are split in half: eth1 is the local endpoint, wmaster0 is the remote one. There are always both of them, and eth1 is the one of interest.

Try this:

```
sudo ifconfig eth1 up
sudo iwlist eth1 scan
```

This is a basic check to make sure it thinks it's a wireless device.

I would also add that, as for drivers, the ipw3945 requires firmware; I got an Ubuntu-pre-installed Dell, so I don't know if that's publicly available.

---

### Post by Nareto on 2009-03-02
thank you for the reply. I reinstalled Intrepid from scratch and it is now misteriously working... i locked the kernel version (prior to 2.6.24 thus i think using ipw) to be safe

---

### Post by nixscripter on 2009-03-02
Glad to hear it. Please mark the thread as solved (under the thread tools menu).

---

