---
title: "Ndiswrapper &quot;unknown symbol&quot;, driver loaded but can't be used"
date: 2011-09-15
forum: Networking &amp; Wireless
---

### Post by dea_jul on 2011-09-15
Hi,

I installed Ubuntu 11 on a friend's laptop, but I'm having trouble getting the wireless network up. The computer is a Gateway M-6846 (also labeled W650A). lspci indicates the network card is Marvell, and I've attempted to install the 64-bit windows driver via ndiswrapper from [here]("http://support.gateway.com/us/en/product/default.aspx?tab=1&modelId=2358").

It appears ndiswrapper is having trouble using (but not loading) the driver. 

```

root@Gateway-Z:/var/log# ndiswrapper -l
netmw148 : driver installed
	device (11AB:2A08) present

```

I'm getting these messages in syslog:
```

Sep 15 17:39:27 Gateway-Z kernel: [  117.762177] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
Sep 15 17:39:27 Gateway-Z loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver netmw148
Sep 15 17:39:27 Gateway-Z kernel: [  117.876360] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeMdl'
Sep 15 17:39:27 Gateway-Z kernel: [  117.876387] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
....(more of the same here)....
Sep 15 17:39:27 Gateway-Z kernel: [  117.877131] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netmw148'
Sep 15 17:39:27 Gateway-Z kernel: [  117.878407] ndiswrapper (load_wrap_driver:108): couldn't load driver netmw148; check system log for messages from 'loadndisdriver'

```

I've also gone through the steps outlined in the [ndiswrapper troubleshooting guide]("http://ubuntuforums.org/showthread.php?t=885847"), and I've tried the wn311t driver, per the suggestion [here]("http://ubuntuforums.org/archive/index.php/t-833363.html"), but could not get the latter loaded properly. 

Any help would be appreciated. I'll keep poking around, but I've sort of hit the end of my options, and I don't know how to fix the syslog issues above.

Thanks!

---

### Post by dea_jul on 2011-09-24
Got it working. For those who find this from google:

I missed the section of the ndiswrapper helper thread which said that "unknown symbol" in your logs means a problem with the driver, which you won't be able to solve. 

I eventually gave up on getting it to work on 64 bit (no one has, AFAIK). I downgraded to 32 bit ubuntu, but the instructions I found above (linked in my original query) did not work for me; I got the driver installed, and got wlan0 to appear, but was unable to connect to any wireless networks. My syslog looked like this:
```
Sep 24 01:08:15 Gateway-M kernel: [ 3697.230096] wlan0: ethernet device 00:16:44:71:28:20 using NDIS driver: netmw14x, version: 0x2010403, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 11AB:2A08.5.conf
Sep 24 01:08:15 Gateway-M kernel: [ 3697.230145] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Sep 24 01:08:15 Gateway-M kernel: [ 3697.235538] usbcore: registered new interface driver ndiswrapper
Sep 24 01:08:15 Gateway-M NetworkManager[784]: <error> [1316840895.204651] [nm-device-wifi.c:3100] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 0)
Sep 24 01:08:15 Gateway-M NetworkManager[784]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
```

I found further instructions here: [http://nohair.com/code/doku.php/computers:ubuntu:gateway_m-6319]("http://nohair.com/code/doku.php/computers:ubuntu:gateway_m-6319")

Note, the package he provides did not work. I downloaded the driver from the link he provided directly ([here]("http://firmware.netgear-forum.com/WN511T/wn511t_3_0_setup.zip")), which looks identical to the prior package I had installed, but didn't result in the same problems.

So:
```
unzip wn511t_3_0_setup.zip
cd Disk1
unshield x data1.cab
unshield x data2.cab
cd Win2KXP_Target
ndiswrapper -i NetMW14x.inf 
ndiswrapper -l
ndiswrapper -a 11ab:2a08 netmw14x
ndiswrapper -m
depmod -a
modprobe ndiswrapper
iwlist scan
```

Good luck!

---

