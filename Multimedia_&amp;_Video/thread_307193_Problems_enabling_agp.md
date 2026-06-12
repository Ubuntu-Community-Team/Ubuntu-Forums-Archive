---
title: "Problems enabling agp"
date: 2006-11-26
forum: Multimedia &amp; Video
---

### Post by zoddic on 2006-11-26
I cant enable Agp for some reason. I give you some output here. Any hints on what to do? I have Option "NvAGP" "1" in xorg.conf. Thanks.
 
> zoddic@zodburken:~$ cat /proc/driver/nvidia/agp/status
Status:          Disabled

> zoddic@zodburken:~$ lsmod | grep agp
agpgart                33456  1 nvidia

> zoddic@zodburken:~$ dmesg | grep NVIDIA
[17179569.184000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[17179588.812000] nvidia: module license 'NVIDIA' taints kernel.
[17179589.080000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9629  Wed Nov  1 19:30:07 PST 2006

> zoddic@zodburken:~$ cat /proc/driver/nvidia/agp/card
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       8x 4x 
Registers:       0xff000e1b:0x00000000

> zoddic@zodburken:~$ cat /proc/driver/nvidia/agp/host-bridge 
Host Bridge:     PCI device 10de:00e1
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       8x 4x 
Registers:       0x1f00421b:0x00000001

---

### Post by zoddic on 2006-11-27
Noone :( ?

---

### Post by Squishy on 2007-05-31
Bump.

Did you find a solution, I am having the same problem.

---

