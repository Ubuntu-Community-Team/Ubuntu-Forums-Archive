---
title: "hostap can't set 5ghz channel"
date: 2012-07-23
forum: Networking &amp; Wireless
---

### Post by bakegoodz on 2012-07-23
I can't set hostap to use 5ghz  In the system logs it says

> wlan0: IEEE 802.11 Configured channel (36) not found from the channel list of current mode (2) IEEE 802.11a

I've been using the correct 5ghz channel numbers.

I've tried several 5ghz channel number and I get the same message. After lots of searching I think it might be something to do with regulatory domain. But I've set my country in /etc/default/crda and in hostapd.conf, I can't find anywhere else to set it.
In the syslog it does have this interesting message:
> cfg80211: Ignoring regulatory request Set by user since the driver requires its own regulatory domain to be set first

hostapd.conf

```
###############################
# Basic Config
###############################
country_code=US
macaddr_acl=0
auth_algs=1
# Most modern wireless drivers in the kernel need driver=nl80211
driver=nl80211
##########################
# Local configuration...
##########################
interface=wlan0
bridge=br0
wme_enabled=1
ieee80211n=1
ht_capab=[HT40+][SHORT-GI-40][DSSS_CCK-40]
channel=36
ssid=MyWireless
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=3
wpa_passphrase=mypassword
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
hw_mode=a

```

syslog
```
Jul 23 17:37:02 max kernel: [    8.970477] ieee80211 phy0: Atheros AR9280 Rev:2
Jul 23 17:37:02 max kernel: [    8.971129] Registered led device: ath9k_htc-phy0
Jul 23 17:37:02 max kernel: [    8.971140] usb 1-4: ath9k_htc: USB layer initialized
Jul 23 17:37:02 max kernel: [    8.971219] usbcore: registered new interface driver ath9k_htc
Jul 23 17:37:02 max kernel: [    9.011283] Console: switching to colour frame buffer device 128x48
Jul 23 17:37:02 max kernel: [    9.020404] cfg80211: Calling CRDA for country: US
Jul 23 17:37:02 max kernel: [    9.023307] fb0: inteldrmfb frame buffer device
Jul 23 17:37:02 max kernel: [    9.023317] drm: registered panic notifier
Jul 23 17:37:02 max kernel: [    9.023472] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Jul 23 17:37:02 max kernel: [    9.058218] cfg80211: Ignoring regulatory request Set by user since the driver requires its own regulatory domain to be set first
Jul 23 17:37:02 max kernel: [    9.058234] cfg80211: Regulatory domain changed to country: US
Jul 23 17:37:02 max kernel: [    9.058241] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul 23 17:37:02 max kernel: [    9.058252] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jul 23 17:37:02 max kernel: [    9.058262] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Jul 23 17:37:02 max kernel: [    9.058272] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 23 17:37:02 max kernel: [    9.058282] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 23 17:37:02 max kernel: [    9.058291] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 23 17:37:02 max kernel: [    9.058301] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Jul 23 17:37:03 max kernel: [    9.986516] r8169 0000:01:00.0: eth0: link up
Jul 23 17:37:03 max kernel: [    9.986969] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jul 23 17:37:03 max kernel: [    9.987775] br0: port 1(eth0) entering forwarding state
Jul 23 17:37:03 max kernel: [    9.987788] br0: port 1(eth0) entering forwarding state
Jul 23 17:37:03 max kernel: [    9.988362] ADDRCONF(NETDEV_CHANGE): br0: link becomes ready
Jul 23 17:37:03 max ntpdate[808]: name server cannot be used: Temporary failure in name resolution (-3)
Jul 23 17:37:03 max kernel: [   10.225938] init: failsafe main process (571) killed by TERM signal
Jul 23 17:37:03 max acpid: starting up with proc fs
Jul 23 17:37:03 max acpid: 1 rule loaded
Jul 23 17:37:03 max acpid: waiting for events: event logging is off
Jul 23 17:37:03 max cron[861]: (CRON) INFO (pidfile fd = 3)
Jul 23 17:37:03 max cron[891]: (CRON) STARTUP (fork ok)
Jul 23 17:37:03 max cron[891]: (CRON) INFO (Running @reboot jobs)
Jul 23 17:37:03 max kernel: [   10.512757] device wlan0 entered promiscuous mode
Jul 23 17:37:03 max kernel: [   10.519839] br0: port 2(wlan0) entering forwarding state
Jul 23 17:37:03 max kernel: [   10.519859] br0: port 2(wlan0) entering forwarding state
Jul 23 17:37:03 max hostapd: wlan0: IEEE 802.11 Configured channel (36) not found from the channel list of current mode (2) IEEE 802.11a
Jul 23 17:37:03 max hostapd: wlan0: IEEE 802.11 Hardware does not support configured channel
Jul 23 17:37:03 max kernel: [   10.526742] device wlan0 left promiscuous mode
Jul 23 17:37:03 max kernel: [   10.526784] br0: port 2(wlan0) entering forwarding state
Jul 23 17:37:14 max kernel: [   20.976023] br0: no IPv6 routers present
Jul 23 17:37:18 max kernel: [   24.992032] br0: port 1(eth0) entering forwarding state
```

