---
title: "Output of iwlist scan - help understanding?"
date: 2012-02-06
forum: Networking &amp; Wireless
---

### Post by romain.astie on 2012-02-06
Hi All,

I a trying to get my computer to connect to my network. I ran
 ```
sudo iwlist scan
```
 and am trying to understand the output:```
Cell 02 - Address: E0:46:9A:68:38:5A ESSID:"i-Sails"
Protocol:IEEE 802.11b Mode:Managed Frequency:2.437 GHz (Channel 6) Quality:40/100 Signal level:-70 dBm Noise level:-96 dBm Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 12 Mb/s; 48 Mb/s
Extra:bcn_int=100 Extra:atim=0 
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP Pairwise Ciphers (1) : CCMP Authentication Suites (1) : PSK
```

 (This is only an excerpt of the full output code)
I know what most of it means, but am wondering what the first part of the line before last means. I'm sort of a newb in the matter of protocols and such, so could I have a comprehensive explanation, please?

Thanks

---

### Post by chili555 on 2012-02-06
> IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP Pairwise Ciphers (1) : CCMP Authentication Suites (1) : PSKI assume these are the lines to which you refer. This simply means that the network *i-Sails* is using WPA2-PSK (pre-shared key.) On your computer, Network Manager should ask for the WPA/WPA2 password. If you supply the right password, case-sensitive, etc., Network Manager and your router should negotiate a connection.

Is your problem deeper than that, Chili asks suspiciously?

[http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access](http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access)> **WPA2** has replaced WPA. WPA2, which requires testing and certification by the Wi-Fi Alliance, implements the mandatory elements of IEEE 802.11i. In particular, it introduces **CCMP**, a new AES-based encryption mode with strong security. Certification began in September, 2004; from March 13, 2006, WPA2 certification is mandatory for all new devices to bear the Wi-Fi trademark.

---

### Post by romain.astie on 2012-02-06
I'm actually quite confused about this whole card-router-security thing. I recently moved, and in my past house my WPC54G Linksys card worked fine with the router/network we had there, which had WPA2 protection. Here, we have a new router, to which my card won't connect. Is there a likely reason why the card won't connect that can be found in the output I posted? Is the card just not compatible with the newer system we are using?

---

### Post by chili555 on 2012-02-06
> Quality:[COLOR="Red"]40[/COLOR]/100How far away is the router? Does it have a transmit strength setting? Is it turned up to eleven? Please see attached. Is the router set to 802.11b only? > Protocol:IEEE 802.11bWhy not mixed B, G and N?

What driver is your card using? Any clues here?```
sudo cat /var/log/syslog | grep etwork | tail -n20
```

---

