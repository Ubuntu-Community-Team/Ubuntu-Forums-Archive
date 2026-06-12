---
title: "Udev rules for capture cards"
date: 2012-08-31
forum: Mythbuntu
---

### Post by Billsputters on 2012-08-31
I've been scratching my head for some time here, initially the problem was trying to get Diseq to stick for LNB's. I'm using a TBS 6981 Dual card, and could get LNB for one tuner, but not the other. After some trial and error, I discovered that my other tuner card (Hauppauge Dual Nova T) could have an LNB assigned to it! This did not seem right somehow, for a DVB-T device.

So I deleted all capture cards and started again. No joy. I then discovered that card order can change on bootup, and found the way around it was a Udev rule.

So I have a Dual TBS 6981, with both inputs occupied, and a Hauppauge Nova-T with just the first input being fed (there is only one multiplex here in Ireland). So I needed to ident and order not only the TBS tuners, but make sure I was talking to the correct Hauppauge DVB-T tuner as well.

I tried this rule


```
# /etc/udev/rules.d/10-dvb.rules
#
# To Ientify serial nos etc for a Device call
# udevadm info -a -p $(udevadm info -q path -n /dev/dvb/adapter0/frontend0)
#
                                    
# Create a symlinks for both tuners of Hauppauge Nova-T device
SUBSYSTEM=="dvb", ATTRS{idVendor}=="2040", ATTRS{idProduct}=="8400", ENV{nova}!="two", ENV{nova}="two", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter_hp1/%%s $${K#*.}'", SYMLINK+="%c"
SUBSYSTEM=="dvb", ATTRS{idVendor}=="2040", ATTRS{idProduct}=="8400", ENV{nova}=="two", ENV{nova}="one", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter_hp2/%%s $${K#*.}'", SYMLINK+="%c"

# Create a symlinks for both tuners of TBS device
SUBSYSTEM=="dvb", ATTRS{device}=="0x8852", ATTRS{subsystem_vendor}=="0x6981", ENV{tbs}!="two", ENV{tbs}="two", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter_tbs1/%%s $${K#*.}'", SYMLINK+="%c"
SUBSYSTEM=="dvb", ATTRS{device}=="0x8852", ATTRS{subsystem_vendor}=="0x6981", ENV{tbs}=="two", ENV{tbs}="one", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter_tbs2/%%s $${K#*.}'", SYMLINK+="%c"



```

It half works, ie it correctly finds the Hauppauge tuners and labels them hp1 and hp2, but fails with the TBS card. The output from udevadm foir the TBS card is

```
  looking at device '/devices/pci0000:00/0000:00:07.0/0000:02:00.0/dvb/dvb1.dvr0':
    KERNEL=="dvb1.dvr0"
    SUBSYSTEM=="dvb"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:07.0/0000:02:00.0':
    KERNELS=="0000:02:00.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="cx23885"
    ATTRS{vendor}=="0x14f1"
    ATTRS{device}=="0x8852"
    ATTRS{subsystem_vendor}=="0x6981"
    ATTRS{subsystem_device}=="0x8888"
    ATTRS{class}=="0x040000"
    ATTRS{irq}=="19"
    ATTRS{local_cpus}=="00000000,00000000,00000000,00000000,00000000,00000000,00000000,0000000f"
    ATTRS{local_cpulist}=="0-3"
    ATTRS{numa_node}=="0"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00/0000:00:07.0':
    KERNELS=="0000:00:07.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="pcieport"
    ATTRS{vendor}=="0x1002"
    ATTRS{device}=="0x597d"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{subsystem_device}=="0x8353"
    ATTRS{class}=="0x060400"
    ATTRS{irq}=="41"
    ATTRS{local_cpus}=="00000000,00000000,00000000,00000000,00000000,00000000,00000000,0000000f"
    ATTRS{local_cpulist}=="0-3"
    ATTRS{numa_node}=="0"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}=="1"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
```

I can't pinpoint where I am going wrong here, can anyone help?

btw, is there a better way of resetting the rules other than rebooting the machine!

---

### Post by Billsputters on 2012-09-01
OK, seems like I fixed this. In between starting this and getting to the stage of testing the udev rules, I must have done an update, and installed a new kernel, and thus the drivers for the TBS cards were not in sync!

Doh!

---

