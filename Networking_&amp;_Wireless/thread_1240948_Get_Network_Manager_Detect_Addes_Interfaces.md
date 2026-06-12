---
title: "Get Network Manager Detect Addes Interfaces"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by devzero on 2009-08-15
Hi,
I have a Acer Netbook with a HTC Cell Phone with Internet Sharing
via WMWifirouter trough USB.
That works very good but the NetworkManager doesn't dedect
the eth1 Interface which was added after bootup.
How can I tell the NetworkManager, to recornize it so pidgin and 
Firefox works?
If I cant get the NM work, how can I get the Programs to work, even
NetworkManager wont detect the interface?

thanks in advance.

---

### Post by nixscripter on 2009-08-15
The only thing I can suggest is to restart the applet. Something like this on the command line should do it:

```
 kill `pgrep nm-applet` && (nm-applet &)
```

---

