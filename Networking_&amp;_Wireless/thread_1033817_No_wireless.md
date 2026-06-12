---
title: "No wireless"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by BRFC on 2009-01-07
Hi people my mum has just bought herself a new laptop and wants me to install Ubuntu on it, she has been running 7.10 for about 6 months on an old laptop of mine and she likes the setup so wants it on her new one.  I downloaded 8.10 thinking new laptop latest version probably best option.  

I ran the Live CD and the wireless didn't work, so I thought rightly or wrongly well I'll do the install and maybe it'll work (happened last time with old laptop). Well I've just finished the install and the wireless doesn't work.

A quick look at Help told me to run this, sudo lshw -C network, in terminal to see whether the device was turned on, which I did and it came back with loads of stuff but the bit that was mentioned in the Help file said, Disabled, meaning that the device is turn off. There is a little switch on the front of the machine to turn the wireless on/off and its on.
The annoying thing is she booted it up with the pre-installed Vista and it found the network straight away but bless my mum she said "I don't want all this nonsense I want the one with the penguin".

Can anyone give me anymore help, I'm stuck now with a new laptop that my recently retired mum bought herself to keep in touch with my brother who now lives in Australia

Laptop is a Toshiba L300-13S

lspci gives

mum@mum-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

I'd be grateful if someone could talk/walk me through a solution.

Chris

---

### Post by lemmy999 on 2009-01-07
Posting the output of ```
sudo lshw -C network
``` will certainly help  us to identify what chipset Moms laptop is running.

And I hate it when the OP posts the info I have just asked for whilst I'm posting.:-)

---

### Post by lemmy999 on 2009-01-07
chris

It "looks" like that lappy has an atheros wifi chipset. If that is the case then try the following post -http://ubuntuforums.org/showthread.php?t=1022311 to install the madwifi drivers that should make the wifi work

---

### Post by BRFC on 2009-01-08
Ok I followed the instructions in the first post of the link that you suggested lemmy999, still no wireless, this is the process in terminal, I had to connect the laptop to my router via ethernet cable would this make a difference to how it was trying to set thing up.  Any help would be great as I'm used to it just working.

Cheers 

Chris


