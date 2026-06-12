---
title: "Samba and DNS"
date: 2013-05-27
forum: Networking &amp; Wireless
---

### Post by wclune on 2013-05-27
Hi All, my ISP decided to make a crazy change in there DNS recently and it has reaked havok on our home network. I believe I understand that samba uses DNS in the resolving of hostnames. Well now when a samba client tries to resolve a hostname of a pc or a printer it queries DNS and our isp returns some IP address on its network.
ping \\pcnetbiosname returns a server in there network. how do i stop samba from using DNS for Netbios resolution??

Sorry if this post is out of place.

---

### Post by redmk2 on 2013-05-27
> **wclune said:**
> Hi All, my ISP decided to make a crazy change in there DNS recently and it has reaked havok on our home network. I believe I understand that samba uses DNS in the resolving of hostnames. Well now when a samba client tries to resolve a hostname of a pc or a printer it queries DNS and our isp returns some IP address on its network.
ping \\pcnetbiosname returns a server in there network. how do i stop samba from using DNS for Netbios resolution??

Sorry if this post is out of place.
Samba dos not use DNS to resolve hostnames.  It does use the entries in the /etc/hosts file to convert local hostnames to NETBIOS names or broadcasts to resolve unknown names.  Nothing your ISP does with DNS should affect your Samba configuration.  What is the specific error you are getting?  What OS is the client running?

---

