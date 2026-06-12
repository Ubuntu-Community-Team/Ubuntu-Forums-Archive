---
title: "Problem getting madwifi working on 2.6.24-24"
date: 2009-07-15
forum: Networking &amp; Wireless
---

### Post by Tony Flury on 2009-07-15
I accepted the upgrade from 2.6.24-23 to 2.6.24-24. I have the madwifi 0.10.5.6 source code compiled against 23, and then installed, and it works seamlessly.

When I rebooted into 24, my wireless did not work - no problem I thought - I will rebuild - so i did : 

```

cd madwifi-hal-0.10.5.6
make clean
make
sudo make install
modprobe ath_pci
[CODE]

When i do the modprobe i get an error message - and the following lines in dmesg : 

[CODE]
[  175.239880] ath_pci: disagrees about version of symbol _ath_hal_attach
[  175.239896] ath_pci: Unknown symbol _ath_hal_attach
[  175.240173] ath_pci: disagrees about version of symbol ath_hal_process_noisef
loor
[  175.240178] ath_pci: Unknown symbol ath_hal_process_noisefloor
[  175.241287] ath_pci: disagrees about version of symbol ath_hal_computetxtime
[  175.241293] ath_pci: Unknown symbol ath_hal_computetxtime

```

Anyone got any clues ?

Note : Due to wireless not working in 2.6.24-24 - I have no acess, so I am reporting as best I can.

---

### Post by Tony Flury on 2009-07-20
a quick bump - if anyone has any ideas that would be appreciated.

---

### Post by kokonobs on 2009-07-20
I'm having a very similar problem to you. When i bootup using 2.6.24-24, my wirless signal shows as connected but i can't access the internet. I'm back using 23 now.

---

### Post by Aearenda on 2009-07-20
Tony Flury, are you sure the linux-headers package has been upgraded to match the kernel version?

---

### Post by Tony Flury on 2009-07-20
There is an interesting question - how do i upgrade the linux-headers package to the right version to 2.6.24-24 when i can't connect.

Anyway I can download them in 2.6.23 (but not install them) and then reboot to 2.6.24-24 and then install.

---

### Post by Aearenda on 2009-07-20
Unless you're doing some dual-booting with separate partitions for your different versions, you can install the headers while running the earlier kernel. The package management system is not kernel-version dependent, and the usual process automatically upgrades both the kernel and the headers while running on the 'now old' kernel.

To keep the headers upgraded in step with the kernel, make sure you have 'linux-headers-generic' installed (assuming you are using the 'generic' kernel) - this always depends on the most recent header package. However, I think this is a standard part of an Ubuntu installation - unless you have removed it, I don't understand why the headers would be wrong. 

In any case, I've done some googling instead of relying on my memory of when I encountered this, and it looks like you might be loading either part of the old ath_pci or the ath5k driver instead of the new one - but I don't think ath5k was included in 8.04, and you haven't tried adding it, have you?

BTW, I'm assuming you're doing 'sudo modprobe ath_pci' - your first post omits 'sudo' from this line, but it wouldn't work without.

Do you have anything in /etc/modprobe.d/blacklist, or in /etc/modules, relevant to ath_pci?

Please post the output (on the new kernel) from```
modinfo ath_pci
modinfo ath_hal
```You might need to capture these to a file to transfer back to the old kernel so you can post them - in which case ```

modinfo ath_pci > file.txt
modinfo ath_hal >> file.txt
```will create the file 'file.txt' for this purpose.

---

