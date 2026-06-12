---
title: "IBM T60 wireless issues"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by Ross86 on 2011-02-23
Hi guys,

I'm using a IBM Thinkpad T60 with Lubuntu 10.10 (uses network manager like Ubuntu) however my wireless is intermittent.

It's a Thomson TG585v7 modem/router.

Basically sometimes I can connect and sometimes I can't. Testing it the laptop with and without the power supply connected I'm starting to think it might be something to do with that.

I'm connected right now whilst posting this so it's not as if I can't connect at all. 

Any ideas?

---

### Post by keithpeter on 2011-02-23
Hello Ross86

What kind of encryption is your router set to use? 

I can't get WPA/WPA2 Personal type connections to work reliably (netgear D834G v3 router and T42/T60 thinkpads) with 10.04 or 10.10

cheers

---

### Post by Ross86 on 2011-02-23
The router is set to WPA/WPA2 encryption. Is it better to change it to something else?

---

### Post by chili555 on 2011-02-23
> **Ross86 said:**
> The router is set to WPA/WPA2 encryption. Is it better to change it to something else?Please try it with WPA2 only instead of mixed mode.

---

### Post by keithpeter on 2011-03-01
Hello All

T42 thinkpad with the ipw-2100 drivers: wpa2 only with psk gives same behaviour as mixed. Works for a bit then does not.

Symptoms to date

Used to work fine then got flaky a month or two ago, so I assume update issues.

Clean install of 10.04.2 with dist-upgrade a week ago resulted in working wpa/wpa2 mixed mode for a few sessions, then the repeated asking for password thing started.

Works fine on open connection and WEP, latter hidden and with MAC address filtering. The neighbours are not computer experts.:twisted:

Wifi connects fine on Windows XP on this same T42 laptop. In fact, rebooting into Windows, allowing the wifi to connect, and then rebooting into Ubuntu seems to 'reset' the wifi somehow so it connects for a bit, but then connection dropped in Ubuntu.

I'd like to pin this one down as I use 'roaming' wifi quite a lot and would rather run Ubuntu when in strange cafes &c.

Anyone any ideas? I'm reading the many threads in the forums about wifi.

---

