---
title: "Connecting to an Epson SX235W Wireless Printer"
date: 2012-05-01
forum: Networking &amp; Wireless
---

### Post by thomastt37 on 2012-05-01
Hi Can anyone help here I have a small ALL In One Epson SX235W wireless printer which I would like to be able to connect wirelesly on my Ubuntu 11.04 and 11.10 32 and 64 bit Desktop pcs.Unfortunately Epson do not support this printer in Linux other than supplying a Linux Driver.They only support Windows Systems,and its very simple setting up the system with all the drivers etc and a cd rom.Finally I don't have a problem using a USB connection with Ubuntu as the Operating system loads a driver automatically its just setting up the wireless connection! Has anyone succeeded doing this ?  Any help appreiated..Michael:(

---

### Post by pbhj on 2012-07-02
It's maybe too late for you but I've [installed my SX535W]("http://alicious.com/epson-install-kubuntu/") without too much trouble - there was a little gotcha on IP address though.

If your router has picked up the printer then it will appear on your router information screens so point your browser to the router admin pages and have a look to see if it's being picked up.

If the router can see the printer then you can go to the assigned address and there's a config page with details for thinks like ink levels and firmware version.

At this stage the network should all be working and you can install via CUPS (which for me had discovered the printer) making sure you've installed the printer drivers appropriate for your model.

HTH

---

