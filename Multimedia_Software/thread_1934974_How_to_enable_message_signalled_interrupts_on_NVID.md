---
title: "How to enable message signalled interrupts on NVIDIA"
date: 2012-03-03
forum: Multimedia Software
---

### Post by Sylos on 2012-03-03
Hello all.

I have an MSI Nvidia 7900GT which I am trying to enable MSI on. Sadly it appears to be failing.

Im doing this because the card is blocking a PCI car from being registered (the MB is a gigabyte GA-Z68AP-D3 which uses a pci-to-pcie bridge). lspci -vvv shows that both are on the same IRQ and this appears to result in alsa being unable to access the PCI sound card. Hence Im trying to enable MSI to get the Nvidia card off the IRQ.

I have tried adding
```
options nvidia NVreg_EnableMSI=1
options nouveau msi=1
```

to /etc/modprobe.d/nvidia.conf

but cat /proc/interrupts still shows:

```
19:       1735          0          0          0   IO-APIC-fasteoi   nvidia

```

So whatever I am doing is obviously failing.

So I am pleading for help. Anyone got any ideas?

cheers

---

### Post by Sylos on 2012-03-04
I just did modinfo on the kernel module and it appears that the msi parameter is active.

```
modinfo nvidia-current
filename:       /lib/modules/2.6.32-38-preempt/updates/dkms/nvidia-current.ko
license:        NVIDIA
alias:          char-major-195-*
alias:          pci:v000010DEd00000E00sv*sd*bc04sc80i00*
alias:          pci:v000010DEd00000AA3sv*sd*bc0Bsc40i00*
alias:          pci:v000010DEd*sv*sd*bc03sc02i00*
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
depends:        
vermagic:       2.6.32-38-preempt SMP preempt mod_unload modversions 
parm:           NVreg_EnableVia4x:int
parm:           NVreg_EnableALiAGP:int
parm:           NVreg_ReqAGPRate:int
parm:           NVreg_EnableAGPSBA:int
parm:           NVreg_EnableAGPFW:int
parm:           NVreg_Mobile:int
parm:           NVreg_ResmanDebugLevel:int
parm:           NVreg_RmLogonRC:int
parm:           NVreg_ModifyDeviceFiles:int
parm:           NVreg_DeviceFileUID:int
parm:           NVreg_DeviceFileGID:int
parm:           NVreg_DeviceFileMode:int
parm:           NVreg_RemapLimit:int
parm:           NVreg_UpdateMemoryTypes:int
parm:           NVreg_UseVBios:int
parm:           NVreg_RMEdgeIntrCheck:int
parm:           NVreg_UsePageAttributeTable:int
[COLOR="Red"]parm:           NVreg_EnableMSI:int[/COLOR]
parm:           NVreg_MapRegistersEarly:int
parm:           NVreg_RegisterForACPIEvents:int
parm:           NVreg_RegistryDwords:charp
parm:           NVreg_NvAGP:int

```

So why isnt it working?

---

### Post by Sylos on 2012-03-05
Bumping for the cause......

---

### Post by Sylos on 2012-03-07
*-Thread falls down stairs-*

BUMP!
    
   BUMP!
   
       BUMP!
           
           BUMP!


EDIT: I put spaces in that to make it staggered like a set of stairs but it doesnt show up. Now I feel a fool!

---

### Post by Sylos on 2012-03-15
For anyone who is also looking at this I managed to do it by manually installing the latest nvidia driver from their website.

---

