---
title: "DWL-520+ working for anyone?"
date: 2006-04-04
forum: Networking &amp; Wireless
---

### Post by bspratt on 2006-04-04
This is my last hope. Have a new Breezy install with all updates. Device manager under PCI says Dlink DWL-520+ with ACX100 22Mbps Wireless Int. When I run iwconfig I get:
wlan0 802.11b+ ESSID: "any" Nickname: "acx100 v0.2.0pre8" Access Point - all zeros; Bit Rate 22MB/s Tx-Power=18 dBm Sens=176/255; all link quality, signal level etc reads zero; no green light on back of adapter. 
1. I have read the numerous threads - the showthread.php?t=69951&page=2 response (edit interfaces) that fixes the DWL650 same chipset does not fix mine. Is there something else I can check?
2. I tried ndiswrapper once but did not like it because you had to manually enable on every boot; is there a way to automate this?
3. Is there a simple PCI or USB Wifi card that works out of the box?
Thanks - Bill

---

### Post by _linux_ on 2006-04-04
I have a DWL-G510 that works with ndiswrapper. Have you tried "sudo ndiswrapper -m" for it to automatically load on boot?

---

### Post by dbott67 on 2006-04-05
My first instinct was that the 520+ & 650+ use different drivers but it appears that they are the same (according to this page [http://support.dlink.com/faq/view.asp?prod_id=357](http://support.dlink.com/faq/view.asp?prod_id=357) ).

The other reference to check would be 
[http://acx100.sourceforge.net/](http://acx100.sourceforge.net/) and 
[http://acx100.sourceforge.net/wiki/Main_Page](http://acx100.sourceforge.net/wiki/Main_Page)

Failing that, perhaps trying ndis_wrapper might work.  The other thing to check (if you're dual-booting or have a Windows laptop available) is to verify that the card still works --- it's possible that there's something wrong with the card.

-Dave

---

### Post by bspratt on 2006-04-05
thanks - I will try ndiswrapper and report back - Bill

---

### Post by bspratt on 2006-04-05
ok - ndiswrapper is loading and reveals:
Installed ndis drivers:
airplus driver present, hardware present
however when I enter the command: sudo iwlist wlan0 scan
wlan0     No scan results
There is no green light on this card.  Do I need to de-activate my eth0 card first to get this thing to work? Dave, I think the card is good as I pulled it from a working windows box prior.  ](*,) ](*,) Any ideas at all?  Tomorrow I will go back and try to install the linux version driver - using the open source ACX100 wiki.  Thanks in advance - Bill

---

### Post by bspratt on 2006-04-08
Ok, after many hours of trying the native and ndiswrapper solutions I took the road less traveled and downgraded to Hoary and we are working beautifully!  Breezy does not play well with the DWL-520+; save yourself some pain - it works out of the box with Hoary - Bill

---

