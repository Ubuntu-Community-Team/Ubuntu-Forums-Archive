---
title: "network manager can't edit connections"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2009-11-20
never a good idea to post when worked up, but I have spent 4 hours trying to fix this issue.

basically I can't seem to get the nm-applet/Network Manager to delete a connection in the list. I seem to have 2 wlanj0 entries, one ni "wired connections" and one in "Wireless". i want to delete the incorrect one in wired, but get this message about ifupdown being read-only.

I have set "managed=true" in the conf file.

I can't even edit the settings, which is what is causing me to not be able to connect to the internet, as it's got a static IP/gateway which is wrong.

PLease help me.

---

### Post by ashishWaghmare on 2009-11-21
hi , 
 Even I faced the same problem. Somehow /etc/network/interfaces files configuration is being overridden by network-manager.
 And can't edit network-manager connections. 
 So when, command /sbin/ifconfig is issued proper network configuration is seen. but after network-manager daemon starts, internet connectivity is lost. 
 So finally removed network manager via 

    apt-get remove network-manager network-manager-gnome

And then net worked smoothly

---

