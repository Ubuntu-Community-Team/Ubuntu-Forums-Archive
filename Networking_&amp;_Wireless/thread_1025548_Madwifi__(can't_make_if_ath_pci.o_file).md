---
title: "Madwifi  (can't make if_ath_pci.o file)"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by KJay87 on 2008-12-30
i have a problem with my ar242x wifi.. the installing is supose to be and easy 4 steps.. download files, make, make install and reboot.. but i get this message when i use the comand "make"

Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-22-generic/build SUBDIRS=/madwifi-0.9.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-22-generic'
  CC [M]  /madwifi-0.9.3/ath/if_ath_pci.o
/madwifi-0.9.3/ath/if_ath_pci.c: In function 'ath_pci_probe':
/madwifi-0.9.3/ath/if_ath_pci.c:203: error: 'struct net_device' has no member named 'owner'
/madwifi-0.9.3/ath/if_ath_pci.c:210: error: 'SA_SHIRQ' undeclared (first use in this function)
/madwifi-0.9.3/ath/if_ath_pci.c:210: error: (Each undeclared identifier is reported only once
/madwifi-0.9.3/ath/if_ath_pci.c:210: error: for each function it appears in.)
make[3]: *** [/madwifi-0.9.3/ath/if_ath_pci.o] Error 1
make[2]: *** [/madwifi-0.9.3/ath] Error 2
make[1]: *** [_module_/madwifi-0.9.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-22-generic'
make: *** [modules] Fejl 2

and how i see it.. it's ath_pci.o file that is the problem.. 
pleas help me..!

ubuntu 8.04 (hardy) 
Intel(R) Pentium(R) Dual  CPU  T2370  @ 1.73GHz
3 GB ram
Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (works)
Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter
2.6.24-22-generic
GCC 4.2.4 (i486-linux-gnu)

---

### Post by KJay87 on 2008-12-31
can anyone help my with madwifi .. i try'd installing madwifi tool in synmaptic.. but can open it.. :S not even form the terminal..
what kind of error is it ?

Plz help i am danish if there is anyone ?

---

### Post by kevdog on 2008-12-31
I thought you could use the ath9k driver with the ath242x chipset?  Have you looked into this?

---

