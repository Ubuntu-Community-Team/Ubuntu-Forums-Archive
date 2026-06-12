---
title: "Problems compiling Hostapd"
date: 2013-02-20
forum: Networking &amp; Wireless
---

### Post by junkmechanic on 2013-02-20
Hi.

I am quite new to Linux. In fact Quantal is my first Linux OS and the word around the town gives me the feeling that I am not on a good start :D.
Anyways, to complicate matters I have Broadcom BCM4313 wireless adapter and one of my basic requirements is to get the hotspot working to connect my android to it.

So, as instructed on hostapd site, I tried for the minimal-config to work. It didnt. I got the following error :
'nl80211' generic netlink not found

So I figured that I need to first install libnl libraries. Downloaded the latest tar ball versions of compat-wireless, regdb, crda, libnl and hostapd. Extracted them in /usr/src/ folder. Then I build-compiled libnl, regdb adn crda. 

Now in the hostapd folder, I copied the default config to .config (cp defconfig .config). Next, inside .config, uncommented and added the following lines

CONFIG_DRIVER_NL80211=y
  LIBNL=/usr
  CFLAGS += -I$(LIBNL)/include/libnl
  LIBS += -L$(LIBNL)/lib

and tried to compile it. figured a few other libraries were missing that I had to install. 
Finally this is what I get.

```

xxxx@yyyyyyyy:/usr/src/hostapd-2.0/hostapd$ sudo make && sudo make install
../src/drivers/driver_nl80211.o: In function `get_link_signal':
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:1700: undefined reference to `genlmsg_attrlen'
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:1700: undefined reference to `genlmsg_attrdata'
../src/drivers/driver_nl80211.o: In function `get_link_noise':
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:1765: undefined reference to `genlmsg_attrlen'
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:1765: undefined reference to `genlmsg_attrdata'
../src/drivers/driver_nl80211.o: In function `netdev_info_handler':
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:545: undefined reference to `genlmsg_attrlen'
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:545: undefined reference to `genlmsg_attrdata'
../src/drivers/driver_nl80211.o: In function `get_sta_handler':
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:7488: undefined reference to `genlmsg_attrlen'
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:7488: undefined reference to `genlmsg_attrdata'
../src/drivers/driver_nl80211.o: In function `get_noise_for_scan_results':
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:1834: undefined reference to `genlmsg_attrlen'
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:1834: undefined reference to `genlmsg_attrdata'
../src/drivers/driver_nl80211.o: In function `get_key_handler':
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:7331: undefined reference to `genlmsg_attrlen'
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:7331: undefined reference to `genlmsg_attrdata'
../src/drivers/driver_nl80211.o: In function `cookie_handler':
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:8229: undefined reference to `genlmsg_attrlen'
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:8229: undefined reference to `genlmsg_attrdata'
../src/drivers/driver_nl80211.o: In function `family_handler':
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:478: undefined reference to `genlmsg_attrlen'
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:478: undefined reference to `genlmsg_attrdata'
../src/drivers/driver_nl80211.o: In function `wiphy_info_handler':
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:2486: undefined reference to `genlmsg_attrlen'
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:2486: undefined reference to `genlmsg_attrdata'
../src/drivers/driver_nl80211.o: In function `nl80211_get_reg':
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:5251: undefined reference to `genlmsg_attrlen'
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:5251: undefined reference to `genlmsg_attrdata'
../src/drivers/driver_nl80211.o: In function `nl80211_cmd':
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:529: undefined reference to `genlmsg_put'
../src/drivers/driver_nl80211.o: In function `process_beacon_event':
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:626: undefined reference to `genlmsg_attrlen'
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:626: undefined reference to `genlmsg_attrdata'
../src/drivers/driver_nl80211.o: In function `bss_info_handler':
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:3973: undefined reference to `genlmsg_attrlen'
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:3973: undefined reference to `genlmsg_attrdata'
../src/drivers/driver_nl80211.o: In function `nl80211_handle_alloc':
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:91: undefined reference to `nl_handle_alloc_cb'
../src/drivers/driver_nl80211.o: In function `nl_create_handle':
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:129: undefined reference to `genl_connect'
../src/drivers/driver_nl80211.o: In function `nl_get_multicast_id':
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:511: undefined reference to `genl_ctrl_resolve'
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:511: undefined reference to `genlmsg_put'
../src/drivers/driver_nl80211.o: In function `wpa_driver_nl80211_init_nl_global':
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:2843: undefined reference to `genl_ctrl_resolve'
../src/drivers/driver_nl80211.o: In function `phy_info_handler':
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:4902: undefined reference to `genlmsg_attrlen'
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:4902: undefined reference to `genlmsg_attrdata'
../src/drivers/driver_nl80211.o: In function `process_bss_event':
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:2362: undefined reference to `genlmsg_attrlen'
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:2362: undefined reference to `genlmsg_attrdata'
../src/drivers/driver_nl80211.o: In function `process_drv_event':
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:2307: undefined reference to `genlmsg_attrlen'
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:2307: undefined reference to `genlmsg_attrdata'
../src/drivers/driver_nl80211.o: In function `process_global_event':
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:2336: undefined reference to `genlmsg_attrlen'
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:2336: undefined reference to `genlmsg_attrdata'
../src/drivers/driver_nl80211.o: In function `nl80211_handle_destroy':
/usr/src/hostapd-2.0/hostapd/../src/drivers/driver_nl80211.c:113: undefined reference to `nl_handle_destroy'
collect2: error: ld returned 1 exit status
make: *** [hostapd] Error 1

```

Any suggestions?
Seemed to have hit a wall. 

Thanks for your time.

---

### Post by spiralsun on 2013-03-11
Hi, not sure but you could try to install libn1

```
sudo apt-get install libnl-dev
```

---

### Post by schragge on 2013-03-11
Just to be sure that the hostapd from Ubuntu repository really doesn't contain the driver for your device as the error message
> **junkmechanic said:**
> 'nl80211' generic netlink not found doesn't look quite unambiguous to me, could you please try
```

sudo apt-get install iw
sudo iw list

```If *iw list* fails, you can then in good conscience continue compiling the newer hostapd version from source.

---

### Post by junkmechanic on 2013-03-28
Thanks for your replies @schragge and @[COLOR=#000000]spiralsun.

I tried your suggestions. Didnt work. iw list says "[/COLOR]nl80211 not found.".
Anyways, more research indicates that I suffer from [this]("http://askubuntu.com/questions/258813/cannot-create-wireless-ap") disease.

---

