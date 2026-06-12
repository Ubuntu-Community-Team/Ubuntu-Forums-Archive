---
title: "Does Ubuntu not like VPN's?"
date: 2011-10-04
forum: Networking &amp; Wireless
---

### Post by frotzed on 2011-10-04
OS: Ubuntu 11.04
VPN: StrongVPN
Type: PPTP and/or OpenVPN

I'm running into two separate issues with my VPN and Ubuntu 11.04.  It should be noted that on the same machine, while booted into Win7, both methods of VPN work flawlessly.

PPTP: I configure the VPN via the built-in tool that comes with Ubuntu.  The connection is established successfully and all is well for about 10 minutes until the connection dies.  There are no errors reported (at least visibly), I simply cannot access the internet at all.  No packets are being moved.

Perhaps there's some kind of keep-alive function I'm missing?  What I have tried is immediately after establishing the connection, begin an active ping to the host (hoping it would keep the connection alive), but the connection still dies even with that active ping.

OpenVPN: I install the network manager tool for openVPN as well as the necessary packages in the repositories, but using the network manager tool simply does not work.  The connection cannot be established.

Using [this method]("http://strongvpn.com/forum/viewtopic.php?id=169") works, however, the openVPN service is always running... I don't want that.  I can start and stop the openVPN service via command line simply enough, but this doesn't lead to results I desire.  Namely, sometimes the service will start correctly but in reality I will not be connected to the VPN.  Other times it seems to just bug out completely and for some reason I can't get on the internet at all.

Final Thoughts: At first, my big reason to keep using Windows was because of Linux's lack of gaming support... but that is slowly changing thanks to the Humble Bundle.  This VPN issue, however, is something I REALLY want to solve and in reality could keep me on Windows until such a time as Ubuntu gets these issues together.

---

### Post by collisionystm on 2011-10-04
I have never had VPN problems with Ubuntu.

Ill bet it is a 'Keep Alive' issue you are having. Make sure its enabled.

---

### Post by frotzed on 2011-10-04
> **collisionystm said:**
> Ill bet it is a 'Keep Alive' issue you are having. Make sure its enabled.

At the risk of sounding noobish, can you please show me via screenshot where this option is located?

---

### Post by collisionystm on 2011-10-04
It has to be enabled on your VPN Server I think. What exactly are you using for your VPN?

---

### Post by frotzed on 2011-10-04
I'm using [Strong VPN]("http://strongvpn.com/"), if that's what you're looking for.

It doesn't seem like the issue is with the VPN itself, because it works fine on the same computer booted into Win7.  To me it clearly is an Ubuntu issue.

---

