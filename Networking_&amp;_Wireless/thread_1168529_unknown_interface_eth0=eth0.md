---
title: "unknown interface eth0=eth0"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by laode on 2009-05-24
I'm facing strange problems with eth0 going worse the more I test.

I had a perfect running Ubunti 9.04 behind a DSL-router (D-Link DIR-635) with DHCP.

than I inteded to use dynDNS, installed inadyn-client, configured port-forwarding 22 to PC's ip-adress, but could not make it working, because router needs rebout when I change forward to IP-Adress, resulting in assigning new IP-Adress to PC, so forwarding can't work.

So I decide to use static IP-Adress, disabeld DHCP in router and changed PCs adress to static (192.168.0.199). From this moment on I could not connect the PC anymore to the web. inner-LAN connection, even windows-to-Ubuntu with ssh via port 22 worked fine.

After a while of looking for reasons, I found this message after 'networking restart':
ignoring unknown interface eth0=etho.

I skip a lot of strange experience while testing more and more, coming to the status now:

swichted everythng back to DHCP, but now I don't have any net-connect at all from this pc

I see the card with it's MAC and DHCP setting in control-center, but when I do 'ifup eth0' I get "ignoring unknown interface eth0=etho"

with ifconfig I see no ipv4 adress, but mac-adress

I shutdown the Pc completely and tried again, no change.

what can I do else to analyse/set proper configuration ?

thanks for any help, laode

---

### Post by Iowan on 2009-05-24
> **laode said:**
> ... inner-LAN connection, even windows-to-Ubuntu with ssh via port 22 worked fine.Probably DNS issue - edit /etc/resolv.conf. DHCP usually sets this - static address means you must intervene.
> **laode said:**
> ...what can I do else to analyse/set proper configuration ?
Is *ifconfig -a* showing multiple ethX's - or just eth0?  Is there a setup line in /etc/network/interfaces for "etho"?  Check */etc/udev/rules.d/70-persistent-net.rules* to see if "etho" shows up there.
I suspect there's another place to look for "etho" that I'm missing...

---

