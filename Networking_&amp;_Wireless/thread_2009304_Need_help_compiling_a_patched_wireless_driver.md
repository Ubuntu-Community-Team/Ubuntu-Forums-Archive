---
title: "Need help compiling a patched wireless driver"
date: 2012-06-24
forum: Networking &amp; Wireless
---

### Post by RazeRules on 2012-06-24
Hi,

I was trying to compile a patched wireless driver using this [guide]("http://www.aircrack-ng.org/doku.php?id=iwlagn"), when I end up with no wireless driver at all.

Probably something went wrong through this process:
```
cd ~
 tar xjf compat-wireless-2.6.tar.bz2
 cd compat-wireless-2009-*
 wget http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch
 patch -p1 < mac80211_2.6.28-rc4-wl_frag+ack_v3.patch
 wget http://patches.aircrack-ng.org/mac80211-2.6.29-fix-tx-ctl-no-ack-retry-count.patch
 patch -p1 < mac80211-2.6.29-fix-tx-ctl-no-ack-retry-count.patch
 make -j4
 make unload [as root!]
 make install [as root!]
 echo options iwlagn swcrypto=1 >> /etc/modprobe.d/options [as root!]
 make load [as root!]
```

There was some errors running those lines:
```
patch -p1 < mac80211_2.6.28-rc4-wl_frag+ack_v3.patch
```
```
sudo echo options iwlagn swcrypto=1 >> /etc/modprobe.d/options
```

Here's the full output for the process above:
```
raze@Raze-Station-U:~$ tar xjf compat-wireless-2.6.tar.bz2 
raze@Raze-Station-U:~$ cd compat-wireless-2012-05-10/
raze@Raze-Station-U:~/compat-wireless-2012-05-10$ wget http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch
--2012-06-24 17:16:00--  http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v3.patch
Resolving patches.aircrack-ng.org (patches.aircrack-ng.org)... 213.186.33.2
Connecting to patches.aircrack-ng.org (patches.aircrack-ng.org)|213.186.33.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1063 (1.0K) [text/plain]
Saving to: `mac80211_2.6.28-rc4-wl_frag+ack_v3.patch'

100%[==========================================================>] 1,063       --.-K/s   in 0s      

2012-06-24 17:16:21 (50.9 MB/s) - `mac80211_2.6.28-rc4-wl_frag+ack_v3.patch' saved [1063/1063]

raze@Raze-Station-U:~/compat-wireless-2012-05-10$ patch -p1 < mac80211_2.6.28-rc4-wl_frag+ack_v3.patch
patching file net/mac80211/tx.c
Hunk #1 FAILED at 611.
1 out of 1 hunk FAILED -- saving rejects to file net/mac80211/tx.c.rej
raze@Raze-Station-U:~/compat-wireless-2012-05-10$ wget http://patches.aircrack-ng.org/mac80211-2.6.29-fix-tx-ctl-no-ack-retry-count.patch
--2012-06-24 17:23:43--  http://patches.aircrack-ng.org/mac80211-2.6.29-fix-tx-ctl-no-ack-retry-count.patch
Resolving patches.aircrack-ng.org (patches.aircrack-ng.org)... 213.186.33.2
Connecting to patches.aircrack-ng.org (patches.aircrack-ng.org)|213.186.33.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 559 [text/plain]
Saving to: `mac80211-2.6.29-fix-tx-ctl-no-ack-retry-count.patch'

100%[==========================================================>] 559         --.-K/s   in 0s      

