---
title: "Local Static IP Kills File Sharing"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by Quake3DeathGod on 2009-03-24
I'm running Mint Linux, 64bit. 

I have to have a static IP so I can use transmission. (bittorrent) If I give myself a local static IP, then I lose my connection to my windows shares on the local network. If I use an auto IP, then I can access the local shares.... Any suggestions on fixing this?

---

### Post by Iowan on 2009-03-24
Have you tried setting up a static lease on your DHCP server?

---

### Post by Quake3DeathGod on 2009-03-25
Never heard of it. The DHCP would be the router.... I've looked at every menu in there, and I dont see anything like that. Mine is a WRT54GS. What might it be under, or what else might Linksys call it?

---

### Post by Iowan on 2009-03-25
I found an [online]("http://www.fixya.com/support/p259964-linksys_wireless_g_wrt54gs_router/manual-20191") manual for your router, but haven't found where/how to set up static/fixed addresses/leases. My DHCP server will - but it's Ubuntu-based.

---

### Post by WrathofthePenguin on 2009-03-25
> **Quake3DeathGod said:**
> I'm running Mint Linux, 64bit. 

I have to have a static IP so I can use transmission. (bittorrent) If I give myself a local static IP, then I lose my connection to my windows shares on the local network. If I use an auto IP, then I can access the local shares.... Any suggestions on fixing this?

Can you give us the output of an ifconfig command? What are the ip addresses of the other PCs - the Windows boxes?

WOTP

---

