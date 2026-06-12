---
title: "Help Me to install driver"
date: 2012-04-12
forum: Networking &amp; Wireless
---

### Post by divyashwarrajj on 2012-04-12
I'm Beginner in BT5 . Some one help me

Some Info Here

```
root@bt:~# airdriver-ng detect

Found "Madwifi[-ng]" device: (ath_pci)
04:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev ff)


USB devices (generic detection):
Bus 001 Device 003: ID 0cf3:311d Atheros Communications, Inc.

PCI devices (generic detection):
04:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev ff)

root@bt:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@bt:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 10:1f:74:c0:6a:73  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:71 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10369 (10.3 KB)  TX bytes:10369 (10.3 KB)
```


And this for installing 


```
root@bt:~# cd madwifi-trunk-r4177-20120131
root@bt:~/madwifi-trunk-r4177-20120131# make clean
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
		make -C $i clean; \
	done
make[1]: Entering directory `/root/madwifi-trunk-r4177-20120131/ath'
rm -f *~ *.o *.ko *.mod.c .*.cmd
rm -f modules.order .depend .version .*.o.flags .*.o.d
rm -rf .tmp_versions
make[1]: Leaving directory `/root/madwifi-trunk-r4177-20120131/ath'
make[1]: Entering directory `/root/madwifi-trunk-r4177-20120131/ath_hal'
rm -f *~ *.o *.ko *.mod.c .*.cmd
rm -f modules.order .depend .version .*.o.flags .*.o.d
rm -f ar*/*~ ar*/*.o ar*/.*.cmd
rm -rf .tmp_versions
make[1]: Leaving directory `/root/madwifi-trunk-r4177-20120131/ath_hal'
make[1]: Entering directory `/root/madwifi-trunk-r4177-20120131/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
		make -C $i clean; \
	done
make[2]: Entering directory `/root/madwifi-trunk-r4177-20120131/ath_rate/amrr'
rm -f *~ *.o *.ko *.mod.c
rm -f modules.order .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/root/madwifi-trunk-r4177-20120131/ath_rate/amrr'
make[2]: Entering directory `/root/madwifi-trunk-r4177-20120131/ath_rate/onoe'
rm -f *~ *.o *.ko *.mod.c
rm -f modules.order .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/root/madwifi-trunk-r4177-20120131/ath_rate/onoe'
make[2]: Entering directory `/root/madwifi-trunk-r4177-20120131/ath_rate/sample'
rm -f *~ *.o *.ko *.mod.c
rm -f modules.order .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/root/madwifi-trunk-r4177-20120131/ath_rate/sample'
make[2]: Entering directory `/root/madwifi-trunk-r4177-20120131/ath_rate/minstrel'
rm -f *~ *.o *.ko *.mod.c
rm -f modules.order .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/root/madwifi-trunk-r4177-20120131/ath_rate/minstrel'
rm -f modules.order
make[1]: Leaving directory `/root/madwifi-trunk-r4177-20120131/ath_rate'
make[1]: Entering directory `/root/madwifi-trunk-r4177-20120131/net80211'
rm -f *~ *.o *.ko *.mod.c
rm -f modules.order .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[1]: Leaving directory `/root/madwifi-trunk-r4177-20120131/net80211'
make -C ./tools clean
make[1]: Entering directory `/root/madwifi-trunk-r4177-20120131/tools'
rm -f athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig wpakey core a.out
for d in ath_info; do \
		make -C $d clean; \
	done
