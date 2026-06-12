---
title: "rp-pppoe bug found"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by qbox on 2009-03-01
Hi
This is not a question. I write this for someone who have similar problem to find solution.

I used pppoeconf script for connecting to an ISP a long time. Connection to the internet was a nightmare because pppoeconf didn't give an option to set Service name, and my ISP want specific Service name. Only way to get connected fast to ISP was to install rp-pppoe because it support Service name option. I installed the [[COLOR="Blue"]_rp-pppoe-3.10_[/COLOR]]("http://www.roaringpenguin.com/products/pppoe") script and I put it to work. Script work great except the change on old default gateway (on eth0) to a new one (on ppp0). In file /etc/ppp/pppoe.conf i make all settings that was needed. 
DEFAULTROUTE=yes
Have been set to 'yes' but this doesn't work. I try the rp-pppoe on mandriva and I have same results.

[SIZE="3"]**The solution:**[/SIZE]

I open file
sudo gedit /usr/sbin/pppoe-connect
and I find the line
```
# Standard PPP options we always use
PPP_STD_OPTIONS="$PLUGIN_OPTS noipdefault noauth default-asyncmap $DEFAULTROUTE hide-password nodetach $PEERDNS mtu 1492 mru 1492 noaccomp nodeflate nopcomp novj novjccomp user $USER lcp-echo-interval $LCP_INTERVAL lcp-echo-failure $LCP_FAILURE $PPPD_EXTRA"
```

in this line, the author of the script forget to enter the [COLOR="Red"]replacedefaultroute[/COLOR] option

so I cnage the line like this
```
# Standard PPP options we always use
PPP_STD_OPTIONS="$PLUGIN_OPTS noipdefault noauth default-asyncmap [COLOR="Lime"]$DEFAULTROUTE[/COLOR] [COLOR="Red"]replacedefaultroute[/COLOR] hide-password nodetach $PEERDNS mtu 1492 mru 1492 noaccomp nodeflate nopcomp novj novjccomp user $USER lcp-echo-interval $LCP_INTERVAL lcp-echo-failure $LCP_FAILURE $PPPD_EXTRA"
```

After this I reboot the system and script have been loaded from rc.local.
This time everything worked perfect. Default gateway have been changed with new one (ppp0) on the booting time.

Cheers
:guitar:

---

