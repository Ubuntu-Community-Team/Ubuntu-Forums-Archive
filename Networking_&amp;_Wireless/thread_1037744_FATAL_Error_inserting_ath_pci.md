---
title: "FATAL: Error inserting ath_pci"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by 804_ak on 2009-01-12
I ditched Vista for Ubuntu this weekend.

I was able to get my wireless working with the madwifi drivers. After I reboot though, it seems to die. I have an AR5007.

I try running:

sudo modprobe ath_pci

and get this message:

FATAL: Error inserting ath_pci (/lib/modules/2.6.24-23-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

dmesg says:

[  384.575603] ath_pci: Unknown symbol _ath_hal_attach
[  384.575708] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[  384.575712] ath_pci: Unknown symbol ath_hal_process_noisefloor
[  384.576139] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[  384.576143] ath_pci: Unknown symbol ath_hal_computetxtime
[  384.576420] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[  384.576423] ath_pci: Unknown symbol ath_hal_mhz2ieee
[  384.576618] ath_pci: Unknown symbol _ath_hal_detach
[  384.577249] ath_pci: Unknown symbol ath_hal_print_decoded_register
[  384.577849] ath_pci: disagrees about version of symbol ath_hal_init_channels
[  384.577853] ath_pci: Unknown symbol ath_hal_init_channels
[  384.578131] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[  384.578135] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[  387.865457] ath_pci: disagrees about version of symbol _ath_hal_attach
[  387.865467] ath_pci: Unknown symbol _ath_hal_attach
[  387.865572] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[  387.865575] ath_pci: Unknown symbol ath_hal_process_noisefloor
[  387.865999] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[  387.866001] ath_pci: Unknown symbol ath_hal_computetxtime
[  387.866277] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[  387.866279] ath_pci: Unknown symbol ath_hal_mhz2ieee
[  387.866471] ath_pci: Unknown symbol _ath_hal_detach
[  387.867102] ath_pci: Unknown symbol ath_hal_print_decoded_register
[  387.867700] ath_pci: disagrees about version of symbol ath_hal_init_channels
[  387.867702] ath_pci: Unknown symbol ath_hal_init_channels
[  387.867972] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[  387.867974] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[  622.841130] ath_pci: disagrees about version of symbol _ath_hal_attach
[  622.841139] ath_pci: Unknown symbol _ath_hal_attach
[  622.841244] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[  622.841247] ath_pci: Unknown symbol ath_hal_process_noisefloor
[  622.841673] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[  622.841676] ath_pci: Unknown symbol ath_hal_computetxtime
[  622.841955] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[  622.841958] ath_pci: Unknown symbol ath_hal_mhz2ieee
[  622.842146] ath_pci: Unknown symbol _ath_hal_detach
[  622.842956] ath_pci: Unknown symbol ath_hal_print_decoded_register
[  622.844146] ath_pci: disagrees about version of symbol ath_hal_init_channels
[  622.844150] ath_pci: Unknown symbol ath_hal_init_channels
[  622.844678] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[  622.844682] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[ 1066.396982] ath_pci: disagrees about version of symbol _ath_hal_attach
[ 1066.396990] ath_pci: Unknown symbol _ath_hal_attach
[ 1066.397095] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor
[ 1066.397097] ath_pci: Unknown symbol ath_hal_process_noisefloor
[ 1066.397524] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[ 1066.397526] ath_pci: Unknown symbol ath_hal_computetxtime
[ 1066.397810] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee
[ 1066.397812] ath_pci: Unknown symbol ath_hal_mhz2ieee
[ 1066.398000] ath_pci: Unknown symbol _ath_hal_detach
[ 1066.398868] ath_pci: Unknown symbol ath_hal_print_decoded_register
[ 1066.400097] ath_pci: disagrees about version of symbol ath_hal_init_channels
[ 1066.400099] ath_pci: Unknown symbol ath_hal_init_channels
[ 1066.400627] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[ 1066.400629] ath_pci: Unknown symbol ath_hal_getwirelessmodes


I found a forum post that suggested uninstalling linux-restricted-modules.
I did that and then broke my graphics and fixed my wireless. I finally managed to get that fixed, but now my wifi is busted again.

Please help!

---

### Post by bashukhan on 2009-01-24
I have the exact same issue started out with the exact same problem when I tore Vista down on my Acer 5720Z and tried to switch to Ubuntu Hardy.

I noticed the actual ath_pci insertion failures started out when I tried getting virtualization softwares to work. Uninstalling VirtualBox for a while fixed the issue but again when I installed Qemu, these same errors started to appear again.


> ```
root@ChainSmoker:~/madwifi-ng7# modprobe ath_pci
FATAL: Error inserting ath_pci (/lib/modules/2.6.24-23-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
 
```



If someone has a solution, suggestion or a workaround for this madwifi modular failure, please post.

Thanks.

---

### Post by diablo75 on 2009-01-24
Have either of you tried using ndiswrapper instead of madwifi?

---

### Post by kevdog on 2009-01-24
For the ar5007 card, I would suggest the ath5k driver (it a new driver) that is located in the linux backports repository.  Its totally open source and is written by the madwifi developers.

---

### Post by setsuna on 2009-02-04
i've same problem with TS . . 

```
abz@Aspire4520:~$ sudo modprobe ath_pci 
FATAL: Error inserting ath_pci (/lib/modules/2.6.24-23-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

i've Hardy installed on my acer 4520 (atheros wifi)
sorry that i newbie . .

i'm forgot when i messed up my wifi,
now, both of them (madwifi and ndiswrapper) not work for me T__T

what should i do?

~thx~

---

