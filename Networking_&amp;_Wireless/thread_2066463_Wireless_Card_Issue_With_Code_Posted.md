---
title: "Wireless Card Issue With Code Posted"
date: 2012-10-04
forum: Networking &amp; Wireless
---

### Post by Skiehawk11 on 2012-10-04
Hello everyone. I am a fairly new Ubuntu user and have really enjoyed Ubuntu for the most part. However, my wireless card has not worked since the day of the Ubuntu install. It worked until I installed the first round of updates and I have no idea how to correct that. 

I have a Toshiba Satellite A215-S4747 model laptop. Below are other details:

**lsb_release -a**
```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise
```


Nm-tool 

```
NetworkManager Tool 

State: connected (global) 

- Device: wlan0  [GEA82] ------------------------------------------------------- 
  Type:              802.11 WiFi 
  Driver:            ath5k 
  State:             connecting (configuring) 
  Default:           no 
  HW Address:        00:1B:9E:3E:36:19 

  Capabilities: 

  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 
```

sudo lshw-c network

```
*-network 
       description: Wireless interface 
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express) 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:14:00.0 
       logical name: wlan0 
       version: 01 
       serial: 00:1b:9e:3e:36:19 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ath5k driverversion=3.2.0-31-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg 
       resources: irq:19

 memory:f8200000-f820ffff
```

sudo lspci |grep Atheros

```
14:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
```

sudo iwconfig
```
lo        no wireless extensions. 

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Encryption key:off 
          Power Management:off 
          
eth0      no wireless extensions.
```


