---
title: "D-Link DWL-650"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by yyx on 2010-04-06
I just installed ubuntu 9.10 on my old laptop (a Dell 8200) and I've hit a dead end trying to get wireless working using a D-Link DWL-650 rev P.

All of the information about this that I've come across so far seems either out of date, or beyond my level of understanding (I haven't used linux since redhat 6.1 11 years ago).

ifconfig shows both wifi0 and wlan0...The [WifiDocsWiFiHowTo]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo") says that this may be the cause of my problem, but the part about what to do next is incomplete.

Sofar I've tried the steps listed [here]("http://ubuntuforums.org/showthread.php?t=296179"), but I still get both wifi0 and wlan0 after adding the following to /etc/modprobe.d/blacklist-hostap-utils:

blacklist orinoco_plx
blacklist orinoco_cs
blacklist orinoco_pci
blacklist orinoco

These instructions also tell me to replace some stuff in /etc/pcmcia/config, which doesn't exist in this installation, so I'm guessing these instructions are out of date (written in Nov. 2006).

Adding those blacklist items to /etc/modprobe.d/blacklist, as the WiFiHowTo suggests, results in losing both wifi0 and wlan0.


Finally the WiFiHowTo repeatedly refers to (System)->(Administration)->(Networking), but I only see (Networking Tools) there...Is this the same thing?

---

### Post by chili555 on 2010-04-06
> ifconfig shows both wifi0 and wlan0...The WifiDocsWiFiHowTo says that this may be the cause of my problem, I doubt it. Many wireless interfaces have a 'dummy' for-internal-use-only interface. With the orinoco suite balcklisted, does the interface show up in *iwconfig*? Does this produce a result?```
sudo iwlist wlan0 scan
```Please post:```
lspcmcia -v
```Thanks.

---

### Post by yyx on 2010-04-06
> **chili555 said:**
> With the orinoco suite balcklisted, does the interface show up in *iwconfig*?

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11-DS  Mode:Managed  
          
wlan0     IEEE 802.11-DS  Mode:Managed  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I'm pretty confused, so I might have been looking at the wrong thing e.g. ifconfig.

```
sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down
```

```
lspcmcia -v
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:01.0)
	Configuration:	state: on	ready: unknown
Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:01.1)
	Configuration:	state: on	ready: unknown
			Voltage: 5.0V Vcc: 5.0V Vpp: 0.0V
Socket 1 Device 0:	[hostap_cs]		(bus ID: 1.0)
	Configuration:	state: on
	Product Name:   D-Link DWL-650 Wireless PC Card RevP ISL37101P-10 A3 
	Identification:	manf_id: 0x000b	card_id: 0x7110
			function: 6 (network)
			prod_id(1): "D-Link" (0x1a424a1c)
			prod_id(2): "DWL-650 Wireless PC Card RevP" (0x6ea57632)
			prod_id(3): "ISL37101P-10" (0xdd97a26b)
			prod_id(4): "A3" (0x56b21f52)

```

---

### Post by chili555 on 2010-04-06
> Adding those blacklist items to /etc/modprobe.d/blacklistThat file should be named blacklist[COLOR="Red"].conf[/COLOR]. Please remove that file, because we are going to try another approach:```
sudo rm /etc/modprobe.d/blacklist
sudo gedit /etc/modprobe.d/blacklist.conf
```Add two new lines:```
blacklist hostap
blacklist hostap_cs
```Proofread carefully, save and close gedit. Reboot and report your results.

---

### Post by yyx on 2010-04-06
I wrote that first post on my windows machine, so I was copy pasting from the howto, but I did make those changes to blacklist.conf.

With
```
blacklist hostap
blacklist hostap_cs
```

and with the various orinoco exclusions listed earlier commented out, I see 'device not ready' under wireless networks on the top right of my screen.
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11-DS  Mode:Managed  
          
wlan0     IEEE 802.11-DS  Mode:Managed  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down


```

---

### Post by chili555 on 2010-04-07
Please post:> rfkill list
lsmod | grep dellIf the module *dell-laptop* is listed, please do:```
sudo rmmod -f dell-laptop
sudo iwlist wlan0 scan
```Did the wireless come to life? If so, we will tweak one file.

---

### Post by yyx on 2010-04-07
*rfkill list* returns nothing and I don't see a dell-laptop module:

```
lsmod | grep dell
dell_wmi    2564   0
```

---

### Post by yyx on 2010-04-07
Rather than going crazy struggling to get some obsolete junk working, I found a mini pci wireless adapter on ebay.  Its on the list of compatable wireless adapters and only 12 bucks, an Intel Pro/Wireless 2200 using the ipw2200 driver.

Do I need to uninstall hostapd, or revert any other changes to ensure that the new card is recognized?

---

### Post by chili555 on 2010-04-07
No changes whatever. The card will work with a completely different driver, ipw2200, unrelated in any way to those you have previously worked with.

---

