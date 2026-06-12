---
title: "Can't change ethernet card smp_affinity when using bonding driver"
date: 2012-09-06
forum: Networking &amp; Wireless
---

### Post by tmartiro on 2012-09-06
I'v got a server with 2x1Gb nics, 8 cores CPU. The nics are bonded using bonding driver with mode 803.2ad. I faced the problem with changing network cards' affinity . The irq interrupts coming from nic cards are spread to 8 cores. I tried to limit the number of irq request against  2 cores of the CPU by editing /proc/irq/devicIRQXX/smp_affinity, but it did not work for me. Could you please help me to limit the irq request to the 2 cores. (every nic card to 1 core)

here is the output of the file /proc/interrupts

>     
CPU0       CPU1       CPU2       CPU3       CPU4       CPU5       CPU6       CPU7       
42: 1528829636 1528257890 1528333632 1529073557 1529549736 1528202078 1528422100 1529102035   PCI-MSI-edge      eth0

43: 1531418329 1530831731 1530926512 1531550710 1531976483 1530794560 1531089080 1531716969   PCI-MSI-edge      eth1

System is Ubuntu 12.04 LTS. kernel 3.2.0-29-generic

---