mum@mum-laptop:~$ cd /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204
mum@mum-laptop:~/Documents/madwifi-hal-0.10.5.6-r3879-20081204$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath/if_ath.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath/if_ath_radar.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath/if_ath_hal_extensions.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath/if_ath_pci.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath/ath_pci.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_hal/ah_os.o
  HOSTCC  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_hal/uudecode
  UUDECODE /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_hal/i386-elf._hal.o
  UNMANGLE /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_hal/i386-elf.hal.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_hal/ath_hal.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate/amrr/amrr.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate/minstrel/minstrel.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate/minstrel/ath_rate_minstrel.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate/onoe/onoe.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate/sample/sample.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate/sample/ath_rate_sample.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/if_media.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/ieee80211_skb.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/ieee80211.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/ieee80211_beacon.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/ieee80211_crypto.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/ieee80211_crypto_none.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/ieee80211_input.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/ieee80211_node.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/ieee80211_output.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/ieee80211_power.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/ieee80211_proto.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/ieee80211_scan.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/ieee80211_wireless.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/ieee80211_linux.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/ieee80211_monitor.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/ieee80211_rate.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/ieee80211_acl.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/ieee80211_crypto_ccmp.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/ieee80211_scan_ap.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/ieee80211_scan_sta.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/ieee80211_crypto_tkip.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/ieee80211_crypto_wep.o
  CC [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/ieee80211_xauth.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/wlan.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/wlan_wep.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/wlan_tkip.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/wlan_ccmp.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/wlan_acl.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/wlan_xauth.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/wlan_scan_sta.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/wlan_scan_ap.o
  Building modules, stage 2.
  MODPOST 14 modules
  CC      /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath/ath_pci.mod.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath/ath_pci.ko
  CC      /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_hal/ath_hal.mod.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_hal/ath_hal.ko
  CC      /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate/amrr/ath_rate_amrr.mod.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate/amrr/ath_rate_amrr.ko
  CC      /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate/minstrel/ath_rate_minstrel.mod.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate/minstrel/ath_rate_minstrel.ko
  CC      /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate/onoe/ath_rate_onoe.mod.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate/onoe/ath_rate_onoe.ko
  CC      /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate/sample/ath_rate_sample.mod.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate/sample/ath_rate_sample.ko
  CC      /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/wlan.mod.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/wlan.ko
  CC      /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/wlan_acl.mod.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/wlan_acl.ko
  CC      /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/wlan_ccmp.mod.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/wlan_ccmp.ko
  CC      /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/wlan_scan_ap.mod.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/wlan_scan_ap.ko
  CC      /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/wlan_scan_sta.mod.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/wlan_scan_sta.ko
  CC      /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/wlan_tkip.mod.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/wlan_tkip.ko
  CC      /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/wlan_wep.mod.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/wlan_wep.ko
  CC      /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/wlan_xauth.mod.o
  LD [M]  /home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211/wlan_xauth.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make -C ./tools all || exit 1
make[1]: Entering directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/tools/ath_info'
gcc -g -O2 -W -Wall -c ath_info.c
ath_info.c: In function 'main':
ath_info.c:2841: warning: ignoring return value of 'fwrite', declared with attribute warn_unused_result
gcc -g -O2 -W -Wall  -o ath_info ath_info.o
make[2]: Leaving directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/tools/ath_info'
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
make[1]: Leaving directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/tools'
mum@mum-laptop:~/Documents/madwifi-hal-0.10.5.6-r3879-20081204$ sudo make install
[sudo] password for mum: 
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  Building modules, stage 2.
  MODPOST 14 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
sh scripts/find-madwifi-modules.sh -r 2.6.27-7-generic 
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
		make -C $i install || exit 1; \
	done
make[1]: Entering directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath'
test -d //lib/modules/2.6.27-7-generic/net || mkdir -p //lib/modules/2.6.27-7-generic/net
install -m 0644 ath_pci.ko //lib/modules/2.6.27-7-generic/net
make[1]: Leaving directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath'
make[1]: Entering directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_hal'
test -d //lib/modules/2.6.27-7-generic/net || mkdir -p //lib/modules/2.6.27-7-generic/net
install -m 0644 ath_hal.ko //lib/modules/2.6.27-7-generic/net
make[1]: Leaving directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_hal'
make[1]: Entering directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
		make -C $i install || exit 1; \
	done
make[2]: Entering directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate/amrr'
test -d //lib/modules/2.6.27-7-generic/net || mkdir -p //lib/modules/2.6.27-7-generic/net
install -m 0644 ath_rate_amrr.ko //lib/modules/2.6.27-7-generic/net
make[2]: Leaving directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate/amrr'
make[2]: Entering directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate/onoe'
test -d //lib/modules/2.6.27-7-generic/net || mkdir -p //lib/modules/2.6.27-7-generic/net
install -m 0644 ath_rate_onoe.ko //lib/modules/2.6.27-7-generic/net
make[2]: Leaving directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate/onoe'
make[2]: Entering directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate/sample'
test -d //lib/modules/2.6.27-7-generic/net || mkdir -p //lib/modules/2.6.27-7-generic/net
install -m 0644 ath_rate_sample.ko //lib/modules/2.6.27-7-generic/net
make[2]: Leaving directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate/sample'
make[2]: Entering directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate/minstrel'
test -d //lib/modules/2.6.27-7-generic/net || mkdir -p //lib/modules/2.6.27-7-generic/net
install -m 0644 ath_rate_minstrel.ko //lib/modules/2.6.27-7-generic/net
make[2]: Leaving directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate/minstrel'
make[1]: Leaving directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/ath_rate'
make[1]: Entering directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211'
test -d //lib/modules/2.6.27-7-generic/net || mkdir -p //lib/modules/2.6.27-7-generic/net
for i in wlan.o wlan_wep.o wlan_tkip.o wlan_ccmp.o wlan_acl.o wlan_xauth.o wlan_scan_sta.o wlan_scan_ap.o; do \
		f=`basename $i .o`; \
		install -m 0644  $f.ko //lib/modules/2.6.27-7-generic/net; \
	done
make[1]: Leaving directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/net80211'
(export KMODPATH=/lib/modules/2.6.27-7-generic/net; /sbin/depmod -ae 2.6.27-7-generic)
make -C ./tools all || exit 1
make[1]: Entering directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/tools/ath_info'
make[1]: Leaving directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/tools'
make -C ./tools install || exit 1
make[1]: Entering directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/tools/ath_info'
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
make[2]: Entering directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/tools/ath_info'
install -d /usr/local/bin
install -m 755 ath_info /usr/local/bin
install -d /usr/local/share/man/man8
install -m 644 ath_info.8 /usr/local/share/man/man8
make[2]: Leaving directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/tools/ath_info'
make[1]: Leaving directory `/home/mum/Documents/madwifi-hal-0.10.5.6-r3879-20081204/tools'
mum@mum-laptop:~/Documents/madwifi-hal-0.10.5.6-r3879-20081204$ modprobe ath_pciWARNING: Error inserting ath_hal (/lib/modules/2.6.27-7-generic/net/ath_hal.ko): Operation not permitted
WARNING: Error inserting wlan (/lib/modules/2.6.27-7-generic/net/wlan.ko): Operation not permitted
FATAL: Error inserting ath_pci (/lib/modules/2.6.27-7-generic/net/ath_pci.ko): Operation not permitted
mum@mum-laptop:~/Documents/madwifi-hal-0.10.5.6-r3879-20081204$

---

### Post by BRFC on 2009-01-09
Anyone got any ideas otherwise I'm stuck and my mum will just have to use Vista :(

---

### Post by lemmy999 on 2009-01-11
Are you using the 32 bit or 64 bit OS?

It might be worth d/l'ing a copy of the 32bit version of 7.10 and trying that as a live CD.

---

