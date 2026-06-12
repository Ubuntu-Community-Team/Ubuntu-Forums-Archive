---
title: "wpa vs wpa2 - dhcp"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by ittiam on 2009-04-29
I changed the encryption of my wireless connection from WPA to WPA2. Then made change to my wpa_supplicant.conf by updating proto to RSN. Once I made this change, after boot up I am associated with the AP but I am getting dhcp address from it. But once i do 

```
sudo dhclient eth1
```

I gets the IP address. (Sometimes I had to kill wpa_supplicant and start it again)

So i reverted back to WPA, then everything works fine.

Whats it with WPA2 and DHCP?

---

