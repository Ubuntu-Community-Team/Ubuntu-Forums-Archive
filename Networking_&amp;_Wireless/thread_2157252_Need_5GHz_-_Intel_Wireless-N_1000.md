---
title: "Need 5GHz - Intel Wireless-N 1000"
date: 2013-06-24
forum: Networking &amp; Wireless
---

### Post by YourOldBuddy on 2013-06-24
Hi

Ubuntu 13.04,
Lenovo Thinkpad X220t,
Intel Wireless-N 1000

I just moved and 2,4GHz is just too overloaded where I moved to. I can only get a semi decent connection in certain spots. 

Changing the AP (ASUS EA-N66) to 5GHz fixed things for my other devices but the Thinkpad can't see the SSID and I can't connect to it as hidden. 

Searching online hasn't helped. Please help.

---

### Post by YourOldBuddy on 2013-06-24
Found this after a bit of poking about. 

XXX@TTT/sys/class/net/wlan0/device/driver/module/drivers/pci:iwlwifi/module/parameters$ ls
11n_disable    antenna_coupling  bt_coex_active  plcp_check   swcrypto
5ghz_disable   auto_agg          fw_restart      power_level  wd_disable
amsdu_size_8K  bt_ch_inhibition  led_mode        power_save

XXX@TTT/sys/class/net/wlan0/device/driver/module/drivers/pci:iwlwifi/module/parameters$ cat 5ghz_disable 
N

XXX@TTT/sys/class/net/wlan0/device/driver/module/drivers/pci:iwlwifi/module/parameters$ cat 11n_disable 
0

Don't know what to read into this.

---

### Post by seenthelite on 2013-06-27
> **YourOldBuddy said:**
> Hi

Ubuntu 13.04,
Lenovo Thinkpad X220t,
Intel Wireless-N 1000

Changing the AP (ASUS EA-N66) to 5GHz fixed things for my other devices but the Thinkpad can't see the SSID and I can't connect to it as hidden. 


  
The reason why you can not see the SSID  at 5GHz is because that card is only single band 2.4 GHz.

 [http://www.intel.com/content/www/us/en/processors/centrino/centrino-wireless-n-1000-brief.html](http://www.intel.com/content/www/us/en/processors/centrino/centrino-wireless-n-1000-brief.html)

---

### Post by chili555 on 2013-06-27
For your information and that of a few searchers, the driver iwlwifi is used by several Intel devices. The driver then loads firmware appropriate to the specific device. Yours probably loads /lib/firmware/iwlwifi-**1000**-5.ucode. The parameters you listed above are switchable for devices that support them, not necessarily _all_ Intel devices. In other words, for example, for Intel devices that support 5gHz traffic, 5gHz may be disabled:```
options iwlwifi 5ghz_disable=Y
```

---

