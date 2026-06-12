---
title: "rtl8192se connects but later disconnects and cannot reconnect"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by Garibaldi3489 on 2010-03-25
I have a Lenovo T410 laptop using Lucid beta 1 x64. The wireless card in this laptop is a Realtek 8192se:
```

$ dmesg | grep rtl
[   17.688964] rtl819xSE 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.688971] rtl819xSE 0000:03:00.0: setting latency timer to 64
[   17.699480] rtl819xSE 0000:03:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin
[   17.988020] ===>rtl8192_SetWirelessMode(), wireless_mode:0x8, support_mode:0x16
[   17.988024] <===rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   36.905035] ===>rtl8192_SetWirelessMode(), wireless_mode:0x10, support_mode:0x16
[   36.905038] <===rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[   38.502613] ===>rtl8192_SetWirelessMode(), wireless_mode:0x6, support_mode:0x16
[   38.502615] <===rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[   38.505031] ===========rtl8192se_update_ratr_table: ff4
[   71.265201] ===========rtl8192se_update_ratr_table: ff4
[   71.317946] ===>rtl8192_SetWirelessMode(), wireless_mode:0x6, support_mode:0x16
[   71.317952] <===rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[   73.822733] ===>rtl8192_SetWirelessMode(), wireless_mode:0x6, support_mode:0x16
[   73.822737] <===rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[   73.828045] ===========rtl8192se_update_ratr_table: ff4
[  121.242381] ===========rtl8192se_update_ratr_table: ff4
[  121.346994] ===>rtl8192_SetWirelessMode(), wireless_mode:0x6, support_mode:0x16
[  121.346998] <===rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[  123.850346] ===>rtl8192_SetWirelessMode(), wireless_mode:0x6, support_mode:0x16
[  123.850351] <===rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[  123.852594] ===========rtl8192se_update_ratr_table: ff4
[  171.136714] ===========rtl8192se_update_ratr_table: ff4
[  171.189145] ===>rtl8192_SetWirelessMode(), wireless_mode:0x6, support_mode:0x16
[  171.189153] <===rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[  171.191760] ===========rtl8192se_update_ratr_table: ff4
[  215.362641] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[  219.355872] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[  251.006151] ===========rtl8192se_update_ratr_table: ff4
[  251.060627] ===>rtl8192_SetWirelessMode(), wireless_mode:0x6, support_mode:0x16
[  251.060632] <===rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[  253.563774] ===>rtl8192_SetWirelessMode(), wireless_mode:0x6, support_mode:0x16
[  253.563777] <===rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
[  253.569145] ===========rtl8192se_update_ratr_table: ff4
[  295.231763] rtl8192_hw_sleep_down(): RF Change in progress!
[  350.768801] ===========rtl8192se_update_ratr_table: ff4
[  470.617212] ===========rtl8192se_update_ratr_table: ff4
[  590.431982] ===========rtl8192se_update_ratr_table: ff4

```

When I first start up Lucid, the wireless works great - it connects automatically to a network that I have saved and just works. However, after a little while of doing normal activities (internet, ssh, etc) the wireless card will suddenly drop the connection. When I try to select the network again (or any network) and reconnect, it just tries to connect indefinitely or reports "Network Offline". Restarting fixes the problem and it works again.

Any ideas on what is causing this? I've tried "ifdown wlan0" and then "ifup wlan0" to try and reset the adapter but that doesn't help. Is there another way to reset the wireless? Any ideas on what is causing this?

Note: I have tried using realtek's own 8192se drivers instead of the ones included in Lucid but they seem to be just as bad if not worse.

Thanks!

---

### Post by ciociocio on 2011-11-19
I've got a Toshiba T110, with Ubuntu 11.10. I've got the same problem, but I found a workaround when this happens.

sudo rmmod rtl8192se
modprobe rtl8192se

at least you don't have to reboot.

Looking for a real solution, but no luck yet.

---

### Post by bill.ca on 2012-02-01
I just updated to 11.10.  Have a realtek card and the  wireless worked for a couple of days and then, can't seem to authenticate on a wpa2 network.  So far the rmmod/modprobe fix is the only thing that's worked.  Anyone found a permanent solution?

---

