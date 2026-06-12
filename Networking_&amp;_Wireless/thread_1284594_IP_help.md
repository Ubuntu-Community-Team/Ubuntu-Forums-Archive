---
title: "IP help"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by KittyAnonymous on 2009-10-06
Ive looked everywhere and cant seem to find a way to set a static ip address to my wireless network connection in ubuntu 9.04 that I can understand. Please help.

---

### Post by yknivag on 2009-10-06
Assuming you're using Ubunutu (as opposed to Kubuntu/Xubuntu etc) and running the default "Network-Manager" then you can click the Network icon up near the clock, and then "Edit Connections". Find the wireless connection you wish to assign the static IP, click "Edit..." then fill in the appropriate values in the boxes.

---

### Post by KittyAnonymous on 2009-10-06
Alright. Got that. But I cant figure out what my gateway is. Ive got the ipconfig open in the terminal, im just not entirely sure what value my gateway is. Also, thanks for the speedy help.

---

### Post by KittyAnonymous on 2009-10-06
I also need help finding what to put in the "search domains" field.

edit: I think im supposed to put my existing nameservers, but im not sure...

editedit: nope.. those are my dns servers... okay. Im back to having nothing for the whole search domain deal

editeditedit: Im hoping, sincerely, that this works. Im going to see what happens if I leave it blank. Thanks for the help guys.

Editediteditedit: golly gee willikers batman, it worked. Thanks guys. I was just being dense.

---

### Post by yknivag on 2009-10-07
Your gateway is (typically) the IP of your router.  If you don't know it then (if you already have a DHCP connection) you can find it from typing ```
route -n
``` in a terminal. On a standard config it will be the value in the "Gateway" column on the last line.

The DNS Servers field should contain the IP of your DNS server.

You can leave the "Search Domains" field blank unless you have explicit reason to use it.

A typical home setup should look something like this

```

IP : 192.168.1.10
Netmask: 255.255.255.0
Gateway: 192.168.1.1
DNS: Your.ISP.DNS.IP (you can put your router IP here if is knows about your ISP's DNS servers).
Search Domains: <blank>

```

---

