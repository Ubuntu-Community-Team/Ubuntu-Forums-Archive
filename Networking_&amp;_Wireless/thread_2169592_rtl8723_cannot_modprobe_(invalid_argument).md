---
title: "rtl8723 cannot modprobe (invalid argument)"
date: 2013-08-22
forum: Networking &amp; Wireless
---

### Post by tomski2 on 2013-08-22
hi


i made a apt-get dist-upgrade, got a new kernel and since that my wireless doesn't work anymore and is not detected in iwconfig.
I followed another topic (Helmut from Germany on ubuntu forum who said to uninstall linux backport which i did, i recompiled after that but still aint working).

Ubuntu 12.04 Kernel 3.2.0-52
Driver rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 found on askubuntu

```
# iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.

# sudo su
root@liberty:/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# make clean
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Entering directory `/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192ce'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192ce'
make[1]: Entering directory `/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192se'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192se'
make[1]: Entering directory `/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192de'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192de'
make[1]: Entering directory `/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e'
root@liberty:/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# make
make -C /lib/modules/3.2.0-52-generic-pae/build M=/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-52-generic-pae'
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rc.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/debug.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/regd.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/efuse.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/cam.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/ps.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/core.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/stats.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/pci.o
  LD [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtlwifi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtlwifi.mod.o
  LD [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtlwifi.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-52-generic-pae'
make[1]: Entering directory `/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192ce'
make -C /lib/modules/3.2.0-52-generic-pae/build M=/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192ce modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-52-generic-pae'
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192ce/hw.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192ce/table.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192ce/sw.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192ce/trx.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192ce/led.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192ce/fw.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192ce/phy.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192ce/rf.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192ce/dm.o
  LD [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192ce/rtl8192ce.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192ce/rtl8192ce.mod.o
  LD [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192ce/rtl8192ce.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-52-generic-pae'
make[1]: Leaving directory `/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192ce'
make[1]: Entering directory `/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192se'
make -C /lib/modules/3.2.0-52-generic-pae/build M=/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192se modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-52-generic-pae'
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192se/hw.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192se/table.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192se/sw.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192se/trx.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192se/led.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192se/fw.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192se/phy.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192se/rf.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192se/dm.o
  LD [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192se/rtl8192se.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192se/rtl8192se.mod.o
  LD [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192se/rtl8192se.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-52-generic-pae'
make[1]: Leaving directory `/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192se'
make[1]: Entering directory `/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192de'
make -C /lib/modules/3.2.0-52-generic-pae/build M=/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192de modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-52-generic-pae'
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192de/hw.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192de/table.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192de/sw.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192de/trx.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192de/led.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192de/fw.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192de/phy.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192de/rf.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192de/dm.o
  LD [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192de/rtl8192de.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192de/rtl8192de.mod.o
  LD [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192de/rtl8192de.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-52-generic-pae'
make[1]: Leaving directory `/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192de'
make[1]: Entering directory `/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e'
make -C /lib/modules/3.2.0-52-generic-pae/build M=/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-52-generic-pae'
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e/hw.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e/table.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e/sw.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e/trx.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e/led.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e/fw.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e/phy.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e/rf.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e/dm.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e/pwrseq.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e/pwrseqcmd.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e/hal_btc.o
  CC [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e/hal_bt_coexist.o
  LD [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e/rtl8723e.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e/rtl8723e.mod.o
  LD [M]  /home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e/rtl8723e.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-52-generic-pae'
make[1]: Leaving directory `/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e'
root@liberty:/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# make install
make -C /lib/modules/3.2.0-52-generic-pae/build M=/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-52-generic-pae'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-52-generic-pae'
make[1]: Entering directory `/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192ce'
make -C /lib/modules/3.2.0-52-generic-pae/build M=/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192ce modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-52-generic-pae'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-52-generic-pae'
make[1]: Leaving directory `/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192ce'
make[1]: Entering directory `/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192se'
make -C /lib/modules/3.2.0-52-generic-pae/build M=/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192se modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-52-generic-pae'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-52-generic-pae'
make[1]: Leaving directory `/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192se'
make[1]: Entering directory `/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192de'
make -C /lib/modules/3.2.0-52-generic-pae/build M=/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192de modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-52-generic-pae'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-52-generic-pae'
make[1]: Leaving directory `/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8192de'
make[1]: Entering directory `/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e'
make -C /lib/modules/3.2.0-52-generic-pae/build M=/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-52-generic-pae'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-52-generic-pae'
make[1]: Leaving directory `/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/rtl8723e'
find /lib/modules/3.2.0-52-generic-pae -name "r8192se_*.ko" -exec rm {} \;
find /lib/modules/3.2.0-52-generic-pae -name "r8192ce_*.ko" -exec rm {} \;
find /lib/modules/3.2.0-52-generic-pae -name "r8723e_*.ko" -exec rm {} \;
root@liberty:/home/tomski/Documents/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# modprobe rtl8723e
FATAL: Error inserting rtl8723e (/lib/modules/3.2.0-52-generic-pae/kernel/drivers/net/wireless/rtlwifi/rtl8723e/rtl8723e.ko): Invalid argument
```


I hope somebody can help me!
thx

---

### Post by wildmanne39 on 2013-08-22
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

