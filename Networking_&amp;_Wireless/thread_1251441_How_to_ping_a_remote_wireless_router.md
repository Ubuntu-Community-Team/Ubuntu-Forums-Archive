---
title: "How to ping a remote wireless router?"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by pannam on 2009-08-27
hi all,
i want to ping a remote wireless router.. i have the BSSID and the router's name..so how do i ping it ??

---

### Post by Cuba71 on 2009-08-27
You should be able to find the IP address from the router's documentation

---

### Post by pannam on 2009-08-27
> **Cuba71 said:**
> You should be able to find the IP address from the router's documentation

i am sorry i don't understand.. i am not connected to the router.. i only know the bssid of the router and the name of the router..

---

### Post by KinKiac on 2009-08-27
Is this your own router or someone elses?

---

### Post by pannam on 2009-08-28
> **KinKiac said:**
> Is this your own router or someone elses?

no .. its not mine.. if it were mine i could simply ping it  by ping 192.168.0.1 ..

---

### Post by Charly85551 on 2009-08-28
Hi,
if it is not yours then it should be without WEP or WPA (similar to public hotspots) otherwise you are walking on hacker's grounds. The easiest way is to set your WLAN adapter on automatic address allocation by  modifying */etc/network/interfaces* in a terminal mode with *sudo gedit ...* your wlan interface should read: *iface eth0 inet dhcp*. Change it accordingly!
cheers
:P

---

