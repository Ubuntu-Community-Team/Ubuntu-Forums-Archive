---
title: "WEP Authentication"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by robwevans on 2009-11-04
I've got a Dell Latitude D600 with an Intel 2200BG wireless card that worked great with Ubuntu 9.04. I upgraded to 9.10 and was unable to get the wireless to authenticate so I did a clean install and still am unable to get WEP to authenticate. I tried replacing Network Manager with WICD and that didn't work either. If there is no security on the access point it will connect fine but I obviously I don't want to go that route. It's an older Linksys AP that only supports WEP so changing to WPA is not an option either. 
 
Anyone else having this problem?

---

### Post by RicGag on 2009-11-09
Hi, i'm using a Toshiba laptop with Intel PRO/Wireless card an experimenting
the same problem since upgrade to Karmic ie:

the Wicd application give the message:

[COLOR=Red]"Connect failed: Unable to get ip address"[/COLOR]

I then tried to manually configure the interface like this:

dhclient eth0 down 
ifconfig -r eth0         
dhclient eth0 up      
iwlist eth0 scan|grep -E "Cell|ESSID" 
iwconfig eth0 essid 000124F05C3C7891
iwconfig eth0 freq 2.412G 
iwconfig eth0 ap 00:01:24:F0:5C:3C       as reported by wireless scanning
iwconfig eth0 key 000102030405060708090a0b0c
iwconfig eth0
iwconfig eth0 mode Managed
iwconfig eth0
dhclient eth0

but it doesn't work. Maybe you can try...

The interface work well if not using encryption.

I hope someone find the solution.

---

