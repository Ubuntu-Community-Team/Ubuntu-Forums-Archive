---
title: "latest compact-wireless"
date: 2012-03-19
forum: Networking &amp; Wireless
---

### Post by pr3zident on 2012-03-19
I'm trying to compile the latest compact-wireless and this is what im getting this ... how do i fix ? ```
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/3.0.0-16-generic/build M=/home/nprezident/Downloads/compat-wireless-3.3-rc6 modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-16-generic'
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/compat/built-in.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/compat/main.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/compat/cordic.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/compat/crc8.o
/home/nprezident/Downloads/compat-wireless-3.3-rc6/compat/crc8.c:17:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
/home/nprezident/Downloads/compat-wireless-3.3-rc6/compat/crc8.c:17:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/compat/compat_atomic.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/compat/compat.o
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bcma/built-in.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bcma/main.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bcma/scan.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bcma/core.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bcma/sprom.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bcma/driver_chipcommon.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bcma/driver_chipcommon_pmu.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bcma/driver_pci.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bcma/host_pci.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bcma/bcma.o
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bluetooth/built-in.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bluetooth/hci_vhci.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bluetooth/btmrvl_main.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bluetooth/btmrvl_debugfs.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bluetooth/hci_ldisc.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bluetooth/hci_h4.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bluetooth/hci_bcsp.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bluetooth/hci_ll.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bluetooth/hci_ath.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bluetooth/hci_uart.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bluetooth/bcm203x.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bluetooth/bpa10x.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bluetooth/bfusb.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bluetooth/dtl1_cs.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bluetooth/bt3c_cs.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bluetooth/bluecard_cs.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bluetooth/btuart_cs.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bluetooth/btusb.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bluetooth/btsdio.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bluetooth/ath3k.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bluetooth/btmrvl.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bluetooth/btmrvl_sdio.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/bluetooth/btwilink.o
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/misc/eeprom/built-in.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/misc/eeprom/eeprom_93cx6.o
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/ethernet/atheros/built-in.o
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/ethernet/atheros/atl1c/built-in.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/ethernet/atheros/atl1c/atl1c_main.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/ethernet/atheros/atl1c/atl1c_hw.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/ethernet/atheros/atl1c/atl1c_ethtool.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/ethernet/atheros/atl1c/atl1c.o
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/ethernet/atheros/atl1e/built-in.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/ethernet/atheros/atl1e/atl1e_main.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/ethernet/atheros/atl1e/atl1e_hw.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/ethernet/atheros/atl1e/atl1e_ethtool.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/ethernet/atheros/atl1e/atl1e_param.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/ethernet/atheros/atl1e/atl1e.o
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/ethernet/atheros/atlx/built-in.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/ethernet/atheros/atlx/atl1.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/ethernet/atheros/atlx/atl2.o
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/ethernet/broadcom/built-in.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/ethernet/broadcom/b44.o
/home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/ethernet/broadcom/b44.c:13:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/usb/built-in.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/usb/cdc_ether.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/usb/rndis_host.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/usb/usbnet.o
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/built-in.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/main.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/regd.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/hw.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/key.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath.o
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath5k/built-in.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath5k/caps.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath5k/initvals.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath5k/eeprom.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath5k/gpio.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath5k/desc.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath5k/dma.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath5k/qcu.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath5k/pcu.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath5k/phy.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath5k/reset.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath5k/attach.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath5k/base.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath5k/led.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath5k/rfkill.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath5k/ani.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath5k/sysfs.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath5k/mac80211-ops.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath5k/pci.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath5k/ath5k.o
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath6kl/built-in.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath6kl/debug.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath6kl/hif.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath6kl/htc.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath6kl/bmi.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath6kl/cfg80211.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath6kl/init.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath6kl/main.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath6kl/txrx.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath6kl/wmi.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath6kl/sdio.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath6kl/testmode.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath6kl/ath6kl.o
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/built-in.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/beacon.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/gpio.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/init.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/main.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/recv.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/xmit.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/mci.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/rc.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/pci.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/ahb.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/debug.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/common.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/htc_hst.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/hif_usb.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/wmi.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/htc_drv_txrx.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/htc_drv_main.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/htc_drv_beacon.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/htc_drv_init.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/htc_drv_gpio.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/htc_drv_debug.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/ar9002_hw.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/ar9003_hw.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/hw.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/ar9003_phy.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/ar9002_phy.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/ar5008_phy.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/ar9002_calib.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/ar9003_calib.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/ar9003_rtt.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/calib.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/eeprom.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/eeprom_def.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/eeprom_4k.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/eeprom_9287.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/ani.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/btcoex.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/mac.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/ar9002_mac.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/ar9003_mac.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/ar9003_eeprom.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/ar9003_paprd.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/ar9003_mci.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/ath9k.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/ath9k_hw.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/ath9k_common.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/ath9k/ath9k_htc.o
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/carl9170/built-in.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/carl9170/main.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/carl9170/usb.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/carl9170/cmd.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/carl9170/mac.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/carl9170/phy.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/carl9170/led.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/carl9170/fw.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/carl9170/tx.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/carl9170/rx.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ath/carl9170/carl9170.o
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/built-in.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/main.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/bus.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/tables.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/tables_nphy.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/radio_2055.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/radio_2056.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/phy_common.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/phy_g.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/phy_a.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/phy_n.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/phy_lp.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/tables_lpphy.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/phy_ht.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/tables_phy_ht.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/radio_2059.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/sysfs.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/xmit.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/lo.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/wa.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/dma.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/pio.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/rfkill.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/leds.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/pcmcia.o
^[4  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/sdio.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43/b43.o
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43legacy/built-in.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43legacy/main.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43legacy/ilt.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43legacy/phy.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43legacy/radio.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43legacy/sysfs.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43legacy/xmit.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43legacy/rfkill.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43legacy/leds.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43legacy/debugfs.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43legacy/dma.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43legacy/pio.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/b43legacy/b43legacy.o
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/built-in.o
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmfmac/built-in.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmfmac/wl_cfg80211.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmfmac/dhd_cdc.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmfmac/dhd_common.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmfmac/dhd_linux.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmfmac/brcmfmac.o
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/built-in.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/mac80211_if.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/ucode_loader.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/ampdu.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/antsel.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/channel.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/main.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/phy_shim.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/pmu.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/rate.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/stf.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/aiutils.o
/home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/aiutils.c:19:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/phy/phy_cmn.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/phy/phy_lcn.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/phy/phy_n.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/phy/phytbl_lcn.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/phy/phytbl_n.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/phy/phy_qmath.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/otp.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/srom.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/dma.o
/home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/dma.c:17:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/nicpci.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/brcms_trace_events.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.o
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmutil/built-in.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmutil/utils.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/brcm80211/brcmutil/brcmutil.o
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ipw2x00/built-in.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ipw2x00/ipw2100.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ipw2x00/ipw2200.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ipw2x00/libipw_module.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ipw2x00/libipw_tx.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ipw2x00/libipw_rx.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ipw2x00/libipw_wx.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ipw2x00/libipw_geo.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/ipw2x00/libipw.o
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlegacy/built-in.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlegacy/3945-mac.o
/home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlegacy/3945-mac.c:30:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlegacy/3945.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlegacy/3945-rs.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlegacy/4965.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlegacy/4965-mac.o
/home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlegacy/4965-mac.c:30:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlegacy/4965-rs.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlegacy/4965-calib.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlegacy/common.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlegacy/iwlegacy.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlegacy/iwl4965.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlegacy/iwl3945.o
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/built-in.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-agn.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-agn-rs.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-mac80211.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-ucode.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-agn-tx.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-agn-lib.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-agn-calib.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-io.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-agn-tt.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-agn-sta.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-agn-rx.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-core.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-eeprom.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-power.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-scan.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-led.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-agn-rxon.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-5000.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-6000.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-1000.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-2000.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-pci.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-trans.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-trans-pcie.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-trans-pcie-rx.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-trans-pcie-tx.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-debugfs.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwl-devtrace.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwlwifi/iwlwifi.o
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwmc3200wifi/built-in.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwmc3200wifi/main.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwmc3200wifi/netdev.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwmc3200wifi/rx.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwmc3200wifi/tx.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwmc3200wifi/sdio.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwmc3200wifi/hal.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwmc3200wifi/fw.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwmc3200wifi/commands.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwmc3200wifi/cfg80211.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwmc3200wifi/eeprom.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwmc3200wifi/trace.o
  LD [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.o
  LD      /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/built-in.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/cfg.o
/home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/cfg.c:9:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/cmd.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/cmdresp.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/debugfs.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/ethtool.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/main.o
/home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/main.c:7:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
/home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/main.c:7:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/rx.o
/home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/rx.c:5:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
/home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/rx.c:5:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/tx.o
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/mesh.o
/home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/mesh.c:1:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/if_cs.o
/home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/if_cs.c:24:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/if_sdio.o
/home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/if_sdio.c:29:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/if_spi.o
/home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/if_spi.c:20:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/if_usb.o
/home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/if_usb.c:5:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
/home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/if_usb.c: In function ‘if_usb_suspend’:
/home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/if_usb.c:1139:4: error: implicit declaration of function ‘olpc_ec_wakeup_clear’ [-Werror=implicit-function-declaration]
/home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/if_usb.c:1141:4: error: implicit declaration of function ‘olpc_ec_wakeup_set’ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors

make[4]: *** [/home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas/if_usb.o] Error 1
make[3]: *** [/home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless/libertas] Error 2
make[2]: *** [/home/nprezident/Downloads/compat-wireless-3.3-rc6/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/nprezident/Downloads/compat-wireless-3.3-rc6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-16-generic'
make: *** [modules] Error 2
```

---

### Post by chili555 on 2012-03-21
I suspect that this version:> compat-wireless-3.[COLOR="Red"]3[/COLOR]-rc6Is not a very good match with your kernel:> 3.[COLOR="Red"]0.0[/COLOR]-16-genericDid you read this on the website?> **Getting compat-wireless on Ubuntu**

With Ubuntu you have the option of either installing compat-wireless yourself or of installing the package that provides it built by the Ubuntu kernel team. The Ubuntu package that carries compat-wireless is called linux-backport-modules and it has more backported modules than just your wireless subsystem. Its updated whenever major updates are pushed out into the wireless-testing git tree. Did you try the backports package?

What are you trying to achieve? Maybe there is an easier way.

---

### Post by pr3zident on 2012-03-21
> **chili555 said:**
> I suspect that this version:Is not a very good match with your kernel:Did you read this on the website?Did you try the backports package?

What are you trying to achieve? Maybe there is an easier way.

i was able to compile the wireless driver using a different version of compact-wireless... now i'm having problems with my bcm4312 wireless ubuntu does not detect my wireless, i can't search for any signals using my bcm4312. How do i reinstall the bcm4312 wireless driver? I just downloaded the back port modules and still no wireless..

---

### Post by chili555 on 2012-03-21
Let's see more specifically what you have:```
lspci -nn | grep 0280
```The problem with Broadcom cards is almost never the driver; it's almost always the firmware. Generally, installing a different driver fixes nothing.

---

### Post by pr3zident on 2012-03-21
> **pr3zident said:**
> i was able to compile the wireless driver using a different version of compact-wireless... now i'm having problems with my bcm4312 wireless ubuntu does not detect my wireless, i can't search for any signals using my bcm4312. How do i reinstall the bcm4312 wireless driver? I just downloaded the back port modules and still no wireless..


```
03:00.0 Network Controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01) 
```

---

### Post by chili555 on 2012-03-21
> Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315]There are two suggested ways to get this going. Please try:```
sudo apt-get install bcmwl-kernel-source
```Reboot and let us have your report.



---------

Note to self: Always get the lspci *FIRST* and save yourself the heartache.

---

### Post by pr3zident on 2012-03-22
> **chili555 said:**
> There are two suggested ways to get this going. Please try:```
sudo apt-get install bcmwl-kernel-source
```Reboot and let us have your report.



---------

Note to self: Always get the lspci *FIRST* and save yourself the heartache.

It's installed already sorry for the late reply

---

### Post by chili555 on 2012-03-22
Let's have a look at:```
lsmod | grep -e b43 -e wl
```If both modoles are loaded, remove b43:```
sudo modprobe -r b43
```If only b43 is loaded, please do:```
sudo modprobe -r b43
sudo modprobe wl
```Any improvement?```
iwconfig
```

---

### Post by pr3zident on 2012-03-23
> **chili555 said:**
> Let's have a look at:```
lsmod | grep -e b43 -e wl
```If both modoles are loaded, remove b43:```
sudo modprobe -r b43
```If only b43 is loaded, please do:```
sudo modprobe -r b43
sudo modprobe wl
```Any improvement?```
iwconfig
```

```
lsmod | grep -e b43 -e wl
``` i get no output

```
sudo modprobe wl
``` FATAL: Error inserting wl (/lib/modules/3.0.0-16-generic/updates/dkms/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by chili555 on 2012-03-23
> FATAL: Error inserting wl (/lib/modules/3.0.0-16-generic/updates/dkms/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)Oops! Please try:```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo apt-get install --reinstall dkms
sudo modprbe wl
```Now does it complain?

---

### Post by pr3zident on 2012-03-23
```
sudo apt-get install --reinstall dkms
```
Media change: please insert the disc labeled
 'Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)'

---

### Post by pr3zident on 2012-03-23
when i try to install additional drivers and check the log this is what i get ... 
```
2012-03-23 22:04:22,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb747ee0c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2012-03-23 22:04:22,517 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-03-23 22:04:22,657 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-03-23 22:04:22,849 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-03-23 22:04:26,027 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-03-23 22:04:31,870 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-03-23 22:04:31,995 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-03-23 22:04:50,322 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-03-23 22:04:50,396 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-03-23 22:04:50,510 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

```

---

### Post by chili555 on 2012-03-24
> **pr3zident said:**
> when i try to install additional drivers and check the log this is what i get ... 
```
2012-03-23 22:04:22,334 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb747ee0c> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')
2012-03-23 22:04:22,517 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-03-23 22:04:22,657 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-03-23 22:04:22,849 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-03-23 22:04:26,027 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-03-23 22:04:31,870 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-03-23 22:04:31,995 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-03-23 22:04:50,322 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-03-23 22:04:50,396 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-03-23 22:04:50,510 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

```Correct. In order to correctly use the driver wl, the competing drivers b43 and b43legacy must be blacklisted.

So, now can you load wl and does your wireless work?

---

