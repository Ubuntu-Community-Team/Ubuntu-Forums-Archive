---
title: "Simple hostapd 802.11n problem - 54Mbit/s bit rate"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by markytheone on 2009-12-10
Hi guys, I have hostapd setup with my Atheros AR9220 a/b/g/n card. Its running as an access point and works fine except for one issue. When I connect my laptop to it it only connects at 54 Mbit/s. The laptop says the network is 802.11n but still only show the bit rate as 54 Mbit.s The card is running with the latest ath9k driver and seems to work fine.

Here is my /etc/hostapd/hostapd.conf
> 
interface=wlan0
driver=nl80211
ssid=Test
channel=1
hw_mode=g
auth_algs=1
ieee80211n=1
country_code=UK


Any ideas?

Thanks in advance.

Marky

---

### Post by markytheone on 2009-12-10
Any ideas on this guys?

---

### Post by markytheone on 2009-12-10
Please guys, I really need help on this...

---

### Post by Znarkus on 2009-12-20
```
hw_mode=g
```

Shouldn't that be set to "n"? Though the comments in the config suggests only a, b and g are supported.

**Edit:** Also, you should probably enable 11n with

```
ieee80211n=1
```

---

### Post by redstain on 2009-12-24
my hostapd.conf
[http://pastebin.com/m4e51f185](http://pastebin.com/m4e51f185)
 
My windows 7 Laptop tells me that im connecting at a 300Mbit rate but I have my doubts.
 
looking at your config your missing the HT Capability section.
 
ieee80211n=1 
ht_capab=[HT40+][SHORT-GI-40][DSSS_CCK-40]
 
From what i understand 'N' runs ontop of A or G (5GHz or 2.4GHz) the card I have in the machine acting as the access point is a AR9281 (single band BGN) the card in the laptop is an AR5009 (dual band AGN)
 
This is the iw list output on the access point. note the highest speed it reports is 54.
[http://pastebin.com/m622a1768](http://pastebin.com/m622a1768)
 
 
Try an iw list and see what HT cababilities your card has and try setting them in your hostapd.conf file and see if you get a result.
 
Even though Windoz says 300Mbit im not convinced, if i SCP files i get ~2100KB/s which is only 16.80 Mbps well below 54Mbps
 
Can anyone enlighten me on the performance issue...

---

### Post by markytheone on 2010-01-22
I can get it to work OK but my iphone never gets and IP via DHCP. Every other device works ok. If I disable wme in hostapd then it will connect. When wme is enabled, no iPhone :(

Any ideas?

s

---

### Post by Walmit on 2011-01-27
Sorry to reactivate an old discussion but did you solve this problem? I am struggling on the same issue.

I am using a 802.11a/b/g/n device with hostapd but the device does not advertise data rate greater than 54Mbps. If the broadcast packets are captured with wireshark, the listed supported data rates are only : "  *Supported Rates: 6.0(B) 9.0 12.0(B) 18.0 24.0(B) 36.0 48.0 54.0*" while I had expected to go up to 270Mbps.

Does anyone know if this problem is related to a wrong configuration of hostapd?

Thank in advance for any suggestion.

---

