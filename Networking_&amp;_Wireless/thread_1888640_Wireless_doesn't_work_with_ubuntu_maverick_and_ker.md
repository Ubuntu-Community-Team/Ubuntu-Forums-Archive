---
title: "Wireless doesn't work with ubuntu maverick and kernel 3.1.4"
date: 2011-11-29
forum: Networking &amp; Wireless
---

### Post by Peps88 on 2011-11-29
Hi
I have a problem with my atheros wireless card with the kernel 3.1.4

I compiled the kernel 2.6.39.1 and the wireless works fine while when i compiled 3.1.4 the card doesn't work

I post you some commands:
sudo lshw -C network
```
giuseppe@giuseppe-house:~$ sudo lshw -C network
[sudo] password for giuseppe: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 90:e6:ba:82:55:12
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.0.6 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:40 ioport:e800(size=256) memory:feaff000-feafffff memory:feac0000-feadffff
  *-network UNCLAIMED
       description: Network controller
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:febf0000-febfffff
```rfkill list
```
giuseppe@giuseppe-house:~$ rfkill list 

```lsmod | grep ath
```
giuseppe@giuseppe-house:~$ lsmod | grep ath
ath9k                  94979  0 
mac80211              240045  1 ath9k
ath9k_common            1462  1 ath9k
ath9k_hw              297659  2 ath9k,ath9k_common
ath                    12054  2 ath9k,ath9k_hw
cfg80211              141888  3 ath9k,mac80211,ath
```sudo ifconfig -a
```
giuseppe@giuseppe-house:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 90:e6:ba:82:55:12  
          indirizzo inet:192.168.0.6  Bcast:192.168.0.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::92e6:baff:fe82:5512/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3794 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4105 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:1241649 (1.2 MB)  Byte TX:405831 (405.8 KB)
          Interrupt:40 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:153 errors:0 dropped:0 overruns:0 frame:0
          TX packets:153 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:12030 (12.0 KB)  Byte TX:12030 (12.0 KB)
```thanks for the help
regards

---

### Post by bluexrider on 2011-11-29
might try updating the wireless firmware

---

### Post by Peps88 on 2011-11-29
what should I do?

---