2012-06-24 17:24:03 (39.1 MB/s) - `mac80211-2.6.29-fix-tx-ctl-no-ack-retry-count.patch' saved [559/559]

raze@Raze-Station-U:~/compat-wireless-2012-05-10$ patch -p1 < mac80211-2.6.29-fix-tx-ctl-no-ack-retry-count.patch
patching file net/mac80211/tx.c
Hunk #1 succeeded at 697 with fuzz 1 (offset 158 lines).

raze@Raze-Station-U:~/compat-wireless-2012-05-10$ make -j4
./scripts/gen-compat-autoconf.sh /home/raze/compat-wireless-2012-05-10/.config /home/raze/compat-wireless-2012-05-10/config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/3.2.0-25-generic-pae/build M=/home/raze/compat-wireless-2012-05-10 modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-25-generic-pae'
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bcma/main.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/compat/main.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/hci_vhci.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/misc/eeprom/eeprom_93cx6.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/compat/compat-3.3.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/compat/compat-3.5.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bcma/scan.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btmrvl_main.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bcma/core.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/compat/compat_atomic.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bcma/sprom.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/compat/compat.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/atheros/atl1c/atl1c_main.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btmrvl_debugfs.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bcma/driver_chipcommon.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/hci_ldisc.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/hci_h4.o
In file included from /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/hci_ldisc.c:37:0:
include/linux/tty.h:607:1: warning: function declaration isn’t a prototype [-Wstrict-prototypes]
include/linux/tty.h:608:1: warning: function declaration isn’t a prototype [-Wstrict-prototypes]
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bcma/driver_chipcommon_pmu.o
In file included from /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/hci_h4.c:37:0:
include/linux/tty.h:607:1: warning: function declaration isn’t a prototype [-Wstrict-prototypes]
include/linux/tty.h:608:1: warning: function declaration isn’t a prototype [-Wstrict-prototypes]
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/hci_bcsp.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/hci_ll.o
In file included from /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/hci_bcsp.c:36:0:
include/linux/tty.h:607:1: warning: function declaration isn’t a prototype [-Wstrict-prototypes]
include/linux/tty.h:608:1: warning: function declaration isn’t a prototype [-Wstrict-prototypes]
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/atheros/atl1c/atl1c_hw.o
In file included from /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/hci_ll.c:42:0:
include/linux/tty.h:607:1: warning: function declaration isn’t a prototype [-Wstrict-prototypes]
include/linux/tty.h:608:1: warning: function declaration isn’t a prototype [-Wstrict-prototypes]
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/hci_ath.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/bcm203x.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bcma/driver_pci.o
In file included from /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/hci_ath.c:34:0:
include/linux/tty.h:607:1: warning: function declaration isn’t a prototype [-Wstrict-prototypes]
include/linux/tty.h:608:1: warning: function declaration isn’t a prototype [-Wstrict-prototypes]
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/bpa10x.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/atheros/atl1c/atl1c_ethtool.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bcma/host_pci.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/bfusb.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/bcma/bcma.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/broadcom/b44.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/atheros/atl1e/atl1e_main.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/atheros/atl1c/atl1c.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/atheros/atl1e/atl1e_hw.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/dtl1_cs.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/atheros/atl1e/atl1e_ethtool.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/bt3c_cs.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/usb/cdc_ether.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/atheros/atl1e/atl1e_param.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/bluecard_cs.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/usb/rndis_host.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/atheros/atl1e/atl1e.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/atheros/atlx/atl1.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btuart_cs.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btusb.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/usb/usbnet.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btsdio.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/ath3k.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/at76c50x-usb.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btmrvl.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btmrvl_sdio.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/atheros/atlx/atl2.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btwilink.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/hci_uart.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rndis_wlan.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/adm8211.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/mwl8k.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/ssb/main.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/mac80211_hwsim.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/main.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/ssb/scan.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/regd.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/main.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/hw.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/ssb/sprom.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/key.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/ssb/pci.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath5k/caps.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath5k/initvals.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/debug.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/ssb/pcihost_wrapper.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/bus.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath5k/eeprom.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/hif.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/ssb/pcmcia.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/tables.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/tables_nphy.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/htc_mbox.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/ssb/sdio.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath5k/gpio.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/radio_2055.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/ssb/driver_chipcommon.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath5k/desc.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/radio_2056.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/ssb/driver_chipcommon_pmu.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath5k/dma.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/htc_pipe.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath5k/qcu.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/ssb/driver_pcicore.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/phy_common.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/bmi.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath5k/pcu.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/phy_g.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/cfg80211.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/ssb/b43_pci_bridge.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath5k/phy.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/ssb/ssb.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/af_bluetooth.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/hci_core.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/phy_a.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/init.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath5k/reset.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/phy_n.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath5k/attach.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/main.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/hci_conn.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath5k/base.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/txrx.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/hci_event.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/phy_lp.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath5k/led.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/wmi.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath5k/rfkill.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath5k/ani.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/tables_lpphy.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath5k/sysfs.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/phy_ht.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/core.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/mgmt.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath5k/mac80211-ops.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/tables_phy_ht.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/testmode.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath5k/pci.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/radio_2059.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/sdio.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath5k/ath5k.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/usb.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/sysfs.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/hci_sock.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/xmit.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43legacy/main.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/ath6kl_core.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/ath6kl_sdio.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/ath6kl_usb.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/beacon.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/hci_sysfs.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/lo.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/gpio.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/init.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/wa.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/l2cap_core.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43legacy/ilt.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/main.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43legacy/phy.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/dma.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/recv.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/pio.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/rfkill.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43legacy/radio.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/xmit.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/l2cap_sock.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/leds.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/smp.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/pcmcia.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43legacy/sysfs.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/sdio.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43legacy/xmit.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/mci.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/sco.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/b43.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/main.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/rc.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43legacy/rfkill.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/lib.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43legacy/leds.o
/home/raze/compat-wireless-2012-05-10/net/bluetooth/lib.c:27:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
/home/raze/compat-wireless-2012-05-10/net/bluetooth/lib.c:27:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/status.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/pci.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/bnep/core.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43legacy/debugfs.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/ahb.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43legacy/dma.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/bnep/sock.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/sta_info.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/debug.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/bnep/netdev.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43legacy/pio.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/bnep/bnep.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/cmtp/core.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43legacy/b43legacy.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/cmtp/sock.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/common.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/wep.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/cmtp/capi.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/wpa.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211/brcmfmac/wl_cfg80211.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/htc_hst.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/cmtp/cmtp.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/hidp/core.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/scan.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/hif_usb.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/hidp/sock.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/wmi.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/offchannel.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211/brcmfmac/dhd_cdc.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/hidp/hidp.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/rfcomm/core.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/htc_drv_txrx.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211/brcmfmac/dhd_common.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/ht.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211/brcmfmac/dhd_linux.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/rfcomm/sock.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/htc_drv_main.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/agg-tx.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211/brcmfmac/dhd_sdio.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/rfcomm/tty.o
In file included from /home/raze/compat-wireless-2012-05-10/net/bluetooth/rfcomm/tty.c:30:0:
include/linux/tty.h:607:1: warning: function declaration isn’t a prototype [-Wstrict-prototypes]
include/linux/tty.h:608:1: warning: function declaration isn’t a prototype [-Wstrict-prototypes]
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/htc_drv_beacon.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/agg-rx.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/rfcomm/rfcomm.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/bluetooth.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/rfkill/rfkill-regulator.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/htc_drv_init.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/core.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211/brcmfmac/bcmsdh.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/ibss.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/htc_drv_gpio.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211/brcmfmac/bcmsdh_sdmmc.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/sysfs.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/work.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/htc_drv_debug.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/radiotap.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211/brcmfmac/sdio_chip.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/iface.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/util.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211/brcmfmac/usb.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/ar9002_hw.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/ar9003_hw.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/rate.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211/brcmfmac/brcmfmac.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211/brcmsmac/mac80211_if.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/reg.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/hw.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/michael.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211/brcmsmac/ucode_loader.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/tkip.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/scan.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211/brcmsmac/ampdu.o
^Cmake[3]: *** [/home/raze/compat-wireless-2012-05-10/net/wireless/scan.o] Interrupt
make[3]: make[5]: make[2]: *** [/home/raze/compat-wireless-2012-05-10/net/wireless] Interrupt
make[5]: *** [/home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/hw.o] Interrupt
make[4]: *** [/home/raze/compat-wireless-2012-05-10/net/mac80211/tkip.o] Interrupt*** [/home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k] Interrupt

make[3]: *** [/home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath] Interruptmake[2]: *** [/home/raze/compat-wireless-2012-05-10/net/mac80211] Interrupt
*** [/home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211/brcmsmac/ampdu.o] Interrupt

make[4]: *** [/home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211/brcmsmac] Interrupt
make[3]: *** [/home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211] Interrupt
make[2]: *** [/home/raze/compat-wireless-2012-05-10/drivers/net/wireless] Interrupt
make[1]: *** [_module_/home/raze/compat-wireless-2012-05-10] Interrupt
make: *** [modules] Interrupt

raze@Raze-Station-U:~/compat-wireless-2012-05-10$ sudo make unload
[sudo] password for raze: 
Stoping bluetooth service..
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service bluetooth stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop bluetooth
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service bluetooth status

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the status(8) utility, e.g. status bluetooth
bluetooth stop/waiting

raze@Raze-Station-U:~/compat-wireless-2012-05-10$ sudo make install

		(!SOME OUTPUT MISSING HERE!)

  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192de/dm.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192de/fw.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192de/hw.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192de/led.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192de/phy.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192de/rf.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192de/sw.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192de/table.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192de/trx.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192se/dm.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192se/fw.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192se/hw.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192se/led.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192se/phy.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192se/rf.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192se/sw.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192se/table.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192se/trx.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/main.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/event.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/tx.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/rx.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/ps.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/cmd.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/acx.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/boot.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/init.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/debugfs.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/io.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/sdio.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/spi.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/wl1251.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/wl1251_spi.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/wl1251_sdio.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl12xx/main.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl12xx/cmd.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl12xx/acx.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl12xx/wl12xx.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/main.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/cmd.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/io.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/event.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/tx.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/rx.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/ps.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/acx.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/boot.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/init.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/debugfs.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/scan.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/testmode.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/sdio.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/spi.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/wlcore.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/wlcore_spi.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/wlcore_sdio.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/zd1211rw/zd_chip.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/zd1211rw/zd_mac.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/zd1211rw/zd_rf_al2230.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/zd1211rw/zd_rf_rf2959.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/zd1211rw/zd_rf_al7230b.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/zd1211rw/zd_rf_uw2453.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/zd1211rw/zd_rf.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/zd1211rw/zd_usb.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/zd1211rw/zd1211rw.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/tkip.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/aes_ccm.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/aes_cmac.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/cfg.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/rx.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/spectmgmt.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/tx.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/key.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/util.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/wme.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/event.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/chan.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/mlme.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/driver-trace.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/led.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/debugfs.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/debugfs_sta.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/debugfs_netdev.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/debugfs_key.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/mesh.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/mesh_pathtbl.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/mesh_plink.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/mesh_hwmp.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/mesh_sync.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/pm.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/rc80211_pid_algo.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/rc80211_pid_debugfs.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/rc80211_minstrel.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/rc80211_minstrel_debugfs.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/rc80211_minstrel_ht.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/rc80211_minstrel_ht_debugfs.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/mac80211.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/scan.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/nl80211.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/mlme.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/ibss.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/sme.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/chan.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/ethtool.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/mesh.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/debugfs.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/wext-compat.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/wext-sme.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/cfg80211.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/lib80211.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/lib80211_crypt_wep.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/lib80211_crypt_ccmp.o
  CC [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/lib80211_crypt_tkip.o
  Building modules, stage 2.
  MODPOST 116 modules
  CC      /home/raze/compat-wireless-2012-05-10/compat/compat.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/compat/compat.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/bcma/bcma.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/bcma/bcma.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/ath3k.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/ath3k.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/bcm203x.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/bcm203x.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/bfusb.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/bfusb.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/bluecard_cs.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/bluecard_cs.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/bpa10x.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/bpa10x.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/bt3c_cs.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/bt3c_cs.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btmrvl.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btmrvl.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btmrvl_sdio.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btmrvl_sdio.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btsdio.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btsdio.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btuart_cs.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btuart_cs.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btusb.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btusb.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btwilink.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btwilink.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/dtl1_cs.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/dtl1_cs.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/hci_uart.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/hci_uart.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/hci_vhci.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/hci_vhci.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/misc/eeprom/eeprom_93cx6.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/misc/eeprom/eeprom_93cx6.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/atheros/atl1c/atl1c.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/atheros/atl1c/atl1c.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/atheros/atl1e/atl1e.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/atheros/atl1e/atl1e.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/atheros/atlx/atl1.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/atheros/atlx/atl1.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/atheros/atlx/atl2.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/atheros/atlx/atl2.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/broadcom/b44.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/broadcom/b44.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/usb/cdc_ether.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/usb/cdc_ether.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/usb/rndis_host.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/usb/rndis_host.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/usb/usbnet.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/usb/usbnet.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/adm8211.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/adm8211.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/at76c50x-usb.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/at76c50x-usb.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath5k/ath5k.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath5k/ath5k.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/ath6kl_core.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/ath6kl_core.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/ath6kl_sdio.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/ath6kl_sdio.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/ath6kl_usb.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/ath6kl_usb.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/ath9k.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/ath9k.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/ath9k_common.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/ath9k_common.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/ath9k_htc.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/ath9k_hw.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/carl9170/carl9170.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/carl9170/carl9170.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/b43.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/b43.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43legacy/b43legacy.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43legacy/b43legacy.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211/brcmfmac/brcmfmac.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211/brcmfmac/brcmfmac.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211/brcmutil/brcmutil.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ipw2x00/ipw2100.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ipw2x00/ipw2100.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ipw2x00/ipw2200.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ipw2x00/ipw2200.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ipw2x00/libipw.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ipw2x00/libipw.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/iwlegacy/iwl3945.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/iwlegacy/iwl3945.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/iwlegacy/iwl4965.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/iwlegacy/iwl4965.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/iwlegacy/iwlegacy.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/iwlegacy/iwlegacy.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwlwifi.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwlwifi.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/libertas/libertas.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/libertas/libertas.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/libertas/libertas_cs.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/libertas/libertas_cs.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/libertas/libertas_sdio.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/libertas/libertas_sdio.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/libertas/libertas_spi.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/libertas/libertas_spi.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/libertas/usb8xxx.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/libertas/usb8xxx.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/libertas_tf/libertas_tf.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/libertas_tf/libertas_tf.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/libertas_tf/libertas_tf_usb.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/mac80211_hwsim.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/mac80211_hwsim.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/mwifiex/mwifiex.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/mwifiex/mwifiex.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/mwifiex/mwifiex_pcie.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/mwifiex/mwifiex_pcie.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/mwifiex/mwifiex_sdio.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/mwifiex/mwifiex_sdio.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/mwl8k.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/mwl8k.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/orinoco/orinoco.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/orinoco/orinoco.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/orinoco/orinoco_cs.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/orinoco/orinoco_cs.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/orinoco/orinoco_nortel.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/orinoco/orinoco_nortel.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/orinoco/orinoco_pci.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/orinoco/orinoco_pci.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/orinoco/orinoco_plx.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/orinoco/orinoco_plx.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/orinoco/orinoco_tmd.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/orinoco/orinoco_tmd.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/orinoco/orinoco_usb.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/orinoco/orinoco_usb.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/orinoco/spectrum_cs.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/orinoco/spectrum_cs.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/p54/p54common.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/p54/p54common.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/p54/p54pci.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/p54/p54pci.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/p54/p54spi.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/p54/p54spi.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/p54/p54usb.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/p54/p54usb.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rndis_wlan.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rndis_wlan.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2400pci.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2400pci.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2500pci.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2500pci.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2500usb.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2500usb.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2800lib.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2800lib.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2800pci.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2800pci.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2800usb.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2800usb.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2x00lib.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2x00lib.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2x00pci.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2x00pci.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2x00usb.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2x00usb.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt61pci.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt61pci.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt73usb.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt73usb.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtl818x/rtl8180/rtl8180.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtl818x/rtl8180/rtl8180.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtl818x/rtl8187/rtl8187.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtlwifi.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtlwifi.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/wl1251.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/wl1251.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/wl1251_sdio.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/wl1251_sdio.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/wl1251_spi.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/wl1251_spi.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl12xx/wl12xx.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl12xx/wl12xx.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/wlcore.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/wlcore.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/wlcore_sdio.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/wlcore_sdio.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/wlcore_spi.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/wlcore_spi.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/zd1211rw/zd1211rw.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/zd1211rw/zd1211rw.ko
  CC      /home/raze/compat-wireless-2012-05-10/drivers/ssb/ssb.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/drivers/ssb/ssb.ko
  CC      /home/raze/compat-wireless-2012-05-10/net/bluetooth/bluetooth.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/bluetooth.ko
  CC      /home/raze/compat-wireless-2012-05-10/net/bluetooth/bnep/bnep.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/bnep/bnep.ko
  CC      /home/raze/compat-wireless-2012-05-10/net/bluetooth/cmtp/cmtp.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/cmtp/cmtp.ko
  CC      /home/raze/compat-wireless-2012-05-10/net/bluetooth/hidp/hidp.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/hidp/hidp.ko
  CC      /home/raze/compat-wireless-2012-05-10/net/bluetooth/rfcomm/rfcomm.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/net/bluetooth/rfcomm/rfcomm.ko
  CC      /home/raze/compat-wireless-2012-05-10/net/mac80211/mac80211.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/net/mac80211/mac80211.ko
  CC      /home/raze/compat-wireless-2012-05-10/net/rfkill/rfkill-regulator.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/net/rfkill/rfkill-regulator.ko
  CC      /home/raze/compat-wireless-2012-05-10/net/wireless/cfg80211.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/cfg80211.ko
  CC      /home/raze/compat-wireless-2012-05-10/net/wireless/lib80211.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/lib80211.ko
  CC      /home/raze/compat-wireless-2012-05-10/net/wireless/lib80211_crypt_ccmp.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/lib80211_crypt_ccmp.ko
  CC      /home/raze/compat-wireless-2012-05-10/net/wireless/lib80211_crypt_tkip.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/lib80211_crypt_tkip.ko
  CC      /home/raze/compat-wireless-2012-05-10/net/wireless/lib80211_crypt_wep.mod.o
  LD [M]  /home/raze/compat-wireless-2012-05-10/net/wireless/lib80211_crypt_wep.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-25-generic-pae'
make -C /lib/modules/3.2.0-25-generic-pae/build M=/home/raze/compat-wireless-2012-05-10 "INSTALL_MOD_DIR=updates"  \
		modules_install
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-25-generic-pae'
  INSTALL /home/raze/compat-wireless-2012-05-10/compat/compat.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/bcma/bcma.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/ath3k.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/bcm203x.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/bfusb.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/bluecard_cs.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/bpa10x.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/bt3c_cs.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btmrvl.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btmrvl_sdio.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btsdio.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btuart_cs.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btusb.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/btwilink.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/dtl1_cs.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/hci_uart.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/bluetooth/hci_vhci.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/misc/eeprom/eeprom_93cx6.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/atheros/atl1c/atl1c.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/atheros/atl1e/atl1e.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/atheros/atlx/atl1.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/atheros/atlx/atl2.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/ethernet/broadcom/b44.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/usb/cdc_ether.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/usb/rndis_host.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/usb/usbnet.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/adm8211.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/at76c50x-usb.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath5k/ath5k.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/ath6kl_core.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/ath6kl_sdio.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath6kl/ath6kl_usb.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/ath9k.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/ath9k_common.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ath/carl9170/carl9170.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43/b43.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/b43legacy/b43legacy.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211/brcmfmac/brcmfmac.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ipw2x00/ipw2100.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ipw2x00/ipw2200.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ipw2x00/libipw.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/iwlegacy/iwl3945.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/iwlegacy/iwl4965.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/iwlegacy/iwlegacy.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwlwifi.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/libertas/libertas.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/libertas/libertas_cs.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/libertas/libertas_sdio.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/libertas/libertas_spi.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/libertas/usb8xxx.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/libertas_tf/libertas_tf.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/mac80211_hwsim.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/mwifiex/mwifiex.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/mwifiex/mwifiex_pcie.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/mwifiex/mwifiex_sdio.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/mwl8k.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/orinoco/orinoco.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/orinoco/orinoco_cs.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/orinoco/orinoco_nortel.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/orinoco/orinoco_pci.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/orinoco/orinoco_plx.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/orinoco/orinoco_tmd.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/orinoco/orinoco_usb.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/orinoco/spectrum_cs.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/p54/p54common.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/p54/p54pci.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/p54/p54spi.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/p54/p54usb.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rndis_wlan.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2400pci.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2500pci.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2500usb.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2800lib.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2800pci.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2800usb.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2x00lib.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2x00pci.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt2x00usb.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt61pci.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rt2x00/rt73usb.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtl818x/rtl8180/rtl8180.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192de/rtl8192de.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/rtlwifi/rtlwifi.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/wl1251.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/wl1251_sdio.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl1251/wl1251_spi.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wl12xx/wl12xx.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/wlcore.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/wlcore_sdio.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/ti/wlcore/wlcore_spi.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/zd1211rw/zd1211rw.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/drivers/ssb/ssb.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/net/bluetooth/bluetooth.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/net/bluetooth/bnep/bnep.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/net/bluetooth/cmtp/cmtp.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/net/bluetooth/hidp/hidp.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/net/bluetooth/rfcomm/rfcomm.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/net/mac80211/mac80211.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/net/rfkill/rfkill-regulator.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/net/wireless/cfg80211.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/net/wireless/lib80211.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/net/wireless/lib80211_crypt_ccmp.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/net/wireless/lib80211_crypt_tkip.ko
  INSTALL /home/raze/compat-wireless-2012-05-10/net/wireless/lib80211_crypt_wep.ko
  DEPMOD  3.2.0-25-generic-pae
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-25-generic-pae'
Updating Ubuntu's initramfs for 3.2.0-25-generic-pae under /boot/ ...
Will now run update-grub to ensure grub will find the new initramfs ...
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-25-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-25-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Note: madwifi detected, we're going to disable it. If you would like to enable it later you can run:
    sudo athenable madwifi

Running athenable ath5k...
Disabling ath_pci ...	[OK]	Module disabled:
net/ath_pci.ko
depmod will prefer updates/ over kernel/ -- OK!

Now run:

sudo make unload to unload all: wireless, bluetooth and ethernet modules
sudo make wlunload to unload wireless modules
sudo make btunload to unload bluetooth modules

Run sudo modprobe driver-name to load your desired driver.
If unsure reboot.

raze@Raze-Station-U:~/compat-wireless-2012-05-10$ sudo echo options iwlagn swcrypto=1 >> /etc/modprobe.d/options
bash: /etc/modprobe.d/options: Permission denied

raze@Raze-Station-U:~/compat-wireless-2012-05-10$ sudo make load
make: *** No rule to make target `load'.  Stop.

