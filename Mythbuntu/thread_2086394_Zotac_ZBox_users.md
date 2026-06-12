---
title: "Zotac ZBox users"
date: 2012-11-20
forum: Mythbuntu
---

### Post by jonnybignote on 2012-11-20
Hey

anyone using a ZBox ID-41 as a frontend?  

I have followed all the usual steps - my backend machine wakes via wake on lan just fine from S3 fine, but this will not.

I finally found that I could resume the machine from the top usb socket using a wired USB keyboard, but not my wireless one....

No matter what I try, Wake On Lan will not work with this.  

As I said, bios enabled for it.  cat /proc/acpi/wakeup shows

```

P0P1	  S4	*disabled  pci:0000:00:1e.0
P0P4	  S4	*disabled  pci:0000:00:1c.0
P0P5	  S4	*disabled  pci:0000:00:1c.1
P0P6	  S4	*disabled  pci:0000:00:1c.2
P0P7	  S4	*disabled  
P0P8	  S4	*disabled  
P0P9	  S4	*disabled  
USB0	  S3	*enabled   pci:0000:00:1d.0
USB1	  S3	*enabled   pci:0000:00:1d.1
USB2	  S3	*enabled   pci:0000:00:1d.2
USB3	  S3	*enabled   pci:0000:00:1d.3
EUSB	  S3	*enabled   pci:0000:00:1d.7

```

I have also tried enabling all the pci devies for wakeup to no effect.

Light on ethernet port goes out in standby, so I'm assuming no power there = problem.

Any help much appreciated.

---

### Post by jonnybignote on 2012-11-20
sorry - forgot to say Mythbuntu 12.04 64bit

---

