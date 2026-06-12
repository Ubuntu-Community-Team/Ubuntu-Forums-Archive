---
title: "home network not showing anymore"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by Ampi on 2009-09-08
I had my wireless perfectly well working. Because of some problems with another (windows) laptop I logged into my router. There I changed my security settings to WPA-PSK (TKP).
Because I had to reset to factory settings I do not remember what my settings were before. 
Now on both laptops (UNR and Windows) there is a list of available networks except for my own network. 
On both laptops I configured my network with the corresponding security and authentication settings. 
How can I get my network back in the list?

---

### Post by Bucky Ball on 2009-09-08
Perhaps change the security settings on he local machine to WPA to match the routers and make sure correct ESSID and WPA key. (System->Admin->Network)

Make sure your router is still acting as a DHCP server and serving IP addresses if you had it set up that way.

You can set a static IP on the local machine by using the router's IP as the gateway and the mask will show up automatically. Hit the DNS tab and get the correct DNS server IPs. If you do this, make sure your router is NOT serving you an IP also.

---

### Post by DevinMcElheran on 2009-09-10
You may have set it as a non-broadcasting network, which basically makes it invisible, and people won't be able to see it when they look for networks. You have to go to "Connect to hidden network" or something similar, it should be under the list of networks. Click it, and type in the name of your network, you'll want to make sure it's simple, nothing you can easily misspell or mess up. If that isn't it, you should try reconfiguring your router again, and look for that option and make sure it's off, or "visible".

---

