---
title: "Problem using a wireless router as an access point"
date: 2010-11-26
forum: Networking &amp; Wireless
---

### Post by kook44 on 2010-11-26
Hi-
I have an old NetGear WGR614 that I'd like to use as a wireless access point on an existing wired network.  The existing setup is a cable modem with a 4-port switch (It's a SMCD3C "Gateway").  I want to plug the WGR614 into one of the ports on the SMC, so i can plug additional wired devices into it, as well as use wireless.

I'm having some trouble with my configuration. I've gone through the setup process many times, trying different configurations, and sequences of the steps - and I still can't get it 100% correct.  Here's what I have done:

First, I went to the "LAN IP" section of the WGR614 and provided a static IP address within the SMC's subnet, and disabled DHCP. After applying the changes, the WGR614's admin interface responds on the new IP, and devices connected to it get IPs from the SMC's DHCP.  This is a positive step, however, the WGR's wireless radio would not turn on - even though the settings were configured to "ON".  The wireless radio light on the front of the unit wouldn't illuminate.
I'm assuming this is because under the WGR's "Internet Port" setting, it was still set to use DHCP.  The router's status at this point would display an ip of 0.0.0.0. So, I entered the same static IP I did on the "LAN IP" page, as well as the subnet mask (same as the SMC's LAN subnet mask), and the gateway (SMC's IP address).  At this point the GUI required that i enter DNS servers, sol I just used the SMC's.

After saving these changes, the wireless radio came on - devices can successfully connect to it, all devices getting IPs from the SMC, DNS working properly across the board.  HOWEVER, the WGR's admin interface is no longer available on its IP.  If i browse for connected devices in the SMC's admin - i see the WGR's ip with a device name of "unknown".

This is very perplexing.  So - i can basically keep on keepin' on, but i can't make any changes to the configuration.  I'm definitely not a networking expert.  Any ideas would be greatly appreciated.

Thanks!

---

