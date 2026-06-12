---
title: "Why is deprecated mii-tool still there and ethtool is not?"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by bottomless on 2011-02-03
Installing the latest Ubuntu 10.10 and it ships with mii-tool which is now deprecated (it doesn't even support gigabit Ethernet) and has been replaced by ethtool.

As I can understand that mii-tool may still be there for compatibility, why not shipping ethtool too?

Also the mii-tool manpage could be updated to reflect the deprecated status and point to ethtool (which turns out used to point to it back in a 2000 version of the manpage but not anymore in the 2004 version shipped with 10.10) (inquiry details on this mystery here: [http://blog.bottomlessinc.com/2011/02/using-ethtool-to-determine-ethernet-link-speed-not-mii-tool/](http://blog.bottomlessinc.com/2011/02/using-ethtool-to-determine-ethernet-link-speed-not-mii-tool/))

I see people getting confused using and trusting mii-tool when they shouldn't.

Cheers,
[http://bottomlessinc.com](http://bottomlessinc.com)

---

### Post by irv on 2011-02-04
ethtool is in the Synaptic Package Manager. Also check out the [Ubuntu Manual. ]("http://manpages.ubuntu.com/manpages/hardy/man8/ethtool.8.html")

---