make[2]: Entering directory `/root/madwifi-trunk-r4177-20120131/tools/ath_info'
rm -f *.o ath_info
make[2]: Leaving directory `/root/madwifi-trunk-r4177-20120131/tools/ath_info'
make[1]: Leaving directory `/root/madwifi-trunk-r4177-20120131/tools'
rm -rf .tmp_versions
rm -f modules.order *.symvers Module.markers svnversion.h
root@bt:~/madwifi-trunk-r4177-20120131# make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.38/build SUBDIRS=/root/madwifi-trunk-r4177-20120131 modules
make[1]: Entering directory `/usr/src/linux-source-2.6.38'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.38/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /root/madwifi-trunk-r4177-20120131/ath/if_ath.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath/if_ath_radar.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath/if_ath_hal_extensions.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath/if_ath_pci.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/ath/ath_pci.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ah.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ah_eeprom_v1.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ah_eeprom_v14.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ah_eeprom_v3.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ah_os.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ah_regdomain.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5210/ar5210_attach.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5210/ar5210_beacon.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5210/ar5210_interrupts.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5210/ar5210_keycache.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5210/ar5210_misc.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5210/ar5210_phy.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5210/ar5210_power.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5210/ar5210_recv.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5210/ar5210_reset.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5210/ar5210_xmit.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5211/ar5211_attach.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5211/ar5211_beacon.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5211/ar5211_interrupts.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5211/ar5211_keycache.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5211/ar5211_misc.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5211/ar5211_phy.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5211/ar5211_power.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5211/ar5211_recv.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5211/ar5211_reset.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5211/ar5211_xmit.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5212/ar2316.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5212/ar2317.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5212/ar2413.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5212/ar2425.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5212/ar5111.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5212/ar5112.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5212/ar5212_ani.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5212/ar5212_attach.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5212/ar5212_beacon.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5212/ar5212_eeprom.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5212/ar5212_gpio.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5212/ar5212_interrupts.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5212/ar5212_keycache.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5212/ar5212_misc.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5212/ar5212_phy.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5212/ar5212_power.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5212/ar5212_recv.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5212/ar5212_reset.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5212/ar5212_rfgain.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5212/ar5212_xmit.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5212/ar5413.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5416/ar2133.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5416/ar5416_ani.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5416/ar5416_attach.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5416/ar5416_beacon.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5416/ar5416_cal.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5416/ar5416_cal_adcdc.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5416/ar5416_cal_adcgain.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5416/ar5416_cal_iq.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5416/ar5416_eeprom.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5416/ar5416_gpio.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5416/ar5416_interrupts.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5416/ar5416_keycache.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5416/ar5416_misc.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5416/ar5416_phy.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5416/ar5416_power.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5416/ar5416_recv.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5416/ar5416_reset.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5416/ar5416_xmit.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5416/ar9160_attach.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5416/ar9280.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ar5416/ar9280_attach.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ath_hal.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_rate/amrr/amrr.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_rate/minstrel/minstrel.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/ath_rate/minstrel/ath_rate_minstrel.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_rate/onoe/onoe.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/ath_rate/sample/sample.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/ath_rate/sample/ath_rate_sample.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/net80211/if_media.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/net80211/ieee80211_skb.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/net80211/ieee80211.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/net80211/ieee80211_beacon.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/net80211/ieee80211_crypto.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/net80211/ieee80211_crypto_none.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/net80211/ieee80211_input.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/net80211/ieee80211_node.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/net80211/ieee80211_output.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/net80211/ieee80211_power.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/net80211/ieee80211_proto.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/net80211/ieee80211_scan.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/net80211/ieee80211_wireless.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/net80211/ieee80211_linux.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/net80211/ieee80211_monitor.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/net80211/ieee80211_rate.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/net80211/ieee80211_acl.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/net80211/ieee80211_crypto_ccmp.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/net80211/ieee80211_scan_ap.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/net80211/ieee80211_scan_sta.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/net80211/ieee80211_crypto_tkip.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/net80211/ieee80211_crypto_wep.o
  CC [M]  /root/madwifi-trunk-r4177-20120131/net80211/ieee80211_xauth.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/net80211/wlan.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/net80211/wlan_wep.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/net80211/wlan_tkip.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/net80211/wlan_ccmp.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/net80211/wlan_acl.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/net80211/wlan_xauth.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/net80211/wlan_scan_sta.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/net80211/wlan_scan_ap.o
  Building modules, stage 2.
  MODPOST 14 modules
  CC      /root/madwifi-trunk-r4177-20120131/ath/ath_pci.mod.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/ath/ath_pci.ko
  CC      /root/madwifi-trunk-r4177-20120131/ath_hal/ath_hal.mod.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/ath_hal/ath_hal.ko
  CC      /root/madwifi-trunk-r4177-20120131/ath_rate/amrr/ath_rate_amrr.mod.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/ath_rate/amrr/ath_rate_amrr.ko
  CC      /root/madwifi-trunk-r4177-20120131/ath_rate/minstrel/ath_rate_minstrel.mod.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/ath_rate/minstrel/ath_rate_minstrel.ko
  CC      /root/madwifi-trunk-r4177-20120131/ath_rate/onoe/ath_rate_onoe.mod.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/ath_rate/onoe/ath_rate_onoe.ko
  CC      /root/madwifi-trunk-r4177-20120131/ath_rate/sample/ath_rate_sample.mod.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/ath_rate/sample/ath_rate_sample.ko
  CC      /root/madwifi-trunk-r4177-20120131/net80211/wlan.mod.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/net80211/wlan.ko
  CC      /root/madwifi-trunk-r4177-20120131/net80211/wlan_acl.mod.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/net80211/wlan_acl.ko
  CC      /root/madwifi-trunk-r4177-20120131/net80211/wlan_ccmp.mod.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/net80211/wlan_ccmp.ko
  CC      /root/madwifi-trunk-r4177-20120131/net80211/wlan_scan_ap.mod.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/net80211/wlan_scan_ap.ko
  CC      /root/madwifi-trunk-r4177-20120131/net80211/wlan_scan_sta.mod.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/net80211/wlan_scan_sta.ko
  CC      /root/madwifi-trunk-r4177-20120131/net80211/wlan_tkip.mod.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/net80211/wlan_tkip.ko
  CC      /root/madwifi-trunk-r4177-20120131/net80211/wlan_wep.mod.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/net80211/wlan_wep.ko
  CC      /root/madwifi-trunk-r4177-20120131/net80211/wlan_xauth.mod.o
  LD [M]  /root/madwifi-trunk-r4177-20120131/net80211/wlan_xauth.ko
