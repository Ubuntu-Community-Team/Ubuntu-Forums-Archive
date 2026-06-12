---
title: "D-Link EBR2310 fails to respond to DHCPDISCOVER"
date: 2010-10-07
forum: Networking &amp; Wireless
---

### Post by website.reader3 on 2010-10-07
Can anyone point me as to why my D-Link Router EBR-2310 is not answering the DHCPDISCOVER messages on the auto eth0 interface?  I can see the leds blink on the LAN port but the syslog shows that the dhcp discover times out and fails.

However when I connect a Windows machine to the same router, it goes through the dhcp discover process, gets a dynamic ip and becomes functional.

I tried using tcpdump to look at the packets but that failed.

This is a brand new machine (lucid edition) and I can only connect it to the local router before getting internet access.

I've tried the "sudo dhclient eth0" command also, but it keeps timing out.  I am wondering if the D-Link router just doesn't know what to do?

:confused:

---

### Post by website.reader3 on 2010-10-07
Problem is resolved, the MAC Address filter in the EBR2310 router was turned on, so it blocked the new MAC.

This option might be obstructive, you might have to reset the router to factory settings if trying to log in to the admin port from a different machine than the one used to make the initial MAC filter settings.

---

