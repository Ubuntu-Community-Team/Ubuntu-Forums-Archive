---
title: "HP Proliant ML110 G7 and Matrox MGa G200EH not working"
date: 2012-05-19
forum: Multimedia Software
---

### Post by hectorUbu on 2012-05-19
Hello,

I just installed Ubuntu 12.04 on an HP Proliant ML110 G7 server with a Matrox MGA G200EH. It seems that the correct driver is not working since I can't select the right resolution for my monitor (1680x1050) and lshw shows UNCLAIMED:

```
$ sudo lshw -c video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: MGA G200EH
       vendor: Matrox Graphics, Inc.
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f9000000-f9ffffff memory:fbde0000-fbde3fff memory:fb000000-fb7fffff
```

The server is Ubuntu Certified as stated here: [http://www.ubuntu.com/certification/hardware/201203-10852/](http://www.ubuntu.com/certification/hardware/201203-10852/)

So why is it not working out of the box? Any help? I googled and serched here without any luck.

Thanks!

Hector

---

