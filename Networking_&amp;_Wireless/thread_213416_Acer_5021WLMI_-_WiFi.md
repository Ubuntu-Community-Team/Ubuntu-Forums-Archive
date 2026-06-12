---
title: "Acer 5021WLMI - WiFi"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by eddard on 2006-07-11
I'm new to linux and I recently installed Kubuntu 6.06, everything is ok except the problem with the wireless.

I followed this walk-thru :

[https://help.ubuntu.com/community/WifiDocs/Acer5021WLMi_Amd64?highlight=%28wifi%29%7C%285021wlmi%29](https://help.ubuntu.com/community/WifiDocs/Acer5021WLMi_Amd64?highlight=%28wifi%29%7C%285021wlmi%29)

to point 1.5 where I have to modprobe acer_acpi files.

This is what i got for make and make install :

root@eddard-laptop:~/acer_acpi-0.3# make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/eddard/acer_acpi-0.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-25-amd64-generic'
  CC [M]  /home/eddard/acer_acpi-0.3/acer_acpi.o
  Building modules, stage 2.
  MODPOST
  CC      /home/eddard/acer_acpi-0.3/acer_acpi.mod.o
  LD [M]  /home/eddard/acer_acpi-0.3/acer_acpi.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-25-amd64-generic'
root@eddard-laptop:~/acer_acpi-0.3# make install
mkdir -p /lib/modules/2.6.15-25-amd64-generic/extra
cp -v acer_acpi.ko /lib/modules/2.6.15-25-amd64-generic/extra/
`acer_acpi.ko' -> `/lib/modules/2.6.15-25-amd64-generic/extra/acer_acpi.ko'
depmod -a

This is the problem:

root@eddard-laptop:/proc# modprobe acer_acpi
FATAL: Error inserting acer_acpi (/lib/modules/2.6.15-25-amd64-generic/extra/acer_acpi.ko): Invalid module format

:(

dmesg says:

[  866.662513] acer_acpi: version magic '2.6.15-25-amd64-generic SMP preempt gcc-3.4' should be '2.6.15-25-amd64-generic SMP preempt gcc-4.0'

What should I do now? 

Thx.

---

### Post by eddard on 2006-07-11
OK, i solved the problem by completely staring over with reinstalling Kubuntu! Admins you can delete this :)

---

