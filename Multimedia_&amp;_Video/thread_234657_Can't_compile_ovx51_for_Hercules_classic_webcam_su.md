---
title: "Can't compile ovx51 for Hercules classic webcam support"
date: 2006-08-11
forum: Multimedia &amp; Video
---

### Post by extremecarver on 2006-08-11
Hi can someone please tell me where there is the error?

```
root@felix-laptop:/home/felix/ovx51# make
make -C /lib/modules/2.6.17-beyond3/build M=/home/felix/ovx51 modules
make[1]: Entering directory `/usr/src/linux-2.6.17'
  CC [M]  /home/felix/ovx51/ov51x.o
/home/felix/ovx51/ov51x.c:246: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:246: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:246: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:246: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:248: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:248: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:248: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:248: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:250: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:250: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:250: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:250: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:252: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:252: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:252: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:252: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:255: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:255: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:255: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:255: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:259: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:259: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:259: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:259: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:262: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:262: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:262: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:262: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:266: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:266: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:266: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:266: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:268: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:268: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:268: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:268: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:270: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:270: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:270: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:270: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:273: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:273: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:273: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:273: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:275: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:275: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:275: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:275: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:278: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:278: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:278: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:278: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:281: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:281: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:281: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:281: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:283: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:283: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:283: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:283: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:285: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:285: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:285: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:285: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:287: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:287: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:287: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:287: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:289: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:289: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:289: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:289: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:291: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:291: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:291: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:291: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:293: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:293: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:293: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:293: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:295: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:295: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:295: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:295: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:297: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:297: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:297: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:297: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:299: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:299: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:299: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:299: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:301: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:301: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:301: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:301: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:303: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:303: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:303: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:303: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:306: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:306: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:306: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:306: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:309: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:309: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:309: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:309: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:311: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:311: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:311: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:311: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:313: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:313: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:313: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:313: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:315: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:315: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:315: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:315: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:317: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:317: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:317: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:317: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:319: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:319: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:319: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:319: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:321: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:321: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:321: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:321: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:324: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:324: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:324: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:324: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:327: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:327: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:327: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:327: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:329: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:329: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:329: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:329: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:331: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:331: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:331: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:331: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:333: error: syntax error before string constant
/home/felix/ovx51/ov51x.c:333: warning: type defaults to ‘int’ in declaration of ‘MODULE_PARM’
/home/felix/ovx51/ov51x.c:333: warning: function declaration isn’t a prototype
/home/felix/ovx51/ov51x.c:333: warning: data definition has no type or storage class
/home/felix/ovx51/ov51x.c:8562: error: unknown field ‘owner’ specified in initializer
/home/felix/ovx51/ov51x.c:8562: warning: initialization from incompatible pointer type
make[2]: *** [/home/felix/ovx51/ov51x.o] Error 1
make[1]: *** [_module_/home/felix/ovx51] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.17'
make: *** [all] Error 2
root@felix-laptop:/home/felix/ovx51#

```

---

### Post by extremecarver on 2006-08-11
I tried to install it on standard ubuntu kernel (though that sucks as many other things are not usable for me then anymore - I will try to compile it for standard kernel and then boot it with my 2.6.17beyond3 in which I enabled load support for modules not configured for the kernel itself)

So here is the next unsolvable error for me at the moment:

FATAL: Error inserting ov519_decomp (/lib/modules/2.6.15-26-386/extra/ov519_decomp.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Dmesg

[17179758.512000] /home/felix/ov51x-jpeg-0.5/ov51x.c: USB OV519 video device found
[17179758.868000] /home/felix/ov51x-jpeg-0.5/ov51x.c: Sensor is an OV7648
[17179758.980000] /home/felix/ov51x-jpeg-0.5/ov51x.c: Device at usb-0000:00:1d.2-1 registered to minor 0
[17179758.980000] usbcore: registered new driver ov51x
[17179758.980000] /home/felix/ov51x-jpeg-0.5/ov51x.c: v1.65-1.11-mark : ov51x USB Camera Driver
[17179776.464000] usbcore: registered new driver ov511
[17179776.464000] drivers/usb/media/ov511/ov511.c: v1.64 for Linux 2.5 : ov511 USB Camera Driver
[17179776.464000] ov519_decomp: disagrees about version of symbol ov511_deregister_decomp_module
[17179776.464000] ov519_decomp: Unknown symbol ov511_deregister_decomp_module
[17179776.464000] ov519_decomp: disagrees about version of symbol ov511_register_decomp_module
[17179776.464000] ov519_decomp: Unknown symbol ov511_register_decomp_module
[17179942.880000] /home/felix/ov51x-jpeg-0.5/ov51x.c: No decompressor available
[17179986.392000] /home/felix/ov51x-jpeg-0.5/ov51x.c: No decompressor available
[17180075.436000] ov519_decomp: disagrees about version of symbol ov511_deregister_decomp_module
[17180075.436000] ov519_decomp: Unknown symbol ov511_deregister_decomp_module
[17180075.436000] ov519_decomp: disagrees about version of symbol ov511_register_decomp_module
[17180075.436000] ov519_decomp: Unknown symbol ov511_register_decomp_module
[17180094.328000] /home/felix/ov51x-jpeg-0.5/ov51x.c: No decompressor available
[17180229.428000] ov519_decomp: disagrees about version of symbol ov511_deregister_decomp_module
[17180229.428000] ov519_decomp: Unknown symbol ov511_deregister_decomp_module
[17180229.428000] ov519_decomp: disagrees about version of symbol ov511_register_decomp_module
[17180229.428000] ov519_decomp: Unknown symbol ov511_register_decomp_module
[17180382.260000] usb 5-7: new high speed USB device using ehci_hcd and address 5
[17180389.168000] /home/felix/ov51x-jpeg-0.5/ov51x.c: No decompressor available
[17180397.140000] usb 5-7: USB disconnect, address 5
[17180559.908000] ov519_decomp: disagrees about version of symbol ov511_deregister_decomp_module
[17180559.908000] ov519_decomp: Unknown symbol ov511_deregister_decomp_module
[17180559.908000] ov519_decomp: disagrees about version of symbol ov511_register_decomp_module
[17180559.908000] ov519_decomp: Unknown symbol ov511_register_decomp_module
[17180609.064000] ov519_decomp: disagrees about version of symbol ov511_deregister_decomp_module
[17180609.064000] ov519_decomp: Unknown symbol ov511_deregister_decomp_module
[17180609.064000] ov519_decomp: disagrees about version of symbol ov511_register_decomp_module
[17180609.064000] ov519_decomp: Unknown symbol ov511_register_decomp_module
[17180989.548000] ov519_decomp: disagrees about version of symbol ov511_deregister_decomp_module
[17180989.548000] ov519_decomp: Unknown symbol ov511_deregister_decomp_module
[17180989.548000] ov519_decomp: disagrees about version of symbol ov511_register_decomp_module
[17180989.548000] ov519_decomp: Unknown symbol ov511_register_decomp_module

---

### Post by extremecarver on 2006-08-12
Solved.

I didn't use uptodate drivers from ov51x. With the newest driver it compiled easily. Using my custom kernel I didn't even have to hack around like with standard ubuntu kernel.

---

