---
title: "Racoon install issue"
date: 2006-06-24
forum: Networking &amp; Wireless
---

### Post by otis166 on 2006-06-24
Hi,

I'm having an issue getting racoon installed.  I installed ipsec-tools and modutils ok.  When I tried to install Racoon I get this error:
Unpacking racoon (from .../racoon_1%3a0.6.5-4ubuntu1_i386.deb) ...
Setting up racoon (0.6.5-4ubuntu1) ...
Loading IPSEC/crypto modules...
insmod: error inserting '/lib/modules/2.6.15-25-k7/kernel/crypto/crc32c.ko': -1 Unknown symbol in module
insmod: error inserting '/lib/modules/2.6.15-25-k7/kernel/net/ipv6/ipcomp6.ko': -1 Unknown symbol in module
IPSEC/crypto modules loaded.
Starting IKE (ISAKMP/Oakley) server: racoon: failed to parse configuration file.racoon-tool: racoon did not start.
invoke-rc.d: initscript racoon, action "start" failed.
dpkg: error processing racoon (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 racoon
E: Sub-process /usr/bin/dpkg returned an error code (1)

I'm running 2.6.15-25-k7 for the kernel on Ubuntu 6.06. 

Thanks.

---

### Post by Palijn on 2006-07-05
Hello,

I'm having apparently the same problem on a slightly different kernel:

Setting up racoon (0.6.5-4ubuntu1) ...
Loading IPSEC/crypto modules...
insmod: error inserting '/lib/modules/2.6.15-25-686/kernel/crypto/crc32c.ko': -1 Unknown symbol in module
IPSEC/crypto modules loaded.
Starting IKE (ISAKMP/Oakley) server: racoon: failed to parse configuration file.racoon-tool: racoon did not start.
invoke-rc.d: initscript racoon, action "start" failed.

Is it that the Ubuntu build of the kernel modules is actually broken, or is it something on my system that prevents crc32c.ko to load ?

---

### Post by MrDomino on 2006-07-13
I'm encountering this problem as well on kernel 2.6.15-26-686.

---

### Post by ephoenix on 2006-07-14
There's a bug confirmed on launchpad on that.

[https://launchpad.net/distros/ubuntu/+source/racoon/+bug/44246](https://launchpad.net/distros/ubuntu/+source/racoon/+bug/44246)

We are waiting for that fix to try to get it worked with Nortel Contivity switch...

---

