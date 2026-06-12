---
title: "Installing Madwifi (problem !! HELP !)"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by bsharp42 on 2008-12-04
Hello,

   I am sort of new to linux, and I installed ubuntu last night. After installing, i noticed that my wired works, but my wireless doesn't work. So after searching the internet, found out i need to install madwifi for the atheros wireless chip that i have. Anyway, I installed all the build-essential,linux headers, gcc, g++, etc, and got the madwifi via subversion,

and after I make the

make clean 

I do,

make

in which I get the following errors.

jjhahnjj@JHahn-Laptop:~/madwifi$ make 
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/jjhahnjj/madwifi modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/jjhahnjj/madwifi/ath/if_ath.o
  CC [M]  /home/jjhahnjj/madwifi/ath/if_ath_radar.o
  CC [M]  /home/jjhahnjj/madwifi/ath/if_ath_hal_extensions.o
  CC [M]  /home/jjhahnjj/madwifi/ath/if_ath_pci.o
  LD [M]  /home/jjhahnjj/madwifi/ath/ath_pci.o
  CC [M]  /home/jjhahnjj/madwifi/ath_hal/ah_os.o
  HOSTCC  /home/jjhahnjj/madwifi/ath_hal/uudecode
  UUDECODE /home/jjhahnjj/madwifi/ath_hal/i386-elf.bin
  UNMANGLE /home/jjhahnjj/madwifi/ath_hal/i386-elf.hal.o
  LD [M]  /home/jjhahnjj/madwifi/ath_hal/ath_hal.o
  CC [M]  /home/jjhahnjj/madwifi/ath_rate/amrr/amrr.o
  LD [M]  /home/jjhahnjj/madwifi/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /home/jjhahnjj/madwifi/ath_rate/minstrel/minstrel.o
  LD [M]  /home/jjhahnjj/madwifi/ath_rate/minstrel/ath_rate_minstrel.o
  CC [M]  /home/jjhahnjj/madwifi/ath_rate/onoe/onoe.o
  LD [M]  /home/jjhahnjj/madwifi/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /home/jjhahnjj/madwifi/ath_rate/sample/sample.o
  LD [M]  /home/jjhahnjj/madwifi/ath_rate/sample/ath_rate_sample.o
  CC [M]  /home/jjhahnjj/madwifi/net80211/if_media.o
  CC [M]  /home/jjhahnjj/madwifi/net80211/ieee80211_skb.o
  CC [M]  /home/jjhahnjj/madwifi/net80211/ieee80211.o
  CC [M]  /home/jjhahnjj/madwifi/net80211/ieee80211_beacon.o
  CC [M]  /home/jjhahnjj/madwifi/net80211/ieee80211_crypto.o
  CC [M]  /home/jjhahnjj/madwifi/net80211/ieee80211_crypto_none.o
  CC [M]  /home/jjhahnjj/madwifi/net80211/ieee80211_input.o
  CC [M]  /home/jjhahnjj/madwifi/net80211/ieee80211_node.o
  CC [M]  /home/jjhahnjj/madwifi/net80211/ieee80211_output.o
  CC [M]  /home/jjhahnjj/madwifi/net80211/ieee80211_power.o
  CC [M]  /home/jjhahnjj/madwifi/net80211/ieee80211_proto.o
  CC [M]  /home/jjhahnjj/madwifi/net80211/ieee80211_scan.o
  CC [M]  /home/jjhahnjj/madwifi/net80211/ieee80211_wireless.o
  CC [M]  /home/jjhahnjj/madwifi/net80211/ieee80211_linux.o
  CC [M]  /home/jjhahnjj/madwifi/net80211/ieee80211_monitor.o
  CC [M]  /home/jjhahnjj/madwifi/net80211/ieee80211_rate.o
  CC [M]  /home/jjhahnjj/madwifi/net80211/ieee80211_acl.o
  CC [M]  /home/jjhahnjj/madwifi/net80211/ieee80211_crypto_ccmp.o
  CC [M]  /home/jjhahnjj/madwifi/net80211/ieee80211_scan_ap.o
  CC [M]  /home/jjhahnjj/madwifi/net80211/ieee80211_scan_sta.o
  CC [M]  /home/jjhahnjj/madwifi/net80211/ieee80211_crypto_tkip.o
  CC [M]  /home/jjhahnjj/madwifi/net80211/ieee80211_crypto_wep.o
  CC [M]  /home/jjhahnjj/madwifi/net80211/ieee80211_xauth.o
  LD [M]  /home/jjhahnjj/madwifi/net80211/wlan.o
  LD [M]  /home/jjhahnjj/madwifi/net80211/wlan_wep.o
  LD [M]  /home/jjhahnjj/madwifi/net80211/wlan_tkip.o
  LD [M]  /home/jjhahnjj/madwifi/net80211/wlan_ccmp.o
  LD [M]  /home/jjhahnjj/madwifi/net80211/wlan_acl.o
  LD [M]  /home/jjhahnjj/madwifi/net80211/wlan_xauth.o
  LD [M]  /home/jjhahnjj/madwifi/net80211/wlan_scan_sta.o
  LD [M]  /home/jjhahnjj/madwifi/net80211/wlan_scan_ap.o
  Building modules, stage 2.
  MODPOST 14 modules
  CC      /home/jjhahnjj/madwifi/ath/ath_pci.mod.o
  LD [M]  /home/jjhahnjj/madwifi/ath/ath_pci.ko
  CC      /home/jjhahnjj/madwifi/ath_hal/ath_hal.mod.o
  LD [M]  /home/jjhahnjj/madwifi/ath_hal/ath_hal.ko
  CC      /home/jjhahnjj/madwifi/ath_rate/amrr/ath_rate_amrr.mod.o
  LD [M]  /home/jjhahnjj/madwifi/ath_rate/amrr/ath_rate_amrr.ko
  CC      /home/jjhahnjj/madwifi/ath_rate/minstrel/ath_rate_minstrel.mod.o
  LD [M]  /home/jjhahnjj/madwifi/ath_rate/minstrel/ath_rate_minstrel.ko
  CC      /home/jjhahnjj/madwifi/ath_rate/onoe/ath_rate_onoe.mod.o
  LD [M]  /home/jjhahnjj/madwifi/ath_rate/onoe/ath_rate_onoe.ko
  CC      /home/jjhahnjj/madwifi/ath_rate/sample/ath_rate_sample.mod.o
  LD [M]  /home/jjhahnjj/madwifi/ath_rate/sample/ath_rate_sample.ko
  CC      /home/jjhahnjj/madwifi/net80211/wlan.mod.o
  LD [M]  /home/jjhahnjj/madwifi/net80211/wlan.ko
  CC      /home/jjhahnjj/madwifi/net80211/wlan_acl.mod.o
  LD [M]  /home/jjhahnjj/madwifi/net80211/wlan_acl.ko
  CC      /home/jjhahnjj/madwifi/net80211/wlan_ccmp.mod.o
  LD [M]  /home/jjhahnjj/madwifi/net80211/wlan_ccmp.ko
  CC      /home/jjhahnjj/madwifi/net80211/wlan_scan_ap.mod.o
  LD [M]  /home/jjhahnjj/madwifi/net80211/wlan_scan_ap.ko
  CC      /home/jjhahnjj/madwifi/net80211/wlan_scan_sta.mod.o
  LD [M]  /home/jjhahnjj/madwifi/net80211/wlan_scan_sta.ko
  CC      /home/jjhahnjj/madwifi/net80211/wlan_tkip.mod.o
  LD [M]  /home/jjhahnjj/madwifi/net80211/wlan_tkip.ko
  CC      /home/jjhahnjj/madwifi/net80211/wlan_wep.mod.o
  LD [M]  /home/jjhahnjj/madwifi/net80211/wlan_wep.ko
  CC      /home/jjhahnjj/madwifi/net80211/wlan_xauth.mod.o
  LD [M]  /home/jjhahnjj/madwifi/net80211/wlan_xauth.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make -C ./tools all || exit 1
