---
title: "bcmwl-kernel-source issues"
date: 2012-07-16
forum: Networking &amp; Wireless
---

### Post by Bellomo on 2012-07-16
Hi all,

I have been looking around for quite a while as far as these n300 adapter and use with bcmwl kernels, however I'm having quite a bit of trouble installing the package. 
both
```
sudo dpkg --configure bcmwl-kernel-source
```
and
```
apt-get install bcmwl-kernel-source
```
return the same error, after freshly apt-get update, and upgrading.


root@bt:~# sudo dpkg --configure bcmwl-kernel-source
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Removing old bcmwl-5.60.48.36+bdcom DKMS files...

------------------------------
Deleting module version: 5.60.48.36+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.2.6
Building for architecture i686
Building initial module for 3.2.6

Error! Bad return status for module build on kernel: 3.2.6 (i686)
Consult the make.log in the build directory
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 bcmwl-kernel-source

Looking into it further, the referenced make.log consists of this:

DKMS make.log for bcmwl-5.60.48.36+bdcom for kernel 3.2.6 (i686)
Mon Jul 16 18:48:40 NZST 2012
make: Entering directory `/usr/src/linux-source-3.2.6'
  LD      /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/shared/linux_osl.o
  CC [M]  /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/wl/sys/wl_linux.o
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/wl/sys/wl_linux.c:219: error: unknown field ‘ndo_set_multicast_list’ specified in initializer
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/wl/sys/wl_linux.c:219: warning: initialization from incompatible pointer type
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/wl/sys/wl_linux.c: In function ‘_wl_set_multicast_list’:
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/wl/sys/wl_linux.c:1435: error: ‘struct net_device’ has no member named ‘mc_list’
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/wl/sys/wl_linux.c:1435: error: ‘struct net_device’ has no member named ‘mc_count’
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/wl/sys/wl_linux.c:1436: error: dereferencing pointer to incomplete type
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/wl/sys/wl_linux.c:1442: error: dereferencing pointer to incomplete type
make[1]: *** [/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/wl/sys/wl_linux.o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-source-3.2.6'

I was able to get the device working for a short while, utilising either b43 or b43legacy (I've tried both), but since neither natively supported injection/mon0 I tried to patch with the b43 injection patch. Needless to say that hasn't worked (yet) and I'm left with this error and a not working wireless adapter.

lsusb does show it, however.

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


I'm a bit stuck, and would appreciate some help in getting this solved, if there is a solution :)

==================

---

### Post by chili555 on 2012-07-16
> ID [COLOR="Red"]0846:9020[/COLOR] NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]Search this forum for the highlighted usb.id and you'll see that the only way to get this device working is ndiswrapper. If your system is 64-bit, you may not get it working at all. I doubt that ndiswrapper supports injection, aircrack, etc. 

I have no knowledge of injection and aircrack and will not get any. If you want to simply connect, I'll be happy to help. I don't know how you could get this device to work with b43/ssb and firmware. The usb.id is not mentioned in the aliases. 

I am not sure why bcmwl-kernel-source errored out, however since it is also incorrect for your device, it probably is moot.> chili@LAPTOP60:~$ modinfo wl
filename:       /lib/modules/3.2.0-26-generic-pae/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     D9C86A9C5C3D22E103EF402
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*  [COLOR="Red"]<---No 0846:9020 here[/COLOR]
alias:          pci:v000014E4d0000435Asv*sd*bc*sc*i*  [COLOR="Red"]<---Only 14e4:xxxx here[/COLOR]
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A99Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
depends:        lib80211
vermagic:       3.2.0-26-generic-pae SMP mod_unload modversions 686 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           name:string


---

