---
title: "catman mode error"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by kalpesh on 2010-03-03
user@ubuntu:~/Downloads/e1000e-1.1.2.1a/src$ sudo make install
[sudo] password for user: 
make -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/user/Downloads/e1000e-1.1.2.1a/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
# remove all old versions of the driver
find /lib/modules/2.6.31-14-generic -name e1000e.ko -exec rm -f {} \; || true
find /lib/modules/2.6.31-14-generic -name e1000e.ko.gz -exec rm -f {} \; || true
install -D -m 644 e1000e.ko /lib/modules/2.6.31-14-generic/kernel/drivers/net/e1000e/e1000e.ko
/sbin/depmod -a || true
install -D -m 644 e1000e.7.gz /usr/share/man/man7/e1000e.7.gz
man -c -P'cat > /dev/null' e1000e || true
man: 
cannot write to /var/cache/man/cat7/e1000e.7.gz in catman mode
e1000e.

I have saw some post on this error but cant get it how to get rid of it error is still up coming
I have checked cat7 dir its empty
what else i do 


What is catman mode?
because I am trying to install this drivers since 2 years with every new release of ubuntu. And its still same problem

plz help to solve this problem this time

---

