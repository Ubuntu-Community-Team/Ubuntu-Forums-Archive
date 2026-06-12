---
title: "Reconnecting wireless usb on each startup"
date: 2006-05-05
forum: Networking &amp; Wireless
---

### Post by amjibaly on 2006-05-05
Hi everyone,

I found out from this forum how to connect my Dlink DWL-122 usb wireless adapter, however for some reason I have to reenter these commands each time I start the computer:

sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="" authtype=opensystem
sudo dhclient wlan0

How do i get this information to "stick" so I dont have to keep entering it?

Thanks,
Abdullah

---

### Post by az on 2006-05-05
Edit your /etc/network/interfaces file like this if you are using WEP (64-bit shown, but you can use 128-bit):


auto wlan0

iface wlan0 inet dhcp
 wireless_mode managed
 wireless_essid partycentral
 wireless_enc on
 wlan_ng_key0 aa:bb:22:21:ff

---

### Post by amjibaly on 2006-05-05
Thanks Azz, I will try that. However, I am not using WEP currently (it's just open). Should I still put the above into the interfaces file? Or maybe just leave out the last line? Thanks a lot for your help!

---

### Post by az on 2006-05-05
[QUOTE=amjibaly]Thanks Azz, I will try that. However, I am not using WEP currently (it's just open). Should I still put the above into the interfaces file? Or maybe just leave out the last line? Thanks a lot for your help![/QUOTE]


Leaqve out the last two:


auto wlan0

iface wlan0 inet dhcp
wireless_mode managed
wireless_essid partycentral

---