make[1]: Leaving directory `/usr/src/linux-source-2.6.38'
make -C ./tools all || exit 1
make[1]: Entering directory `/root/madwifi-trunk-r4177-20120131/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/root/madwifi-trunk-r4177-20120131/tools/ath_info'
gcc -g -O2 -W -Wall -D_FILE_OFFSET_BITS=64 -c ath_info.c
gcc -g -O2 -W -Wall  -o ath_info ath_info.o
make[2]: Leaving directory `/root/madwifi-trunk-r4177-20120131/tools/ath_info'
gcc -o athstats -g -O2 -Wall -I. -I../ath_hal -I.. -I../ath  athstats.c
athstats.c: In function 'main':
athstats.c:288: warning: format not a string literal and no format arguments
athstats.c:290: warning: format not a string literal and no format arguments
athstats.c:310: warning: format not a string literal and no format arguments
athstats.c:312: warning: format not a string literal and no format arguments
athstats.c:347: warning: format not a string literal and no format arguments
gcc -o 80211stats -g -O2 -Wall -I. -I../ath_hal -I..  80211stats.c
80211stats.c: In function 'main':
80211stats.c:287: warning: format not a string literal and no format arguments
gcc -o athkey -g -O2 -Wall -I. -I../ath_hal -I..  athkey.c
gcc -o athchans -g -O2 -Wall -I. -I../ath_hal -I..  athchans.c
gcc -o athctrl -g -O2 -Wall -I. -I../ath_hal -I..  athctrl.c
gcc -o athdebug -g -O2 -Wall -I. -I../ath_hal -I..  athdebug.c
gcc -o 80211debug -g -O2 -Wall -I. -I../ath_hal -I..  80211debug.c
gcc -o wlanconfig -g -O2 -Wall -I. -I../ath_hal -I..  wlanconfig.c
wlanconfig.c: In function 'list_keys':
wlanconfig.c:779: warning: ignoring return value of 'system', declared with attribute warn_unused_result
wlanconfig.c: In function 'ieee80211_status':
wlanconfig.c:895: warning: ignoring return value of 'system', declared with attribute warn_unused_result
gcc -o wpakey -g -O2 -Wall -I. -I../ath_hal -I..  wpakey.c
make[1]: Leaving directory `/root/madwifi-trunk-r4177-20120131/tools'
root@bt:~/madwifi-trunk-r4177-20120131# sudo make install
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.38/build SUBDIRS=/root/madwifi-trunk-r4177-20120131 modules
make[1]: Entering directory `/usr/src/linux-source-2.6.38'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.38/Module.symvers
           is missing; modules will have no dependencies and modversions.

  Building modules, stage 2.
  MODPOST 14 modules
make[1]: Leaving directory `/usr/src/linux-source-2.6.38'
sh scripts/find-madwifi-modules.sh -r 2.6.38 
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
		make -C $i install || exit 1; \
	done
