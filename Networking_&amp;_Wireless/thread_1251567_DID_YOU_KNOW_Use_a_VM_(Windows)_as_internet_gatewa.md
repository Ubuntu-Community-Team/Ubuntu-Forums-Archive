---
title: "DID YOU KNOW: Use a VM (Windows) as internet gateway (wireless)"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by bterminalx on 2009-08-27
Here's a little tip I found out. In almost any Virtualization software, you can use windows (any version) as the wireless gateway.

I recommend VirtualBox because it auto-creates an ethernet drive you can connect to.
You install windows, as normal, then in windows, you set networking as 'Host-Only' then install your wireless drivers. You then connect to the internet on the VM. 

Once you've confirmed that you're connected to the internet, either setup Internet Connection Sharing on the Ethernet driver (In the VM) or setup a bridge (recommended). 

That's done, you can connect to the internet via your VM. I hope that clears up things a bit.

---

