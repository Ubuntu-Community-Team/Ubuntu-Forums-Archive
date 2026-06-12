---
title: "OpenVPN bridge question"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by hugetivofan on 2010-12-04
Hi, have an openvpn bridge up and running (ubuntu to ubuntu, both in vmware fusion machines on macs).  my problem is that i cant get a connection faster than ~9mbps even though 20+mbps is available.  ive been troubleshooting for a while and have tried many fixes.  i just now did ethtool tap0 and i think maybe i found it.  it says the link is 10mbps.  i tried to change it with:

sudo ethtool -s tap0 speed 100

but it says ethtool cant change speed on tap0.  How can i define the link speed of tap0?  Many thanks for any help.

---

### Post by hugetivofan on 2011-01-03
bump - anyone out there with a suggestion?

---

### Post by PatchesTheCaveman on 2011-01-03
Your connection is being limited by VMware, not Ubuntu:
[http://kb.vmware.com/kb/1002456](http://kb.vmware.com/kb/1002456)

---

### Post by hugetivofan on 2011-01-03
Thanks for the reply.  I am having trouble installing vmxnet3 driver using vmware tools and config.  here is the output when i run vmware tools config - I did some googling and it seems like this is a problem others have encountered, but I am not sure how to fix it.  Any help would be appreciated!

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmxnet-only'
make -C /lib/modules/2.6.35-22-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /tmp/vmware-root/modules/vmxnet-only/vmxnet.o
/tmp/vmware-root/modules/vmxnet-only/vmxnet.c: In function ‘vmxnet_load_multicast’:
/tmp/vmware-root/modules/vmxnet-only/vmxnet.c:2795: error: ‘struct net_device’ has no member named ‘mc_list’
/tmp/vmware-root/modules/vmxnet-only/vmxnet.c:2805: error: ‘struct net_device’ has no member named ‘mc_count’
/tmp/vmware-root/modules/vmxnet-only/vmxnet.c:2806: error: dereferencing pointer to incomplete type
/tmp/vmware-root/modules/vmxnet-only/vmxnet.c:2807: error: dereferencing pointer to incomplete type
make[2]: *** [/tmp/vmware-root/modules/vmxnet-only/vmxnet.o] Error 1
make[1]: *** [_module_/tmp/vmware-root/modules/vmxnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [vmxnet.ko] Error 2
make: Leaving directory `/tmp/vmware-root/modules/vmxnet-only'

The fast network device driver (vmxnet module) is used only for our fast 
networking interface. The rest of the software provided by VMware Tools is 
designed to work independently of this feature.
If you wish to have the fast network driver enabled, you can install the driver
by running vmware-config-tools.pl again after making sure that gcc, binutils, 
make and the kernel sources for your running kernel are installed on your 
machine. These packages are available on your distribution's installation CD.

---

