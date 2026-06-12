---
title: "Lost network after upgrade"
date: 2011-12-14
forum: Networking &amp; Wireless
---

### Post by Shellbak3 on 2011-12-14
I have a new specialty computer that had to go back to the vendor to have new NICs installed (the Gigabit NIC didn't support Jumbo Frames).  When I received it last week I plugged it in and verified the best I could that the new NIC supported "jumbo frames".  I plugged it in to a LAN and was able to connect and download and install Chrome.  Ubuntu nagged me that I should attend to a large update to bring 10.04 current.  I did this and now cannot reach the internet.  When I use the browser I get an immediate error that the network can't be reached.

Before the update the two NICs were eth0 (10/100 mbs) and eth1 (1 gbs).  After the update it showed eth2 and eth3.  On advice from the vendor I deleted the old eth0 and eth1 and added what I think are the correct MAC addresses for the new NICs.  No go.  eth2 is set for auto and DHCP. 

I notice that NetworkManager has very different ip addresses for name servers than the notebook I'm using now which is connected by wireless to the same router.

I'm now at a loss of what to do to next either to diagnose the problem or fix it.  :confused:  

I'm kind of new to Linux and Ubuntu.

TIA
Nate

---

### Post by Shellbak3 on 2011-12-14
OK, I found it from information on this link:
[https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html]("https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html")

I had to edit the /etc/network/interface file to conform with the new configuration.  :P

---

