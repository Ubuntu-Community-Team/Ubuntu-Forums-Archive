---
title: "Network Manager won't connect"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by ignavia on 2006-06-12
First off, I have to manually start nm-applet every time I reboot, but it won't connect. I've commented out everything except lo in /etc/network/interfaces, and I created /etc/default/wpasupplicant with ENABLED=0.

My NIC is a D-Link G630 vC2 Atheros as ath0. 

Is there any way to get WPA working with the default network-admin or via command line? Or any way to get NM working for me?

Also, how can I set up a static IP with NM?

Any help is greatly appreciated.

Joe

---

### Post by ignavia on 2006-06-12
Do I have rabies? No one ever responds to my posts. I've never posted any messages with generic titles like 'help' or the like.

Perhaps I should be flattered? That if I can't do it, no one else can either? No, that can't be it...

---

### Post by skelooth on 2006-06-12
I probably cant help but I'll take a shot :)

Are you using ndiswrapper? does it show up in network admin? 

I have had limited success with deactivating and reactivating wireless cards in network admin

---

