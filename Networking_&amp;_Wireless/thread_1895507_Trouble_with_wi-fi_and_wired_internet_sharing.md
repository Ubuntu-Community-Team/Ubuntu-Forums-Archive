---
title: "Trouble with wi-fi and wired internet sharing"
date: 2011-12-14
forum: Networking &amp; Wireless
---

### Post by misternuvistor on 2011-12-14
Hello everyone,

I currently have Ubuntu 11.10 running on a  Gateway E4000 mini-PC, installed with 2 wi-fi adapters (a Realtek-based  Belkin USB adapter, and a Ralink-based Linksys PCI internal adapter), as  well as the on-board wired Ethernet adapter (Intel-based).  The main  internet connection for this PC comes in via wi-fi the Belkin adapter  (it's a wi-fi connection I'm using with full consent from the owner of a  business downstairs from me), but what I'd like to do is to share it to  the internal Linksys wi-fi adapter so I can use the PC as a wi-fi  repeater in my area using a separate SSID with encryption (the original signal is a bit weak, the Belkin seems  to be the most sensitive at picking it up), as well as having the  internet connection, as received by the Belkin adapter, shared over the  wired ethernet adapter as well.

I tried to set up all the  adapters accordingly (the Belkin set to "Automatic (DHCP)", the Linksys  set up as a hotspot and set to "Shared with other computers", and the  wired adapter set to "Shared with other computers" as well, but it  didn't work.  Instead, I kept getting the connection indicator  that  normally comes up in the upper right-hand corner of the desktop below  the top status bar, showing a connection name of "(none)", which kept  alternating with:

"(none)
Connection Established" and

"(none)
Disconnected".

It  would keep doing this in an endless loop after I set everything up as previously mentioned.  I then tried disabling and re-enabling the  Linksys card as a hotspot, where the connection indicator then came up  with "(ryan-e-4000) - Connection Established" (ryan-e-4000 being the  system name that Ubuntu assigned to the Linksys adapter as a default  SSID), but then that disconnects too, and the same endless loop of the  "(none)" connection keeps going on in a loop until I go and delete all  the network devices from the System Setting menu and re-load them.

Am  I doing something wrong or overlooking a crucial step in setting all of  this up?  if someone here more knowledgeable could lend me a hand in  getting all of this working together properly, I'd be most indebted.

Thanks,
Ryan (misternuvistor)

---

