---
title: "Interface bridge| wireless to ethernet to connect xbox 360 problems"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by HellFireAus on 2009-01-05
Hi guys,
I'm having massive trouble trying to bridge my wireless interface to my ethernet interface.
I've searched for days trying to find how to fix this but not having much luck.
Every time i enable the bridge (br0) via brctl the dhclient fails to get an ip address and all connectivity cuts out.
When i remove the bridge, all is fine however.

My network devices:
```
ra0 - RALINK rt2870 based Wireless USB dongle
    - Connected to my wireless router
    - Provides internet connectivity
    - Gains DHCP IP from router (usually 192.168.1.103)
eth0 - Onboard NIC
     - Connected directly to my Xbox 360 (which has an ip of 192.168.0.2)
     - Static IP (192.168.0.1)
```

My network looks something like:
```
(Wireless modem/router)-- (ethernet) -- Windows vista pc
      | via wireless dongle
      | ra0
 [linux htpc]eth0 -- (ethernet) -- Xbox 360
```

I have heard that my wireless usb dongle may not support bridging.
It looks like it's heading that way, because every time the bridge is up 'dhclient br0' gets no DHCPOFFERs received.
I have tried different ways of setting up the bridge but still nothing.

I have gotten the xbox 360 connection working with firestarter, and also by following a guide on setting up IPMASQ.
The only problem here is that the 360 and the linux htpc are sharing an ip address to my router.
Because of this sharing and the NAT happening on my linux pc, i'm getting a moderate nat warning in xbox live and certain media features are unavaliable.

What i want to acheive is:
The Xbox gets its own ip address to the router
The Linux htpc gets its own ip address to the router
The xbox 360 to show up in the networking folder of the windows vista pc, and other pc's connected wirelessly to the router for that matter
Internet connectivity to all devices

I have also tried some IPTABLES configs but it's just lost me.
If i can't setup a bridge because my wireless usb dongle doesn't support it, is there any other way i can get what i want to acheive?
I have heard i can enable bi-directional nat or something similar but have no idea how to do it.

Cheers for any help, thanks in advance :)

---