locate -i ath9k
```
/lib/modules/3.2.0-23-generic-pae/kernel/drivers/net/wireless/ath/ath9k 
/lib/modules/3.2.0-23-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko 
/lib/modules/3.2.0-23-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
/lib/modules/3.2.0-23-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko 
/lib/modules/3.2.0-23-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
/lib/modules/3.2.0-27-generic-pae/kernel/drivers/net/wireless/ath/ath9k 
/lib/modules/3.2.0-27-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko 
/lib/modules/3.2.0-27-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
/lib/modules/3.2.0-27-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko 
/lib/modules/3.2.0-27-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
/lib/modules/3.2.0-29-generic-pae/kernel/drivers/net/wireless/ath/ath9k 
/lib/modules/3.2.0-29-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko 
/lib/modules/3.2.0-29-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
/lib/modules/3.2.0-29-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko 
/lib/modules/3.2.0-29-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
/lib/modules/3.2.0-30-generic-pae/kernel/drivers/net/wireless/ath/ath9k 
/lib/modules/3.2.0-30-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko 
/lib/modules/3.2.0-30-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
/lib/modules/3.2.0-30-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko 
/lib/modules/3.2.0-30-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
/lib/modules/3.2.0-31-generic-pae/kernel/drivers/net/wireless/ath/ath9k 
/lib/modules/3.2.0-31-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko 
/lib/modules/3.2.0-31-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
/lib/modules/3.2.0-31-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko 
/lib/modules/3.2.0-31-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
/usr/src/linux-headers-3.2.0-23/drivers/net/wireless/ath/ath9k 
/usr/src/linux-headers-3.2.0-23/drivers/net/wireless/ath/ath9k/Kconfig 
/usr/src/linux-headers-3.2.0-23/drivers/net/wireless/ath/ath9k/Makefile 
/usr/src/linux-headers-3.2.0-23/include/linux/ath9k_platform.h 
/usr/src/linux-headers-3.2.0-23-generic-pae/include/config/ath9k 
/usr/src/linux-headers-3.2.0-23-generic-pae/include/config/ath9k.h 
/usr/src/linux-headers-3.2.0-23-generic-pae/include/config/ath9k/ahb.h 
/usr/src/linux-headers-3.2.0-23-generic-pae/include/config/ath9k/common.h 
/usr/src/linux-headers-3.2.0-23-generic-pae/include/config/ath9k/debugfs.h 
/usr/src/linux-headers-3.2.0-23-generic-pae/include/config/ath9k/htc 
/usr/src/linux-headers-3.2.0-23-generic-pae/include/config/ath9k/htc.h 
/usr/src/linux-headers-3.2.0-23-generic-pae/include/config/ath9k/hw.h 
/usr/src/linux-headers-3.2.0-23-generic-pae/include/config/ath9k/pci.h 
/usr/src/linux-headers-3.2.0-23-generic-pae/include/config/ath9k/rate 
/usr/src/linux-headers-3.2.0-23-generic-pae/include/config/ath9k/htc/debugfs.h 
/usr/src/linux-headers-3.2.0-23-generic-pae/include/config/ath9k/rate/control.h 
/usr/src/linux-headers-3.2.0-23-generic-pae/include/linux/ath9k_platform.h 
/usr/src/linux-headers-3.2.0-27/drivers/net/wireless/ath/ath9k 
/usr/src/linux-headers-3.2.0-27/drivers/net/wireless/ath/ath9k/Kconfig 
/usr/src/linux-headers-3.2.0-27/drivers/net/wireless/ath/ath9k/Makefile 
/usr/src/linux-headers-3.2.0-27/include/linux/ath9k_platform.h 
/usr/src/linux-headers-3.2.0-27-generic-pae/include/config/ath9k 
/usr/src/linux-headers-3.2.0-27-generic-pae/include/config/ath9k.h 
/usr/src/linux-headers-3.2.0-27-generic-pae/include/config/ath9k/ahb.h 
/usr/src/linux-headers-3.2.0-27-generic-pae/include/config/ath9k/common.h 
/usr/src/linux-headers-3.2.0-27-generic-pae/include/config/ath9k/debugfs.h 
/usr/src/linux-headers-3.2.0-27-generic-pae/include/config/ath9k/htc 
/usr/src/linux-headers-3.2.0-27-generic-pae/include/config/ath9k/htc.h 
/usr/src/linux-headers-3.2.0-27-generic-pae/include/config/ath9k/hw.h 
/usr/src/linux-headers-3.2.0-27-generic-pae/include/config/ath9k/pci.h 
/usr/src/linux-headers-3.2.0-27-generic-pae/include/config/ath9k/rate 
/usr/src/linux-headers-3.2.0-27-generic-pae/include/config/ath9k/htc/debugfs.h 
/usr/src/linux-headers-3.2.0-27-generic-pae/include/config/ath9k/rate/control.h 
/usr/src/linux-headers-3.2.0-27-generic-pae/include/linux/ath9k_platform.h 
/usr/src/linux-headers-3.2.0-29/drivers/net/wireless/ath/ath9k 
/usr/src/linux-headers-3.2.0-29/drivers/net/wireless/ath/ath9k/Kconfig 
/usr/src/linux-headers-3.2.0-29/drivers/net/wireless/ath/ath9k/Makefile 
/usr/src/linux-headers-3.2.0-29/include/linux/ath9k_platform.h 
/usr/src/linux-headers-3.2.0-29-generic-pae/include/config/ath9k 
/usr/src/linux-headers-3.2.0-29-generic-pae/include/config/ath9k.h 
/usr/src/linux-headers-3.2.0-29-generic-pae/include/config/ath9k/ahb.h 
/usr/src/linux-headers-3.2.0-29-generic-pae/include/config/ath9k/common.h 
/usr/src/linux-headers-3.2.0-29-generic-pae/include/config/ath9k/debugfs.h 
/usr/src/linux-headers-3.2.0-29-generic-pae/include/config/ath9k/htc 
/usr/src/linux-headers-3.2.0-29-generic-pae/include/config/ath9k/htc.h 
/usr/src/linux-headers-3.2.0-29-generic-pae/include/config/ath9k/hw.h 
/usr/src/linux-headers-3.2.0-29-generic-pae/include/config/ath9k/pci.h 
/usr/src/linux-headers-3.2.0-29-generic-pae/include/config/ath9k/rate 
/usr/src/linux-headers-3.2.0-29-generic-pae/include/config/ath9k/htc/debugfs.h 
/usr/src/linux-headers-3.2.0-29-generic-pae/include/config/ath9k/rate/control.h 
/usr/src/linux-headers-3.2.0-29-generic-pae/include/linux/ath9k_platform.h 
/usr/src/linux-headers-3.2.0-30/drivers/net/wireless/ath/ath9k 
/usr/src/linux-headers-3.2.0-30/drivers/net/wireless/ath/ath9k/Kconfig 
/usr/src/linux-headers-3.2.0-30/drivers/net/wireless/ath/ath9k/Makefile 
/usr/src/linux-headers-3.2.0-30/include/linux/ath9k_platform.h 
/usr/src/linux-headers-3.2.0-30-generic-pae/include/config/ath9k 
/usr/src/linux-headers-3.2.0-30-generic-pae/include/config/ath9k.h 
/usr/src/linux-headers-3.2.0-30-generic-pae/include/config/ath9k/ahb.h 
/usr/src/linux-headers-3.2.0-30-generic-pae/include/config/ath9k/common.h 
/usr/src/linux-headers-3.2.0-30-generic-pae/include/config/ath9k/debugfs.h 
/usr/src/linux-headers-3.2.0-30-generic-pae/include/config/ath9k/htc 
/usr/src/linux-headers-3.2.0-30-generic-pae/include/config/ath9k/htc.h 
/usr/src/linux-headers-3.2.0-30-generic-pae/include/config/ath9k/hw.h 
/usr/src/linux-headers-3.2.0-30-generic-pae/include/config/ath9k/pci.h 
/usr/src/linux-headers-3.2.0-30-generic-pae/include/config/ath9k/rate 
/usr/src/linux-headers-3.2.0-30-generic-pae/include/config/ath9k/htc/debugfs.h 
/usr/src/linux-headers-3.2.0-30-generic-pae/include/config/ath9k/rate/control.h 
/usr/src/linux-headers-3.2.0-30-generic-pae/include/linux/ath9k_platform.h 
/usr/src/linux-headers-3.2.0-31/drivers/net/wireless/ath/ath9k 
/usr/src/linux-headers-3.2.0-31/drivers/net/wireless/ath/ath9k/Kconfig 
/usr/src/linux-headers-3.2.0-31/drivers/net/wireless/ath/ath9k/Makefile 
/usr/src/linux-headers-3.2.0-31/include/linux/ath9k_platform.h 
/usr/src/linux-headers-3.2.0-31-generic-pae/include/config/ath9k 
/usr/src/linux-headers-3.2.0-31-generic-pae/include/config/ath9k.h 
/usr/src/linux-headers-3.2.0-31-generic-pae/include/config/ath9k/ahb.h 
/usr/src/linux-headers-3.2.0-31-generic-pae/include/config/ath9k/common.h 
/usr/src/linux-headers-3.2.0-31-generic-pae/include/config/ath9k/debugfs.h 
/usr/src/linux-headers-3.2.0-31-generic-pae/include/config/ath9k/htc 
/usr/src/linux-headers-3.2.0-31-generic-pae/include/config/ath9k/htc.h 
/usr/src/linux-headers-3.2.0-31-generic-pae/include/config/ath9k/hw.h 
/usr/src/linux-headers-3.2.0-31-generic-pae/include/config/ath9k/pci.h 
/usr/src/linux-headers-3.2.0-31-generic-pae/include/config/ath9k/rate 
/usr/src/linux-headers-3.2.0-31-generic-pae/include/config/ath9k/htc/debugfs.h 
/usr/src/linux-headers-3.2.0-31-generic-pae/include/config/ath9k/rate/control.h 
/usr/src/linux-headers-3.2.0-31-generic-pae/include/linux/ath9k_platform.h
```

---