make[1]: Entering directory `/home/jjhahnjj/madwifi/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/jjhahnjj/madwifi/tools/ath_info'
gcc -g -O2 -W -Wall -c ath_info.c
ath_info.c: In function 'main':
ath_info.c:2841: warning: ignoring return value of 'fwrite', declared with attribute warn_unused_result
gcc -g -O2 -W -Wall  -o ath_info ath_info.o
make[2]: Leaving directory `/home/jjhahnjj/madwifi/tools/ath_info'
gcc -o athstats -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal -I../ath  athstats.c
athstats.c: In function 'main':
athstats.c:289: warning: format not a string literal and no format arguments
athstats.c:291: warning: format not a string literal and no format arguments
athstats.c:311: warning: format not a string literal and no format arguments
athstats.c:313: warning: format not a string literal and no format arguments
athstats.c:348: warning: format not a string literal and no format arguments
gcc -o 80211stats -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  80211stats.c
80211stats.c: In function 'main':
80211stats.c:287: warning: format not a string literal and no format arguments
gcc -o athkey -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athkey.c
gcc -o athchans -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athchans.c
gcc -o athctrl -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athctrl.c
gcc -o athdebug -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athdebug.c
gcc -o 80211debug -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  80211debug.c
gcc -o wlanconfig -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  wlanconfig.c
wlanconfig.c: In function 'list_keys':
wlanconfig.c:779: warning: ignoring return value of 'system', declared with attribute warn_unused_result
wlanconfig.c: In function 'ieee80211_status':
wlanconfig.c:895: warning: ignoring return value of 'system', declared with attribute warn_unused_result
gcc -o wpakey -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  wpakey.c
make[1]: Leaving directory `/home/jjhahnjj/madwifi/tools'
jjhahnjj@JHahn-Laptop:~/madwifi$ 




anytype of help would be appreciated !!

---