### Post by bluexrider on 2011-11-29
1. Have you tried resetting it with the network manager?
2. Have you rebooted into the old kernel and confirmed it still works there?
3. Have you looked for bug reports of this problem? If so there may be a fix?
4. There is another issue (solved) here  [http://ubuntuforums.org/showthread.php?t=1286503](http://ubuntuforums.org/showthread.php?t=1286503)

---

### Post by Peps88 on 2011-11-30
I tried to reset wicd but nothing
with the kernel 2.6.39 the atheros works fine (now I'm writing from this kernel)
Then I thought that the problem was kernel version so I tried a live of ubuntu 11.10 because last ubuntu use 3.0.0 kernel version but the card works fine.
i tried  [http://ubuntuforums.org/showthread.php?t=1286503](http://ubuntuforums.org/showthread.php?t=1286503) but nothing

this is the error when i do make install

```
giuseppe@giuseppe-house:~/Scrivania/compat-wireless-3.1.1-1$ sudo make install

Your old wireless subsystem modules were left intact:

kernel/net/mac80211/mac80211.ko
kernel/net/wireless/cfg80211.ko
kernel/net/wireless/lib80211.ko
kernel/drivers/net/wireless/adm8211.ko
kernel/drivers/net/wireless/at76c50x-usb.ko
kernel/drivers/net/wireless/ath/ath.ko
kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko
kernel/drivers/net/b44.ko
kernel/drivers/net/usb/cdc_ether.ko
kernel/drivers/misc/eeprom/eeprom_93cx6.ko
kernel/drivers/net/wireless/ipw2x00/ipw2100.ko
kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
kernel/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.ko
kernel/net/wireless/lib80211_crypt_ccmp.ko
kernel/net/wireless/lib80211_crypt_tkip.ko
kernel/net/wireless/lib80211_crypt_wep.ko
kernel/drivers/net/wireless/libertas/libertas.ko
kernel/drivers/net/wireless/libertas/libertas_cs.ko
kernel/drivers/net/wireless/libertas/libertas_sdio.ko
kernel/drivers/net/wireless/libertas/libertas_spi.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf.ko
kernel/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
kernel/drivers/net/wireless/ipw2x00/libipw.ko
kernel/drivers/net/wireless/mac80211_hwsim.ko
kernel/drivers/net/wireless/mwl8k.ko
kernel/drivers/net/wireless/orinoco/orinoco_cs.ko
kernel/drivers/net/wireless/orinoco/orinoco_nortel.ko
kernel/drivers/net/wireless/orinoco/orinoco_plx.ko
kernel/drivers/net/wireless/orinoco/orinoco_usb.ko
kernel/drivers/net/wireless/orinoco/orinoco.ko
kernel/drivers/net/wireless/p54/p54common.ko
kernel/drivers/net/wireless/p54/p54pci.ko
kernel/drivers/net/wireless/p54/p54spi.ko
kernel/drivers/net/wireless/p54/p54usb.ko
kernel/drivers/net/usb/rndis_host.ko
kernel/drivers/net/wireless/rndis_wlan.ko
kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
kernel/drivers/net/wireless/rt2x00/rt61pci.ko
kernel/drivers/net/wireless/rt2x00/rt73usb.ko
kernel/drivers/net/wireless/rtl818x/rtl8180/rtl8180.ko
kernel/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko
kernel/drivers/net/wireless/orinoco/spectrum_cs.ko
kernel/drivers/ssb/ssb.ko
kernel/drivers/net/wireless/libertas/usb8xxx.ko
kernel/drivers/net/usb/usbnet.ko
kernel/drivers/net/wireless/wl1251/wl1251.ko
kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko

Your old ethernet subsystem modules are left intact:

kernel/drivers/net/atlx/atl1.ko
kernel/drivers/net/atlx/atl2.ko
kernel/drivers/net/atl1e/atl1e.ko
kernel/drivers/net/atl1c/atl1c.ko

Your old bluetooth subsystem modules were left intact:

kernel/net/bluetooth/bluetooth.ko

make -C /lib/modules/3.1.4/build M=/home/giuseppe/Scrivania/compat-wireless-3.1.1-1 modules
make[1]: ingresso nella directory "/usr/src/linux-3.1.4"
  CC [M]  /home/giuseppe/Scrivania/compat-wireless-3.1.1-1/net/wireless/util.o
/home/giuseppe/Scrivania/compat-wireless-3.1.1-1/net/wireless/util.c: In function ‘cfg80211_change_iface’:
/home/giuseppe/Scrivania/compat-wireless-3.1.1-1/net/wireless/util.c:804: error: implicit declaration of function ‘br_port_exists’
make[3]: *** [/home/giuseppe/Scrivania/compat-wireless-3.1.1-1/net/wireless/util.o] Errore 1
make[2]: *** [/home/giuseppe/Scrivania/compat-wireless-3.1.1-1/net/wireless] Errore 2
make[1]: *** [_module_/home/giuseppe/Scrivania/compat-wireless-3.1.1-1] Errore 2
make[1]: uscita dalla directory "/usr/src/linux-3.1.4"
make: *** [modules] Errore 2
```

---

### Post by Peps88 on 2011-11-30
Hi :P
I solved with this thread

[http://ubuntuforums.org/showthread.php?t=1286503](http://ubuntuforums.org/showthread.php?t=1286503)

but i installed the compat-wireless-3.2-rc1-1.tar.bz2

until now works fine

thanks a lot

:)

---

### Post by bluexrider on 2011-11-30
Sure sounds like a conflict of drivers because you have "left-overs" from the previous kernel. 
That also explains why a live CD with a newer kernel works, because the live CD isn't really installed on your machine yet therefor no conflict.

I would proceed this way.

Download but do not install the newer kernel.

Remove the wireless and bluetooth drivers.

Make and install the new kernel.

should take care of the issue.

GOOD LUCK

---

### Post by bluexrider on 2011-11-30
great, please mark this (SOLVED)

---

### Post by Peps88 on 2011-11-30
thanks for the help bluexrider :)

I marked solved ):P

---

