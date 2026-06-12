---
title: "OSS Driver for AES16 causes modprobe oops"
date: 2007-10-08
forum: Multimedia &amp; Video
---

### Post by djshorter on 2007-10-08
I've tried installing a OSS v4.0 Build 1006 driver (LynxTwo) for the AES16 Multichannel Audio in following Ubuntu distributions and kernels:

1) Ubuntu 6.06.1 AMD64 Desktop - Kernel 2.6.15-26-amd64-generic
2) Ubuntu 7.04 AMD64 Desktop - Kernel 2.6.20-15-generic
3) Ubuntu 6.10 AMD64 Desktop - Kernel 2.6.17-10-generic

In all of these, modprobe (or insmod) causes a paging oops in the Kernel.  The soundon logfile is attached and it shows the oops.

I have also tried adding to the kernel boot  line:

1) pci=nommconf
2) acpi=off
3) nosmp noapic
4) pci=routeirq
5) pci=conf1

There is no problem with i386 kernels.

The PC is a Core2 Duo with a Q965 chipset.  The AES16 is a 32-bit PCI cards (v2.2 compliant bus).

OSS say that their driver works for them on Kernel 2.6.17-10-generic.  This is one of the kernels that I have tried, it didn't work for me.

Any ideas.....................................................

---

