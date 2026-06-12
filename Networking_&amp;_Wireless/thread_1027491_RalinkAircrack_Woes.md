---
title: "Ralink/Aircrack Woes"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by bb2120 on 2009-01-01
Having battled with ndiswrapper under Dapper a while ago, I've bought a D-Link DWL-122 Rev. C1 for my fresh install of 8.10. After installing linux-wlan-ng it works beautifully. I am however having an issue with aircrack. The error isn't listed in any of the troubleshooting documentation I've found - could anyone help me? My linux knowledge isn't great, so please be gentle :)

This is what I get:
> bede@D1520:~$ sudo -s
root@D1520:~# airmon-ng start wlan1


Interface	Chipset		Driver

wlan0		Broadcom 43xx	b43 - [phy0]
wlan1		Ralink 2573 USB	rt73usb - [phy2]
				(monitor mode enabled on mon0)

root@D1520:~# airodump-ng wlan1
[COLOR="Red"]ioctl(SIOCSIWMODE) failed: Device or resource busy[/COLOR]

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start wlan1 <#>'
Sysfs injection support was not found either.


---

### Post by lemmy999 on 2009-01-03
You are trying to bring up airmon-ng on wlan0 but the previous output suggests that the card is mon0.

it would be better to get the latest rt73 driver here ([http://homepages.tu-darmstadt.de/~p_larbig/wlan/rt73-k2wrlz-3.0.2.tar.bz2](http://homepages.tu-darmstadt.de/~p_larbig/wlan/rt73-k2wrlz-3.0.2.tar.bz2))

then 
extract archive

```
ifconfig rausb0 down
modprobe -r rt73
cd rt73-k2wrlz-3.0.1/Module
make && make install
#choose whatever is appropriate for your card wlan0/rausb0 etc
modprobe rt73 ifname=rausb0 or wlan0
```

Should be "good to go"

---