make[1]: Entering directory `/root/madwifi-trunk-r4177-20120131/ath'
test -d //lib/modules/2.6.38/net || mkdir -p //lib/modules/2.6.38/net
install -m 0644 ath_pci.ko //lib/modules/2.6.38/net
make[1]: Leaving directory `/root/madwifi-trunk-r4177-20120131/ath'
make[1]: Entering directory `/root/madwifi-trunk-r4177-20120131/ath_hal'
test -d //lib/modules/2.6.38/net || mkdir -p //lib/modules/2.6.38/net
install -m 0644 ath_hal.ko //lib/modules/2.6.38/net
make[1]: Leaving directory `/root/madwifi-trunk-r4177-20120131/ath_hal'
make[1]: Entering directory `/root/madwifi-trunk-r4177-20120131/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
		make -C $i install || exit 1; \
	done
make[2]: Entering directory `/root/madwifi-trunk-r4177-20120131/ath_rate/amrr'
test -d //lib/modules/2.6.38/net || mkdir -p //lib/modules/2.6.38/net
install -m 0644 ath_rate_amrr.ko //lib/modules/2.6.38/net
make[2]: Leaving directory `/root/madwifi-trunk-r4177-20120131/ath_rate/amrr'
make[2]: Entering directory `/root/madwifi-trunk-r4177-20120131/ath_rate/onoe'
test -d //lib/modules/2.6.38/net || mkdir -p //lib/modules/2.6.38/net
install -m 0644 ath_rate_onoe.ko //lib/modules/2.6.38/net
make[2]: Leaving directory `/root/madwifi-trunk-r4177-20120131/ath_rate/onoe'
make[2]: Entering directory `/root/madwifi-trunk-r4177-20120131/ath_rate/sample'
test -d //lib/modules/2.6.38/net || mkdir -p //lib/modules/2.6.38/net
install -m 0644 ath_rate_sample.ko //lib/modules/2.6.38/net
make[2]: Leaving directory `/root/madwifi-trunk-r4177-20120131/ath_rate/sample'
make[2]: Entering directory `/root/madwifi-trunk-r4177-20120131/ath_rate/minstrel'
test -d //lib/modules/2.6.38/net || mkdir -p //lib/modules/2.6.38/net
install -m 0644 ath_rate_minstrel.ko //lib/modules/2.6.38/net
make[2]: Leaving directory `/root/madwifi-trunk-r4177-20120131/ath_rate/minstrel'
make[1]: Leaving directory `/root/madwifi-trunk-r4177-20120131/ath_rate'
make[1]: Entering directory `/root/madwifi-trunk-r4177-20120131/net80211'
test -d //lib/modules/2.6.38/net || mkdir -p //lib/modules/2.6.38/net
for i in wlan.o wlan_wep.o wlan_tkip.o wlan_ccmp.o wlan_acl.o wlan_xauth.o wlan_scan_sta.o wlan_scan_ap.o; do \
		f=`basename $i .o`; \
		install -m 0644  $f.ko //lib/modules/2.6.38/net; \
	done
make[1]: Leaving directory `/root/madwifi-trunk-r4177-20120131/net80211'
(export KMODPATH=/lib/modules/2.6.38/net; /sbin/depmod -ae 2.6.38)
WARNING: -e needs -E or -Fmake -C ./tools all || exit 1
make[1]: Entering directory `/root/madwifi-trunk-r4177-20120131/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/root/madwifi-trunk-r4177-20120131/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/root/madwifi-trunk-r4177-20120131/tools/ath_info'
make[1]: Leaving directory `/root/madwifi-trunk-r4177-20120131/tools'
make -C ./tools install || exit 1
make[1]: Entering directory `/root/madwifi-trunk-r4177-20120131/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/root/madwifi-trunk-r4177-20120131/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/root/madwifi-trunk-r4177-20120131/tools/ath_info'
install -d /usr/local/bin
for i in athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig wpakey; do \
		install $i /usr/local/bin/$i; \
		strip /usr/local/bin/$i; \
	done
install -d /usr/local/man/man8
install -m 0644 man/*.8 /usr/local/man/man8
install ../scripts/madwifi-unload /usr/local/bin/madwifi-unload
for d in ath_info; do \
		make -C $d install || exit 1; \
	done
make[2]: Entering directory `/root/madwifi-trunk-r4177-20120131/tools/ath_info'
install -d /usr/local/bin
install -m 755 ath_info /usr/local/bin
install -d /usr/local/share/man/man8
install -m 644 ath_info.8 /usr/local/share/man/man8
make[2]: Leaving directory `/root/madwifi-trunk-r4177-20120131/tools/ath_info'
make[1]: Leaving directory `/root/madwifi-trunk-r4177-20120131/tools'
root@bt:~/madwifi-trunk-r4177-20120131# sudo modprobe ath_pci
root@bt:~/madwifi-trunk-r4177-20120131# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@bt:~/madwifi-trunk-r4177-20120131# 
```

---