---

### Post by bakegoodz on 2012-08-01
I tried the route of changing regulatory settings. I even recompiled crda and recompile the wireless modules to use a static regdb I created (net/wireless/db.txt)

It certainly appears that Ath9k project is putting out bad information:
> Features and modes of operation

All of these modes of operation are supported and should work on all ath9k cards.

Modes of operation

    Station Mode

    AP Mode

    IBSS Mode

    Monitor Mode

    Mesh point with HT support, as well as RSN

    WDS (as of >= 2.6.37)

Because I have 3 ath9k adapters and I found one that works.

Working adapter Ubiquiti SR71-E Atheros - AR9280

```

Band 2:
		Capabilities: 0x11ce
			HT20/HT40
			SM Power Save disabled
			RX HT40 SGI
			TX STBC
			RX STBC 1-stream
			Max AMSDU length: 7935 bytes
			DSSS/CCK HT40
		Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
		Minimum RX AMPDU time spacing: 8 usec (0x06)
		HT TX/RX MCS rate indexes supported: 0-15
		Frequencies:
			* 5180 MHz [36] (17.0 dBm)
			* 5200 MHz [40] (17.0 dBm)
			* 5220 MHz [44] (17.0 dBm)
			* 5240 MHz [48] (17.0 dBm)
			* 5260 MHz [52] (20.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5280 MHz [56] (20.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5300 MHz [60] (20.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5320 MHz [64] (20.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5500 MHz [100] (20.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5520 MHz [104] (20.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5540 MHz [108] (20.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5560 MHz [112] (20.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5580 MHz [116] (20.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5600 MHz [120] (disabled)
			* 5620 MHz [124] (disabled)
			* 5640 MHz [128] (disabled)
			* 5660 MHz [132] (20.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5680 MHz [136] (20.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5700 MHz [140] (20.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5745 MHz [149] (30.0 dBm)
			* 5765 MHz [153] (30.0 dBm)
			* 5785 MHz [157] (30.0 dBm)
			* 5805 MHz [161] (30.0 dBm)
			* 5825 MHz [165] (30.0 dBm)

```

Not working adapter Netgear WNDA3200 - Atheros AR9280

```

Band 2:
		Capabilities: 0x114e
			HT20/HT40
			SM Power Save disabled
			RX HT40 SGI
			RX STBC 1-stream
			Max AMSDU length: 3839 bytes
			DSSS/CCK HT40
		Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
		Minimum RX AMPDU time spacing: 8 usec (0x06)
		HT TX/RX MCS rate indexes supported: 0-15
		Frequencies:
			* 5180 MHz [36] (30.0 dBm) (passive scanning, no IBSS)
			* 5200 MHz [40] (30.0 dBm) (passive scanning, no IBSS)
			* 5220 MHz [44] (30.0 dBm) (passive scanning, no IBSS)
			* 5240 MHz [48] (30.0 dBm) (passive scanning, no IBSS)
			* 5260 MHz [52] (30.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5280 MHz [56] (30.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5300 MHz [60] (30.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5320 MHz [64] (30.0 dBm) (passive scanning, no IBSS, radar detection)
			* 5500 MHz [100] (disabled)
			* 5520 MHz [104] (disabled)
			* 5540 MHz [108] (disabled)
			* 5560 MHz [112] (disabled)
			* 5580 MHz [116] (disabled)
			* 5600 MHz [120] (disabled)
			* 5620 MHz [124] (disabled)
			* 5640 MHz [128] (disabled)
			* 5660 MHz [132] (disabled)
			* 5680 MHz [136] (disabled)
			* 5700 MHz [140] (disabled)
			* 5745 MHz [149] (30.0 dBm) (passive scanning, no IBSS)
			* 5765 MHz [153] (30.0 dBm) (passive scanning, no IBSS)
			* 5785 MHz [157] (30.0 dBm) (passive scanning, no IBSS)
			* 5805 MHz [161] (30.0 dBm) (passive scanning, no IBSS)
			* 5825 MHz [165] (30.0 dBm) (passive scanning, no IBSS)

```

---

### Post by bakegoodz on 2012-08-03
Wow, I figured it out how to open all the channels and adapters for AP Mode. You won't believe how much time I spent on this, Thats the way I am, I keep going until it works. It was a regulatory domain issue, I found that the ath9k driver will restrict the capabilities of the wireless channels according to the EEPROM or firmware country code burned into the adapter and then restricted more with crda if the codes don't match. ```
dmesg | grep EEPROM
``` You have to recompile ath9k to get it to not restrict by EEPROM code. In my experience this is required for a 5Ghz access point to work at all, except for just channel 36 on the Ubiquity adapter. Here are my notes to repeat it, someone is welcome to use it for a guide.

