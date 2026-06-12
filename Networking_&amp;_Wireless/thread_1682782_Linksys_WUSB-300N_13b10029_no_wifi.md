---
title: "Linksys WUSB-300N 13b1:0029 no wifi"
date: 2011-02-06
forum: Networking &amp; Wireless
---

### Post by Zalokin on 2011-02-06
Hi,

My USB WIFI device is Linksys WUSB 300-N.
I use Ubuntu 10.10 amd64.

I  installed relevant ndiswrapper including ndigtk sucessfully.

I installed netmw245 driver under Wireless Network Drivers sucessfully.
It states "Hardware present:yes"

However no connection is present.

More specifically no option regarding WIFI comes up when clicking the top right Wireless icon on the screen.
However "Enable Networking" is ticked.

When I type in the terminal:

#iwconfig it shows -

lo - no wireless extensions
eth0 - no wireless extensions

Would be grateful if someone can help me.

Thanks.

Zalokin

---

### Post by pottzie on 2011-02-18
I actually found this thread via a Google search for this driver (I'm trying to get it working in Mint/Debian.)
 According to Source Forge, this driver only works with a 32-bit system. Poster says he's using 64 bit Ubuntu.
 Sorry. Bummer, I know. I think that when the 26.37 kernel is released, it will include many N type receivers. Hopefully around (or before!) March. I hope, I hope, I hope.

---

