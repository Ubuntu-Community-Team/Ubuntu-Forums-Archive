---
title: "Please help!!!! Video driver update"
date: 2012-12-26
forum: Multimedia Software
---

### Post by perro68 on 2012-12-26
I updated my drivers using the additional drivers tab

my video is an AMD Radeon HD 7640G 

after changing the driver now when when ever i restart / reboot 

all i get is the command line prompt

how do i revert back to the original drivers supplied by ubuntu

the proprietary drivers don't seem to work

---

### Post by fdrake on 2012-12-26
post the output of 
```
lsmod | grep -i -e amd -e fglrx
sudo lshw -C display
```

---

### Post by perro68 on 2012-12-26
> **fdrake said:**
> post the output of 
```
lsmod | grep -i -e amd -e fglrx
sudo lshw -C display
```

lsmod | grep -i -e amd -e fglrx


gives me :

fglrx                                 4715353    1
amd_iommu_v2                    19097    1  fglrx





sudo lshw -C display

gives me :

PCI (sysfs)

and no prompt .....it just sits there after that

---

### Post by fdrake on 2012-12-27
> **perro68 said:**
> 

sudo lshw -C display

gives me :

PCI (sysfs)

and no prompt .....it just sits there after that

give it some times it may take 30 sec depending on the speed of the system but eventually it will something something.

also while you there provide me with this output too.
```
uname -ra
```

---

### Post by Yellow Pasque on 2012-12-27
```
sudo apt-get remove --purge fglrx
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

### Post by fdrake on 2012-12-27
> **Temüjin said:**
> ```
sudo apt-get remove --purge fglrx
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
is  fglrx the propietary module?
so the  amd_iommu_v2 is the one from ubuntu then? still trying to figure that out.

---

### Post by Yellow Pasque on 2012-12-27
amd_iommu_v2 is probably a memory mapping module used by fglrx/Catalyst. The open source driver uses something different for memory mapping.

---

