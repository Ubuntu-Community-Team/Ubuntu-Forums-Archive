---
title: "Can I use any of these wireless cards for aircrack-ng or backtrack 4 R1"
date: 2010-08-27
forum: Networking &amp; Wireless
---

### Post by masterchief0026 on 2010-08-27
Hi
So we have 3 laptops, an Hp dv2000, a Dell Xps M1330, and an older Hp dv4000, and a usb adapter that came with the router

The hp dv2000 has a Broadcom 4321AG 802.11a/b/g/draft-n wireless adapter.
The Dell M1330 has a Dell Wireless 1505 Draft 802.11n WLAN minicard.
The older dv4000 has an Intel PRO/Wireless 2200BG Mini PCI Adapter.
Lastly, the usb adapter is a Netgear WGT111T 
more info here [http://kb.netgear.com/app/products/model/a_id/2559](http://kb.netgear.com/app/products/model/a_id/2559)

i tried running backtrack 4 R1 through vmware on my dv2000, and it didnt detect my card, although it did connect to the internet. then i tried aircrack, but it failed too.

on the older dv4000, i installed aircrack-ng and macchanger through terminal and followed this video ([http://www.youtube.com/watch?v=6RIUOoMdkv8](http://www.youtube.com/watch?v=6RIUOoMdkv8)) 
everything worked except for the last command (sudo aireplay-ng -1 0 -a [bssid] -h [fake mac] mon0) and i got an error saying mon0 was not detected. 

i havent tried either the usb or the dell, but i wanted to know if they are compatible. i still need to find the usb adapter, but i can try the dell anytime, or burn backtrack 4 to a disk.

thanks

---

