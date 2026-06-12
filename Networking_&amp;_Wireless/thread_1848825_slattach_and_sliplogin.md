---
title: "slattach and sliplogin"
date: 2011-09-23
forum: Networking &amp; Wireless
---

### Post by TSorcerer on 2011-09-23
I am currently trying to tunnel TCP/IP traffic over a serial null modem cable. I'm doing this because I do not have any (available) network interfaces on my "server" machine, but require a authentic ssh connection (simple terminal emulation will not work for me, sadly).

There does not seem to be a package in ubuntu / debian that provides sliplogin though. I was able to find a source tarball for slackware ([http://vesta.informatik.rwth-aachen.de/ftp/pub/comp/Linux/slackware/slackware-8.0/pasture/pasture-sources/sliplogin-2.1.1/sliplogin-2.1.1.tar.gz](http://vesta.informatik.rwth-aachen.de/ftp/pub/comp/Linux/slackware/slackware-8.0/pasture/pasture-sources/sliplogin-2.1.1/sliplogin-2.1.1.tar.gz)), but I wasn't able to get it to compile. I found a blogpost that explained to replace the -m486 switch with -mtune=i486 which helped to fix one of the issues, but I now get even more error messages that I am not able to fix:


```
gcc -O2 -pipe -fomit-frame-pointer -mtune=i486  -DSLIPPATH=\"/etc/slip\" -DESLIPLOGIN -DESLIP_AUTO -c sliplogin.c
sliplogin.c: In function ‘exit_sliplogin’:
sliplogin.c:183: error: invalid use of undefined type ‘struct enet_statistics’
sliplogin.c:183: error: invalid use of undefined type ‘struct enet_statistics’
sliplogin.c: In function ‘main’:
sliplogin.c:223: error: ‘environ’ undeclared (first use in this function)
sliplogin.c:223: error: (Each undeclared identifier is reported only once
sliplogin.c:223: error: for each function it appears in.)
sliplogin.c:277: warning: assignment makes pointer from integer without a cast
sliplogin.c:284: error: dereferencing pointer to incomplete type
make: *** [sliplogin.o] Error 1

```

Can anyone help me out in some way? Either point me in a direction on how I might be able to fix this issue or provide me a link to a tarball that will compile or even a binary .deb package.

Thanks alot!

---

### Post by TSorcerer on 2011-09-29
Ok, I managed to get it to work without sliplogin, which is apparently not required for what I wanted.

[These easy steps](http://www.ott.net/knowledge/tcpip-nullmodem/) setup TCP/IP over a serial line. You can improve those steps by adding pre-up and post-down rules to your /etc/network/interfaces file to auto slattach, whenever your interfaces go up and down.

Best regards,
Daniel

---

