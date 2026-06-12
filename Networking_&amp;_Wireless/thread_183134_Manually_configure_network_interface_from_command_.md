---
title: "Manually configure network interface from command line?"
date: 2006-05-27
forum: Networking &amp; Wireless
---

### Post by PatrickMay16 on 2006-05-27
Hello,

I set up the sever install of Ubuntu on my spare machine. It automatically configured the ethernet using DHCP. I'd prefer to set it up manually so it uses an IP address I assign to it. I'd use the network preferences tool in GNOME, but I don't have GNOME or X installed since this is going to be a server.

How do you configure the network interface from the command line? 

Thanks in advance, everyone.

---

### Post by 5-HT on 2006-05-27
All you need to do is edit /etc/network/interfaces accordingly.

For a description of the syntax and options, see:
```
 man interfaces 
``` 

The man page has a quick description and example of what is required to configure a static address.

HTH

---

### Post by PatrickMay16 on 2006-05-27
Thanks, 5-HT.

---

