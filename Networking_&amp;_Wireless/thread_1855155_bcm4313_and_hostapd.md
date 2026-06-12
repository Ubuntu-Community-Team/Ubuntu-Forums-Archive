---
title: "bcm4313 and hostapd"
date: 2011-10-05
forum: Networking &amp; Wireless
---

### Post by hrickh on 2011-10-05
So, a couple weeks ago I finally got hostapd running on my Ubuntu 10.04 netbook. Then my netbook took its last breath and I went out and got another.

My problem is that the internal Wifi card is a Broadcom card. My previous netbook had an ath5k card, which was no problem to get set up as an AP.

My first order of business was to make sure I was using the open source drivers, since I'd read that neither the proprietary STA drivers nor ndiswrapper with the Windows driver would work for what I wanted (a simple AP).

The open source drivers work well for standard access to an existing AP, but I'm having a hard time getting ot to work as its own AP.

Here is what I was getting by running the version of hostapd that's included in Ubuntu 11.04's distribution:
==
Configuration file: /etc/hostapd/hostapd.conf
nl80211 not found.
nl80211 driver initialization failed.
eth1: Unable to setup interface.
==

First off, I don't understand why this interface is configurred as "eth1" instead of "wlan0".

But OK, I did some digging and found out that I needed to compile hostapd with nl80211 support. No problem. I went and downloaded the latest hostapd (0.7.3) and made sure I had libnl2-dev. I downloaded libnl-dev first, and hostapd compiled fine, but when Itried running hostapd, got the same error, even though it compiled cleanly. So I went with libnl2-dev. Now when I try to compile hostapd, I get this:

