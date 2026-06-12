---
title: "Can other wireless in the neighbor interferred with mine ?"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by hoboy on 2010-02-15
The pass 5-6 days my NetGear wireless connection refused to connect sometimes, when I reset netgears then it connects, when I look at the connection I see 4 other wireless in the neighbor, is it possible that because of other wireless in the neighbor that my connection cut ? 
if so what can I do to prevent this ?

---

### Post by iponeverything on 2010-02-15
They can interfere 

```
sudo iwlist scan

```

will show you channel everyone is using.

If your access point is on the same channel as one of the other access points you can log into your AP and change the channel that it is using.

---

### Post by hoboy on 2010-02-15
> **iponeverything said:**
> They can interfere 

```
sudo iwlist scan

```

will show you channel everyone is using.

If your access point is on the same channel as one of the other access points you can log into your AP and change the channel that it is using.

I have run the commands
I see the channell: 11
 ESSID:"NETGEAR"
and more .
Ok I must admit I have on idea what is going on

---

### Post by hoboy on 2010-02-15
Ok I can use iwlist to scan on linux I also have portable computer with vista on how can I scan it ?
for this
"will show you channel everyone is using.

If your access point is on the same channel as one of the other access points you can log into your AP and change the channel that it is using."
 problem mentioned by iponeverything ?

---

### Post by i.r.id10t on 2010-02-15
Portable phones, microwaves, baby monitors, and other wireless access points all use the 2.4ghz range.

For best results, see what channels all the other APs are using, and set yours to something far away.  Most I've seen run on channel 6 (default, middle of range), so I'd look at using channel 1 or 11.

---

### Post by hoboy on 2010-02-15
> **i.r.id10t said:**
> Portable phones, microwaves, baby monitors, and other wireless access points all use the 2.4ghz range.

For best results, see what channels all the other APs are using, and set yours to something far away.  Most I've seen run on channel 6 (default, middle of range), so I'd look at using channel 1 or 11.

but others are not connected, how can I check their range ?

---

### Post by northd_tech on 2010-02-15
> **i.r.id10t said:**
> Portable phones, microwaves, baby monitors, and other wireless access points all use the 2.4ghz range.

For best results, see what channels all the other APs are using, and set yours to something far away.  Most I've seen run on channel 6 (default, middle of range), so I'd look at using channel 1 or 11.

Also Xbox (and other game) controllers, newer printers, store inventory/barcode scanners and credit/debit card machines, etc. are also in the 2-3 GHz range.  If someone lives in a large apartment complex or urban area, the odds are very good that they will find interference in the WiFi frequency band.

That is good advice about changing away from channel 6 IMHO.

There are often other problems (often driver or configuration) in ubuntu that will cause wireless to drop out other than frequency "cross talk" though.

---

### Post by hoboy on 2010-02-15
> **northd_tech said:**
> Also Xbox (and other game) controllers, newer printers, store inventory/barcode scanners and credit/debit card machines, etc. are also in the 2-3 GHz range.  If someone lives in a large apartment complex or urban area, the odds are very good that they will find interference in the WiFi frequency band.

That is good advice about changing away from channel 6 IMHO.

There are often other problems (often driver or configuration) in ubuntu that will cause wireless to drop out other than frequency "cross talk" though.

Mnnnnnnnnnnn it seemed like this is not easy think to do.
Do I have to login to NetGear ? to make the change ?

---

### Post by northd_tech on 2010-02-15
> **hoboy said:**
> 
Do I have to login to NetGear ? to make the change ?
Yes, you would usually need to [ethernet] cable into the router and open a Web Browser and type an IP address something like 192.168.0.1 and then enter a username and password to access the router settings.

I would personally change the broadcast SSID from "Netgear" so something like "Gumby" or "MrBill50" just so that your neighbors are less tempted to mess with your wireless settings.  Getting rid of the default username & password and using WPA or WPA2 encryption are very good ideas too.

If you check the manual for your Netgear you should find info on all this (or search their website for your model number).  The proper IP address should be listed in the manual too (but the above is probably pretty close).

[http://kb.netgear.com/app/](http://kb.netgear.com/app/)

---

