---
title: "Getting symbol version mismatch in the cdc_ether driver"
date: 2012-11-29
forum: Networking &amp; Wireless
---

### Post by guppi278 on 2012-11-29
Hi,
 I am building a new loadable kernel module similar to usbnet.
 i am reusing all the functionality of usbnet and and on top of that will have my own specific features ( for one of the demo project i am working at my organization).

 i was able to create the module based on my code changes and was successfully able to run with a ECM based modem( which would use cdc_ether as minidriver). 

 But recently, i added some new functionality in the usbnet driver and when i load the module ,it loads successfully. However, as soon as i insert my ECM modem device, i start getting the following errors:


[ 8949.900137] usb 2-1: new high speed USB device using ehci_hcd and address 22
[ 8950.084835] cdc_ether: disagrees about version of symbol usbnet_get_ethernet_addr
[ 8950.084845] cdc_ether: Unknown symbol usbnet_get_ethernet_addr (err -22)
[ 8950.085155] cdc_ether: disagrees about version of symbol usbnet_suspend
[ 8950.085162] cdc_ether: Unknown symbol usbnet_suspend (err -22)
[ 8950.085584] cdc_ether: disagrees about version of symbol usbnet_get_endpoints
[ 8950.085591] cdc_ether: Unknown symbol usbnet_get_endpoints (err -22)
[ 8950.086254] cdc_ether: disagrees about version of symbol usbnet_disconnect
[ 8950.086261] cdc_ether: Unknown symbol usbnet_disconnect (err -22)
[ 8950.086477] cdc_ether: disagrees about version of symbol usbnet_probe
[ 8950.086484] cdc_ether: Unknown symbol usbnet_probe (err -22)
[ 8950.086792] cdc_ether: disagrees about version of symbol usbnet_resume
[ 8950.086798] cdc_ether: Unknown symbol usbnet_resume (err -22)


i am not sure why the cdc_ether is unable to get the correct usbnet symbols  versions even when i have compiled my usbnet module with the same kernel version which is installed.


the compiler version is also same as i use in my Makefile.

cat /proc/version
Linux version 2.6.38-13-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #56-Ubuntu SMP Tue Feb 14 12:40:40 UTC 2012

Makefile:

obj-m := usbnet_sid.o
usbnet-objs := usbnet_sid.o
ccflags-y := -g
ccflags-y += -DEBUG
KDIR := /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)
OUTPUTDIR=/lib/modules/`uname -r`/kernel/drivers/net/usb/

all: clean
        $(MAKE) -C $(KDIR) M=$(PWD) modules

install: all
        cp -f usbnet_sid.ko $(OUTPUTDIR)
        depmod -a

clean:
        rm -rf *.o *~ core .depend .*.cmd *.ko *.mod.c .tmp_versions Module.* modules.order


Can someone please help me answering this.

regards
Sid

---

### Post by guppi278 on 2012-11-29
I figured it out that its neither the compiler version, or kernel version or adding new flags to Makefile that is causing the issue.

I reverted my changes to an older version of my src files( keeping the same compiler , kernel and Makefile) and with that i don't see any symbol mismatch for cdc_ether.

Why after my latest changes, cdc_ether is complaining about the symbol version mismatch.

i did not change any of the below functions that cdc_ether looks for in usbnet, namely the below:

static struct usb_driver cdc_driver = {
	.name =		"cdc_ether",
	.id_table =	products,
	.probe =	usbnet_probe,
	.disconnect =	usbnet_disconnect,
	.suspend =	usbnet_suspend,
	.resume =	usbnet_resume,
	.reset_resume =	usbnet_resume,

---

### Post by guppi278 on 2012-11-30
Ok, i figured out that the version mismatch is happening whenever i include either of the below header files:

<linux/udp.h>
<linux/tcp.h>

there is no issue when i include <linux/ip.h>

Can someone please point me why this is the case.
it blocking all my development.

appreciate any response in this regard from Linux experts

regards
Sid

---