==
../src/drivers/driver_nl80211.c: In function ‘send_and_recv’:
../src/drivers/driver_nl80211.c:202:2: warning: passing argument 1 of ‘nl_send_auto_complete’ from incompatible pointer type
/usr/include/netlink/netlink.h:53:14: note: expected ‘struct nl_sock *’ but argument is of type ‘struct nl_handle *’
../src/drivers/driver_nl80211.c:217:3: warning: passing argument 1 of ‘nl_recvmsgs’ from incompatible pointer type
/usr/include/netlink/netlink.h:63:14: note: expected ‘struct nl_sock *’ but argument is of type ‘struct nl_handle *’
../src/drivers/driver_nl80211.c: In function ‘nl_get_multicast_id’:
../src/drivers/driver_nl80211.c:282:2: warning: passing argument 1 of ‘genl_ctrl_resolve’ from incompatible pointer type
/usr/include/netlink/genl/ctrl.h:30:14: note: expected ‘struct nl_sock *’ but argument is of type ‘struct nl_handle *’
../src/drivers/driver_nl80211.c: In function ‘wpa_driver_nl80211_event_receive’:
../src/drivers/driver_nl80211.c:1095:2: warning: passing argument 1 of ‘nl_recvmsgs’ from incompatible pointer type
/usr/include/netlink/netlink.h:63:14: note: expected ‘struct nl_sock *’ but argument is of type ‘struct nl_handle *’
../src/drivers/driver_nl80211.c: In function ‘wpa_driver_nl80211_init_nl’:
../src/drivers/driver_nl80211.c:1265:2: warning: implicit declaration of function ‘nl_handle_alloc_cb’
../src/drivers/driver_nl80211.c:1265:17: warning: assignment makes pointer from integer without a cast
../src/drivers/driver_nl80211.c:1272:23: warning: assignment makes pointer from integer without a cast
../src/drivers/driver_nl80211.c:1279:2: warning: passing argument 1 of ‘genl_connect’ from incompatible pointer type
/usr/include/netlink/genl/genl.h:23:13: note: expected ‘struct nl_sock *’ but argument is of type ‘struct nl_handle *’
../src/drivers/driver_nl80211.c:1285:2: warning: passing argument 1 of ‘genl_connect’ from incompatible pointer type
/usr/include/netlink/genl/genl.h:23:13: note: expected ‘struct nl_sock *’ but argument is of type ‘struct nl_handle *’
../src/drivers/driver_nl80211.c:1304:2: warning: passing argument 1 of ‘genl_ctrl_alloc_cache’ from incompatible pointer type
/usr/include/netlink/genl/ctrl.h:25:14: note: expected ‘struct nl_sock *’ but argument is of type ‘struct nl_handle *’
../src/drivers/driver_nl80211.c:1304:2: error: too few arguments to function ‘genl_ctrl_alloc_cache’
/usr/include/netlink/genl/ctrl.h:25:14: note: declared here
../src/drivers/driver_nl80211.c:1310:2: warning: passing argument 1 of ‘genl_ctrl_alloc_cache’ from incompatible pointer type
/usr/include/netlink/genl/ctrl.h:25:14: note: expected ‘struct nl_sock *’ but argument is of type ‘struct nl_handle *’
../src/drivers/driver_nl80211.c:1310:2: error: too few arguments to function ‘genl_ctrl_alloc_cache’
/usr/include/netlink/genl/ctrl.h:25:14: note: declared here
../src/drivers/driver_nl80211.c:1327:3: warning: passing argument 1 of ‘nl_socket_add_membership’ from incompatible pointer type
/usr/include/netlink/socket.h:30:13: note: expected ‘struct nl_sock *’ but argument is of type ‘struct nl_handle *’
../src/drivers/driver_nl80211.c:1337:3: warning: passing argument 1 of ‘nl_socket_add_membership’ from incompatible pointer type
/usr/include/netlink/socket.h:30:13: note: expected ‘struct nl_sock *’ but argument is of type ‘struct nl_handle *’
../src/drivers/driver_nl80211.c:1345:2: warning: passing argument 1 of ‘nl_socket_get_fd’ from incompatible pointer type
/usr/include/netlink/socket.h:57:13: note: expected ‘struct nl_sock *’ but argument is of type ‘struct nl_handle *’
../src/drivers/driver_nl80211.c:1355:2: warning: implicit declaration of function ‘nl_handle_destroy’
../src/drivers/driver_nl80211.c: In function ‘wpa_driver_nl80211_init’:
../src/drivers/driver_nl80211.c:1425:2: warning: passing argument 1 of ‘nl_socket_get_fd’ from incompatible pointer type
/usr/include/netlink/socket.h:57:13: note: expected ‘struct nl_sock *’ but argument is of type ‘struct nl_handle *’
../src/drivers/driver_nl80211.c: In function ‘wpa_driver_nl80211_deinit’:
../src/drivers/driver_nl80211.c:1599:2: warning: passing argument 1 of ‘nl_socket_get_fd’ from incompatible pointer type
/usr/include/netlink/socket.h:57:13: note: expected ‘struct nl_sock *’ but argument is of type ‘struct nl_handle *’
make: *** [../src/drivers/driver_nl80211.o] Error 1
==

So at this point I can't even compile hostapd. I could go back to libnl.dev (and have indeed tried), but I still get the initial "nl80211 not found" error libnl1.

Any help is greatly appreciated.

R.
==

---

### Post by wildmanne39 on 2011-10-05
Hi, here is a link that should help.
[http://exain.wordpress.com/2011/03/31/making-a-wifi-hotspot-access-point-using-linux-wifi-lan-cardusb-adapter/](http://exain.wordpress.com/2011/03/31/making-a-wifi-hotspot-access-point-using-linux-wifi-lan-cardusb-adapter/)
Thank you

---

### Post by hrickh on 2011-10-08
> **wildmanne39 said:**
> Hi, here is a link that should help.
[http://exain.wordpress.com/2011/03/31/making-a-wifi-hotspot-access-point-using-linux-wifi-lan-cardusb-adapter/](http://exain.wordpress.com/2011/03/31/making-a-wifi-hotspot-access-point-using-linux-wifi-lan-cardusb-adapter/)
Thank you
I had found this link when I was originally setting up my 10.04 install with an ath5k card, and it worked beautifully. In fact, I think I even posted a link to it in a previous post regarding setting up the ath5k card.

Doesn't work with the bcm4313 card, though.

R.
==

---

### Post by wildmanne39 on 2011-10-08
Hi, here is one more link that might help, I am sorry that is all the help I can be on this issue, I have never tried to setup a laptop as an AP.
Thank you

---