```

Here's the wireless ticket information as required by the forum rules:
**1 ) Machine Brand and Model (PC/Laptop):**
Lenovo ThinkPad R61 (8933B51)

**2 ) Wireless Brand, Model and Wireless Chipset:**
$ lspci
```
raze@Raze-Station-U:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

```
$ lsusb
```
raze@Raze-Station-U:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 17ef:1004 Lenovo Integrated Webcam
Bus 003 Device 002: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller

```
$ lspci -nn | grep 'Wireless Brand'
```
returns nothing.
```

**3 ) check interface:**
$ ifconfig
```
raze@Raze-Station-U:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:37:d8:5f:33  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:37ff:fed8:5f33/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8900 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6217983 (6.2 MB)  TX bytes:1385157 (1.3 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6766 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6766 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480434 (480.4 KB)  TX bytes:480434 (480.4 KB)

```
$ iwconfig
```
raze@Raze-Station-U:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```
$ iwconfig wlan0
```
raze@Raze-Station-U:~$ iwconfig wlan0
wlan0     No such device

```

**4 ) Check for modules:**
$ lsmod
```
raze@Raze-Station-U:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
joydev                 17393  0 
snd_hda_codec_conexant    52516  1 
parport_pc             32114  0 
ppdev                  12849  0 
pcmcia                 39791  0 
binfmt_misc            17292  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
r852                   17901  0 
sm_common              16737  1 r852
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
thinkpad_acpi          73942  0 
r592                   17808  0 
psmouse                72919  0 
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
serio_raw              13027  0 
snd_seq_midi_event     14475  1 snd_seq_midi
mtd                    35584  2 sm_common,nand
memstick               15857  1 r592
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nvram                  14029  1 thinkpad_acpi
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
nand_ecc               13070  1 nand
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,thinkpad_acpi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
tpm_tis                18308  0 
i915                  414663  3 
mac_hid                13077  0 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
tg3                   141369  0 

```
$ lsmod | grep "wlan_module_name"
```
returns nothing.
```

**5 ) Kernel boot messages**
$ dmesg | grep "wlan_module_name"
```
returns nothing
```

**6 ) Network configuration**
$ sudo lshw -C network
```
raze@Raze-Station-U:~$ sudo lshw -C network
[sudo] password for raze: 
  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:df6fe000-df6fffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:37:d8:5f:33
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=sb v2.11 ip=192.168.1.8 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:47 memory:fe000000-fe00ffff

```

**7 ) Scan for networks:**
$ iwlist scan
```
raze@Raze-Station-U:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```
$ iwlist scan wlan0
```
raze@Raze-Station-U:~$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').
```

**8 ) Ubuntu Version:**
$ lsb_release -d
```
raze@Raze-Station-U:~$ lsb_release -d
Description:	Ubuntu 12.04 LTS

```

**9 ) Kernel/architecture (including 32 vs. 64 bit):**
$ uname -mr
```
raze@Raze-Station-U:~$ uname -mr
3.2.0-25-generic-pae i686

```

**10 ) Restarting the network:**
$ sudo /etc/init.d/networking restart
```
raze@Raze-Station-U:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
```

Any ideas to get my wireless working again with or without the patched driver is very appreciated. Thanks in advance.

---

### Post by chili555 on 2012-06-24
> /home/raze/compat-wireless-2012-05-10/drivers/net/wireless/iwlwifi/iwlwifi.koAs you can see, it built the driver iwlwifi for 12.04; it's no longer called iwlagn. Are there any informative messages when you do:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
```Also, this step is grossly in error:> echo options iwlagn swcrypto=1 >> /etc/modprobe.d/options [as root!]Grossly!! Please do:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```Add one line:```
options iwlwifi swcrypto=1
```Proofread, save and close.

If there are any errors above, please post them and we'll proceed.

---

### Post by RazeRules on 2012-06-24
```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
```
returns:
```
raze@Raze-Station-U:~$ sudo modprobe -r iwlwifi
[sudo] password for raze: 
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
raze@Raze-Station-U:~$ sudo modprobe iwlwifi
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.

```

Also, I've done this:
```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```
saved the line and closed.

Will reboot now then feedback.

---

### Post by chili555 on 2012-06-24
> WARNING: All config files need .conf: [COLOR="Red"]/etc/modprobe.d/options[/COLOR], it will be ignored in a future release.That's the erroneous file from above; you can safely remove it:```
sudo rm /etc/modprobe.d/options
```

---

### Post by RazeRules on 2012-06-24
After reboot:
```
raze@Raze-Station-U:~$ sudo lshw -c network
[sudo] password for raze: 
  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:df6fe000-df6fffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:37:d8:5f:33
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=sb v2.11 ip=192.168.1.6 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:47 memory:fe000000-fe00ffff
```

Am I missing something?

---

### Post by RazeRules on 2012-06-24
> **chili555 said:**
> That's the erroneous file from above; you can safely remove it:```
sudo rm /etc/modprobe.d/options
```

Done.

---

### Post by chili555 on 2012-06-24
Please do:```
sudo modprobe iwlwifi
```Is it still unclaimed? If so, let's see if there are informative messages:```
dmesg | grep iwl
```

---

### Post by RazeRules on 2012-06-24
Here:
```
raze@Raze-Station-U:~$ sudo modprobe iwlwifi
[sudo] password for raze: 
raze@Raze-Station-U:~$ dmesg | grep iwl
[  813.941219] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[  813.941224] iwlwifi: Copyright(c) 2003-2012 Intel Corporation
raze@Raze-Station-U:~$ 

```

---

### Post by RazeRules on 2012-06-24
It's still unclaimed after ```
sudo modprobe iwlwifi
```
should I reboot?

---

### Post by chili555 on 2012-06-24
No.

All I can conclude is that the patches are too old for your kernel and gcc versions. For example: mac80211_[COLOR="Red"]2.6.28-rc4[/COLOR]-wl_frag+ack_v3.patch but your kernel is [COLOR="Red"]3.2.0-25[/COLOR]-generic-pae. I'm not at all sure the patches will ever work. You might search for newer patches. 

In the meantime, I'd uninstall compat-wireless.```
cd compat-wireless-2012-05-10
sudo su
make uninstall
modprobe -r iwlwifi
modprobe iwlwifi
iwconfig
exit
```

---

### Post by RazeRules on 2012-06-24
Is this ok?
```
raze@Raze-Station-U:~$ cd compat-wireless-2012-05-10/
raze@Raze-Station-U:~/compat-wireless-2012-05-10$ sudo su
[sudo] password for raze: 
root@Raze-Station-U:/home/raze/compat-wireless-2012-05-10# make uninstall

root@Raze-Station-U:/home/raze/compat-wireless-2012-05-10# modprobe -r iwlwifi
root@Raze-Station-U:/home/raze/compat-wireless-2012-05-10# modprobe iwlwifi
root@Raze-Station-U:/home/raze/compat-wireless-2012-05-10# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by chili555 on 2012-06-24
Quite a little mystery you have there! Let's try what I regret not trying about 153 posts ago:```
sudo modprobe -r iwlwifi
sudo modprobe iwl4965
iwconfig
```

---

### Post by RazeRules on 2012-06-24
iwl4965 not found :(
```
raze@Raze-Station-U:~$ sudo modprobe -r iwlwifi
[sudo] password for raze: 
raze@Raze-Station-U:~$ sudo modprobe iwl4965
FATAL: Module iwl4965 not found.
raze@Raze-Station-U:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```
Is there a way to restore the working driver that came with 12.04 before I started the whole thing ?

---

### Post by chili555 on 2012-06-24
Please try this:```
sudo apt-get install --reinstall linux-image-`uname -r`
```Those tickmarks are on the left side of my US keyboard on the same key with ~.```
sudo modprobe iwl4965
```We know it exists:> /lib/modules/3.2.0-25-generic-pae/kernel/drivers/net/wireless/iwlegacy/iwl4965.ko

---

### Post by RazeRules on 2012-06-24
That Worked! 

```
raze@Raze-Station-U:~$ sudo apt-get install --reinstall linux-image-`uname -r`
[sudo] password for raze: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/37.9 MB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 215842 files and directories currently installed.)
Preparing to replace linux-image-3.2.0-25-generic-pae 3.2.0-25.40 (using .../linux-image-3.2.0-25-generic-pae_3.2.0-25.40_i386.deb) ...
Done.
Unpacking replacement linux-image-3.2.0-25-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-25-generic-pae /boot/vmlinuz-3.2.0-25-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-25-generic-pae /boot/vmlinuz-3.2.0-25-generic-pae
Setting up linux-image-3.2.0-25-generic-pae (3.2.0-25.40) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.2.0-25.40 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.2.0-25.40 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-25-generic-pae /boot/vmlinuz-3.2.0-25-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-25-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-25-generic-pae /boot/vmlinuz-3.2.0-25-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-25-generic-pae /boot/vmlinuz-3.2.0-25-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-25-generic-pae /boot/vmlinuz-3.2.0-25-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-25-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-25-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
raze@Raze-Station-U:~$ sudo modprobe iwl4965
raze@Raze-Station-U:~$ 

```

Thank you chili555, you were very helpful. I'm posting this through my wireless connection :)

---

### Post by chili555 on 2012-06-24
Glad it's working. Sorry I have no idea about how to get the patched driver working.

---

### Post by RazeRules on 2012-06-24
There is only one more problem, I have to run this line after every reboot otherwise the same issue happens :(
```
sudo modprobe iwl4965
```

---

### Post by chili555 on 2012-06-24
Let's see if this helps:```
sudo su
echo iwl4965 >> /etc/modules
exit
```

---

### Post by RazeRules on 2012-06-24
Perfect. Thank you

---

