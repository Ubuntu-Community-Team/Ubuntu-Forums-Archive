---
title: "Wired Ethernet in AOD250"
date: 2009-09-05
forum: Networking &amp; Wireless
---

### Post by jdglover on 2009-09-05
Hi,

I've been try to install the driver for the wired network card on an Acer AOD250, following the guidance given on the AOD250 Community page. Everything goes well until the make install command, and i get this output:

john@aspire:~/atheros/src$ sudo make install
make -C /lib/modules/2.6.28-15-generic/build SUBDIRS=/home/john/atheros/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
# remove all old versions of the driver
find /lib/modules/2.6.28-15-generic -name atl1e.ko -exec rm -f {} \; || true
find /lib/modules/2.6.28-15-generic -name atl1e.ko.gz -exec rm -f {} \; || true
install -D -m 644 atl1e.ko /lib/modules/2.6.28-15-generic/kernel/drivers/net/atl1e/atl1e.ko
/sbin/depmod -a || true
install -D -m 644 atl1e.7.gz /usr/share/man/man7/atl1e.7.gz
man -c -P'cat > /dev/null' atl1e || true
man: 
cannot write to /var/cache/man/cat7/atl1e.7.gz in catman mode
atl1e.

I'm assuming that the last line "cannot write to..." is a problem as the driver never installs and the wired card is not visible or enabled. So, is there something else i need to be doing to get this to work?  I'm following the instructions posted here:

[https://help.ubuntu.com/community/AspireOneAOD250#Install%20Wired%20Network%20Driver](https://help.ubuntu.com/community/AspireOneAOD250#Install%20Wired%20Network%20Driver)

Any help would be appreciated.  Thanks!

john

---

