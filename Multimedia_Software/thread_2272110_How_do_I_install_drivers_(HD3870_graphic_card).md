---
title: "How do I install drivers (HD3870 graphic card)"
date: 2015-04-04
forum: Multimedia Software
---

### Post by jasmin811 on 2015-04-04
hello everyone,  i have this card in my computer and the Ubuntu 14.04 LTS,so I want to know how to safely install the drivers for this card.  Thank you all for answers.

---

### Post by Bucky Ball on 2015-04-04
*Thread moved to **Multimedia**.*

Do an update then check 'Additional Drivers'. Anything there for your card? Could you also give the output of:

```
sudo lshw -C video
```

---

### Post by jasmin811 on 2015-04-04
this is what it says:

service@service-G31-M7-TE:~$ sudo lshw -C video
[sudo] password for service: 
  *-display               
       description: VGA compatible controller
       product: RV670 [Radeon HD 3870]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:42 memory:d0000000-dfffffff memory:feaf0000-feafffff ioport:d000(size=256) memory:feac0000-feadffff
service@service-G31-M7-TE:~$

---

### Post by jasmin811 on 2015-04-04
there is nothing in 'Additional Drivers' after checking

---

### Post by Bucky Ball on 2015-04-04
From your output, you have the correct open-source driver for that card already. Is there a reason you need to install the proprietary driver? Are you having issues with your screen output?

```
driver=radeon
```

That driver may be your only option if what Bashing-om states [here]("http://ubuntuforums.org/showthread.php?t=2160592&p=12721389&viewfull=1#post12721389") is true, that AMD no longer support the 3*** series of cards (pretty old).

---

### Post by Rob Sayer on 2015-04-04
> **Bucky Ball said:**
> ... That driver [radeon] may be your only option if what Bashing-om states [here]("http://ubuntuforums.org/showthread.php?t=2160592&p=12721389&viewfull=1#post12721389") is true, that AMD no longer support the 3*** series of cards (pretty old).

That's true.  AMD linux support isn't the best, and that series has been moved into legacy as far as linux is concerned.

In other words, stick with the open source radeon driver.

According to this:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

you should still have proper 3D hardware acceleration.

---

### Post by ajgreeny on 2015-04-04
Both the 3xxx and 4xxx series are no longer supported by the fglrx driver so your only option with those cards is the open-source radeon driver.

(Or, of course, another OS entirely.)

---

### Post by Kenneth_Benson on 2015-04-04
They may not be supported, but I just checked the AMD site and they do have a Linux driver for the HD 3xxx series (version 13.1) available for download.

---

### Post by QIII on 2015-04-04
They are there, however they ***will not work*** with any version of Ubuntu after 12.04.1 due to changes in the graphics stack.

Do not attempt to install those older drivers or we will be helping you clean up as we have so many others.

---