```

apt-get install build-essential linux-source
cd /usr/src/linux-source-3.2.0/drivers/net/wireless/ath/
wget --no-check- certificate https://dev.openwrt.org/export/32952/trunk/package/mac80211/patches/403-ath_regd_optional.patch
patch -Np5  -i 403-ath_regd_optional.patch
echo "#define ATH_USER_REGD 1"|cat - regd.c > /tmp/out && mv /tmp/out regd.c
mkdir /usr/src/mytree
cd /usr/src/mytree
cp /boot/config-`uname -r`  .config
cp /usr/src/linux-headers-3.2.0-26-generic/Module.symvers .
cd /usr/src/linux-source-3.2.0/
make EXTRAVERSION=-21-generic O=/usr/src/mytree prepare
make EXTRAVERSION=-21-generic O=/usr/src/mytree outputmakefile
make EXTRAVERSION=-21-generic O=/usr/src/mytree archprepare
make EXTRAVERSION=-21-generic O=/usr/src/mytree modules SUBDIRS=scripts
make EXTRAVERSION=-21-generic O=/usr/src/mytree modules SUBDIRS=drivers/net/wireless/ath
cp -v /usr/src/mytree/drivers/net/wireless/ath/ath.ko /lib/modules/3.2.0-26-generic/kernel/drivers/net/wireless/ath/
cp -v /usr/src/mytree/drivers/net/wireless/ath/ath9k/ath9k.ko /lib/modules/3.2.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
depmod -a
reboot

```

Disclaimer: Regulatory domain is there to keep devices from using the wrong frequencies in certain countrys. I still have crda restricting me to channels allowed in the US. The problem with is that EEPROM in all my adapters was not set to US. I bought the Ubiquity adapter from retail in the US, but it still had "the World" code burned into it and when masked by US domain it only allowed one channel for AP Mode. Two other adapters I bought on Ebay and their country codes when combined with US settings in crda blocked all channels from using AP Mode. Regdomain are a real pain but I guess Atheros and the ath9k project are dedicated to not anger the world's communication regulators.

---

### Post by zeromemory on 2012-11-26
You sir are super awesome for figuring this out.

I was using your instructions on how to recompile ath9k but ran into problems when using them as is. The following slightly changed set of commands worked for getting things compiled under Linux Mint 13 and should work for Ununtu 12.04

```

# wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.6-1.tar.bz2
# tar xvf compat-wireless-3.6.6-1.tar.bz2
# cd compat-wireless-3.6.6-1/drivers/net/wireless/ath/
# wget --no-check-certificate https://dev.openwrt.org/export/32952/trunk/package/mac80211/patches/403-ath_regd_optional.patch
# patch -Np5 -i 403-ath_regd_optional.patch
# echo "#define ATH_USER_REGD 1" | cat - regd.c > /tmp/out && mv /tmp/out regd.c
# cd -
# cd compat-wireless-3.6.6-1
# make
# sudo make install

```

---

### Post by gertjan_hofman on 2013-11-25
Very, very helpful.  Probably would have never solved this without this post. Thanks

---

### Post by h.hittini on 2014-07-09
When I tried to make I got the following errors; I used make -d
I'm running Ubuntu 13.10 and kernel 3.11


```

Reaping losing child 0x0835d848 PID 25096
make[3]: *** [/root/compat-wireless-3.6.6-1/drivers/bcma/main.o] Error 1
Removing child 0x0835d848 PID 25096 from chain.
Reaping losing child 0x09106678 PID 25095
make[2]: *** [/root/compat-wireless-3.6.6-1/drivers/bcma] Error 2
Removing child 0x09106678 PID 25095 from chain.
Reaping losing child 0x0884ddf8 PID 24942
make[1]: *** [_module_/root/compat-wireless-3.6.6-1] Error 2
Removing child 0x0884ddf8 PID 24942 from chain.
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-12-generic'
Reaping losing child 0x088c8600 PID 24754
make: *** [modules] Error 2
Removing child 0x088c8600 PID 24754 from chain.
 
```

---

### Post by h.hittini on 2014-07-14
The previous errors were because of a new kernel and an old compate-wireless version, I tried backports 3.15 with this patch [https://dev.openwrt.org/browser/trunk/package/kernel/mac80211/patches/403-ath_regd_optional.patch?rev=39442](https://dev.openwrt.org/browser/trunk/package/kernel/mac80211/patches/403-ath_regd_optional.patch?rev=39442) but it didn't work
Can you recommend me something?
Please note that I'm using Ubuntu 13.10 server with 3.11 kernel

---

