---
title: "nvidia 8600 freezes system on X startup"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by surg30n on 2007-11-27
When X starts with "nvidia" driver, system got freeze. Dead black screen and no message, errors or speaker beeps..


```
# dmesg
[   20.393275] PCI: Cannot allocate resource region 3 of device 0000:05:00.0
[   20.480120] PCI: Failed to allocate mem resource #3:2000000@fe000000 for 0000:05:00.0
[   21.108511] Boot video device is 0000:05:00.0
[   39.067285] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 20
[   39.067387] PCI: Setting latency timer of device 0000:05:00.0 to 64
```

I also try:
- enabling restricted drivers.
- install nvidia 100.14.23 driver thru nvidia-installer
- install drivers thru Envy script
- compile latest kernel
- play with apic,lapic,noapic,acpi=off and other kernel options

And what is the region 3 of device? Sure my prob here..
>> PCI: Cannot allocate resource region 3 of device 0000:05:00.0 (video card)

Probably this is bios or kernel bug...

Btw video works greet on winxp sp2 on this machine.
If there are io/memory conflicts in linux kernel, how to pass right parameters (from windows sysinfo) for kernel (reserve=, pci=) for videocard gets work?

Any ideas?
Thx.

---

### Post by p_ano on 2007-12-14
I am having the exact same issue with my 8800 GTS, and have tried the same steps as you :

- enabling restricted drivers.
- install nvidia 100.14.23 driver thru nvidia-installer
- install drivers thru Envy script
- compile latest kernel
- play with apic,lapic,noapic,acpi=off and other kernel options

plus

- installed 7.10 and 7.04, same issue with both
- updating bios
- all sorts of xorg.conf settings and tweaks

I suspect this is a motherboard issue.   I have a Biostar NF4U AM2G using an nForce4 chipset.

Any ideas?

---

### Post by surg30n on 2007-12-17
Hello. I solved this issue, check this post
[http://forum.msi.com.tw/index.php?topic=112541.msg842513#msg842513](http://forum.msi.com.tw/index.php?topic=112541.msg842513#msg842513)

---

