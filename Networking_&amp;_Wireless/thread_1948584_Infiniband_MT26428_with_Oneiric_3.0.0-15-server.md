---
title: "Infiniband MT26428 with Oneiric 3.0.0-15-server"
date: 2012-03-28
forum: Networking &amp; Wireless
---

### Post by anothracc on 2012-03-28
Hi everyone, this is my first significant post:  fingers crossed!

I have a set of Dell machines with infiniband MT26428 cards.  Try as I might I cannot bring the cards up to present an interface.  I have tried three approaches:

1)  Instructions at [http://www.mindwerks.net/2011/02/infiniband-on-ubuntu-10-10-meerkat/comment-page-1/#comment-2546](http://www.mindwerks.net/2011/02/infiniband-on-ubuntu-10-10-meerkat/comment-page-1/#comment-2546)

This worked ok (with the latest file from openfabrics) but the command,

LD_PRELOAD=libsdp.so iperf -s

gives me an error,

ERROR: ld.so: object 'libsdp.io' from LD_PRELOAD cannot be preloaded: ignored.

and, as I noted on the page I do not know how to proceed to generate an interface I can use.

2)  Instructions at

[http://www.lucubration.com/open-source-projects/ubuntu-infiniband-ipoib.html](http://www.lucubration.com/open-source-projects/ubuntu-infiniband-ipoib.html)

I didn't use rpm to install, however.  I used, for example,

$ rpm2cpio infiniband-diags-1.5.12-1.src.rpm | cpio -idmv
$ tar xf infiniband-diags-1.5.12.tar.gz
$ cd infiniband-diags-1.5.12/
$ ./configure
$ make
$ sudo make install

on the rpm files pertaining to libibcommon, libibumad, libibmad, opensm, and infiniband-diags.  This seemed to work ok.  I added,

ib_mthca
ib_ipoib
ib_sdp
ib_sa
ib_cm
ib_umad
ib_addr
ib_uverbs
ib_ipath
ib_qib

to /etc/modules.  I added, 

auto ib0
iface ib0 inet static
address 192.168.1.1
netmask 255.255.255.0

to /etc/network/interfaces and reset.  No new interface occurred with ifconfig.

3)  I tried (on a fresh machine) to install opensm from the repositories.  This looked promising but still no interface and
opensm generates the output:

-------------------------------------------------
OpenSM 3.2.6_20090317
Command Line Arguments:
 Log File: /var/log/opensm.log
-------------------------------------------------
OpenSM 3.2.6_20090317

Entering DISCOVERING state


No local ports detected!

Error from osm_opensm_bind (0x2A)
Perhaps another instance of OpenSM is already running
Exiting SM

All of my attempts produce this output from opensm:
that it cannot find a local port.  

The card is present:  lspci output includes...

06:00.0 InfiniBand: Mellanox Technologies MT26428 [ConnectX VPI PCIe 2.0 5GT/s - IB QDR / 10GigE] (rev b0)


Please!  Someone help me!  I'm going bald here.....

Best regards,

Mark.

---

### Post by anothracc on 2012-03-28
I found this in the meantime:

[http://ubuntuforums.org/showthread.php?t=1051835](http://ubuntuforums.org/showthread.php?t=1051835)

---

### Post by StOlEnDeStInY on 2013-03-18
> **anothracc said:**
> Hi everyone, this is my first significant post:  fingers crossed!

I have a set of Dell machines with infiniband MT26428 cards.  Try as I might I cannot bring the cards up to present an interface.  I have tried three approaches:

1)  Instructions at [http://www.mindwerks.net/2011/02/infiniband-on-ubuntu-10-10-meerkat/comment-page-1/#comment-2546](http://www.mindwerks.net/2011/02/infiniband-on-ubuntu-10-10-meerkat/comment-page-1/#comment-2546)

This worked ok (with the latest file from openfabrics) but the command,

LD_PRELOAD=libsdp.so iperf -s

gives me an error,

ERROR: ld.so: object 'libsdp.io' from LD_PRELOAD cannot be preloaded: ignored.

and, as I noted on the page I do not know how to proceed to generate an interface I can use.

2)  Instructions at

[http://www.lucubration.com/open-source-projects/ubuntu-infiniband-ipoib.html](http://www.lucubration.com/open-source-projects/ubuntu-infiniband-ipoib.html)

I didn't use rpm to install, however.  I used, for example,

$ rpm2cpio infiniband-diags-1.5.12-1.src.rpm | cpio -idmv
$ tar xf infiniband-diags-1.5.12.tar.gz
$ cd infiniband-diags-1.5.12/
$ ./configure
$ make
$ sudo make install

on the rpm files pertaining to libibcommon, libibumad, libibmad, opensm, and infiniband-diags.  This seemed to work ok.  I added,

ib_mthca
ib_ipoib
ib_sdp
ib_sa
ib_cm
ib_umad
ib_addr
ib_uverbs
ib_ipath
ib_qib

to /etc/modules.  I added, 

auto ib0
iface ib0 inet static
address 192.168.1.1
netmask 255.255.255.0

to /etc/network/interfaces and reset.  No new interface occurred with ifconfig.

3)  I tried (on a fresh machine) to install opensm from the repositories.  This looked promising but still no interface and
opensm generates the output:

-------------------------------------------------
OpenSM 3.2.6_20090317
Command Line Arguments:
 Log File: /var/log/opensm.log
-------------------------------------------------
OpenSM 3.2.6_20090317

Entering DISCOVERING state


No local ports detected!

Error from osm_opensm_bind (0x2A)
Perhaps another instance of OpenSM is already running
Exiting SM

All of my attempts produce this output from opensm:
that it cannot find a local port.  

The card is present:  lspci output includes...

06:00.0 InfiniBand: Mellanox Technologies MT26428 [ConnectX VPI PCIe 2.0 5GT/s - IB QDR / 10GigE] (rev b0)


Please!  Someone help me!  I'm going bald here.....

Best regards,

Mark.


Hi Mark,

Were you able to find a solution to the LD_PRELOAD problem? After almost an year, I am having the same problem with libsdp.so file.

---

### Post by anothracc on 2013-03-19
Hi stolendestiny,

In short, no.  I had some feedback from Mellanox who suggested OFED-1.5 could be made to run on Ubuntu by performing:

Install rpm, linux-headers-2.6.28-15-server bison flex pciutils-dev tk tcl8.4dev tk8.4dev

Then,

./install.pl --all --without-depcheck -s /usr/src/linux-headers-2.6.28-15-server

... but I had problems and got pulled away from the cluster before I had a chance to try more.

Please, if you get it working, can you post back?

Best regards,

Mark.

---

