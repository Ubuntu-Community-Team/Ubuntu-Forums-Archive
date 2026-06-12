---
title: "wireless pxe boot project theory"
date: 2012-08-24
forum: Networking &amp; Wireless
---

### Post by darkapec on 2012-08-24
I have an idea and I am not sure if it would work or not. So I though I would ask here first. 

Is it possible to netboot a device through the ethernet jack using a universal wireless adapter like the NETGEAR WNCE2001? I have never used one before, but assuming the wireless AP and key are setup and stored in the actual device I see no reason why it wouldnt work. 

I currently have my wireless router setup as my DNS and DHCP server and using ddwrt to forward any pxe boot request to my fog server.

would this setup work?

---

### Post by Jive Turkey on 2012-08-24
If the wireless device works as you describe I don't see why it wouldn't work.  If it doesn't, you might consider the gpxe/ipxe projects, each allow you to make a bootable ROM that may be compatible with your situation.

---

### Post by darkapec on 2012-08-24
> **Jive Turkey said:**
> If the wireless device works as you describe I don't see why it wouldn't work.  If it doesn't, you might consider the gpxe/ipxe projects, each allow you to make a bootable ROM that may be compatible with your situation.

Yah I saw the gpxe stuff, only problem is you have to manually type in wifi credentials + be able to boot from a cd.

I kind of envisioned a netbook environment and a situation where all the bench ethernet jacks are being occupied. 

I agree, I see no reason why it wouldnt, I just dont want to drop $40 on something if it wont. Im wondering if there are any restrictions in the pxe protocol (possibly in the router itself) where it is only listening for the pxe boot on the LAN ports.

---

