---
title: "Wireless Adhoc Network between Ubuntu 11.10 Laptop and a Desktop with Windows XP"
date: 2012-02-07
forum: Networking &amp; Wireless
---

### Post by faucakappa on 2012-02-07
I  have on my laptop (Asus X51L) Ubuntu 11.10 and a Desktop with Windows XP (with a TP-LINK Wireless Adaptor - TL-VN422G).  

I created a DSL connection with username and password, at PPP setings tab I checked at Echo - Send PPP echo packets; at IPv4 Settings tab, at Method - Automatic(PPPoE).


The wireless connection I ceated from "Edit connection" -> Wireless Tab -> Add; 
Connection name: ubuntu-1110
**Wireless Tab:**
- SSID: ubuntu-1100
- Mode: Adhoc
- Band: Automatic
- Channel: default
- BSSID: blank
- Device MAC Address: blank
- Cloned MAC Address: blank
- MTU: automatic
**IPv4 Settings Tab:**
- Method: Shared to other computers
- I checked IPv4 addressing for this connection to complete
**IPv6 Sttings Tab:**
- Method: Ignore
**Wireless Security Tab:**
- Security: WEP 40/128-bit key (Hex or ASCII)

*_**AND CLICK SAVE**_*

On my desktop I searched my new wireless connection, I successfully  connected, but I cant access some sites like: Facebook and a few more.  Google, Wikipedia works.
  Do you have any suggestion?
  Thank you.

---

### Post by ffg1977 on 2012-02-24
Hello.
Did you try forcing DNS server on your Windows XP machine?
You can try setting DNS to 8.8.8.8 or 8.8.4.4.
Regards.

---

