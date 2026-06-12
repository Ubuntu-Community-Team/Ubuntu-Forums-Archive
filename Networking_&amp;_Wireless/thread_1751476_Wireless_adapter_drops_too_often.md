---
title: "Wireless adapter drops too often"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by Slave2Metal on 2011-05-06
Have been using a netgear wna1000 since 10.04, using compat wireless and recompiling at every kernel upgrade.  Then finally did a fresh install of 10.10 about 2 months ago, but the necessary drivers are there, so no need for compat and recompiling.  The connection drops every so often, so I did a network upgrade to 11.04, same thing as the previous distro, no recompiling, but drops off frequently.  


lsmod shows module "mac 80211" being used by two drivers, carl9170 and ar9170usb.  Also, module cfg80211 shows carl9170, ar9170usb, mac80211 and ath drivers being used.  I'm not sure what action to take to get a reliable connection.

Using 10.04 and compat wireless, I was using ar9170usb, but the connection dropped frequently.

---

### Post by Slave2Metal on 2011-05-18
When the connection drops, nothing but a shut down and restart gets the connection going.  So I blacklisted the driver ar9170usb and now when it drops, a few seconds later it will reconnect.  That's progress I suppose.

---

### Post by nbound on 2011-06-20
Install the compat-wireless package (it wont be named that) from synaptic, i got much improved connectivity (especially for torrents, but less dropouts overall, roughly equivalent to the old ar9170usb driver) using that.

See the howto in my sig if need more detail :)

---

