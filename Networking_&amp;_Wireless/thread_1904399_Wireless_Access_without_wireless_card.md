---
title: "Wireless Access without wireless card"
date: 2012-01-04
forum: Networking &amp; Wireless
---

### Post by javaben on 2012-01-04
First, I'm not affiliated in any way with TrendNet, whose product I'll be discussing.

I recently took an old PC and put it in our den, with the idea I would use it with Ubuntu and Google Chrome to stream radio (see chrome extensions for 'radio live' for one that works well).  However, the location I put it in wasn't wired, and none of the wireless cards I already had worked with Ubuntu.

I didn't want to buy another wireless card, but instead wanted to use the PC's built-in LAN connection.  This way, I could avoid driver issues all together!  This would also give me a different device for other projects that were in need of hard-wired LAN connections, so it would be a useful device to have around beyond the streaming radio implementation.

Searching around, I found a 'wireless adapter' which was advertised as being used for gaming systems.  I thought this might work well, as I couldn't see any difference between one device's TCP LAN connection and another's, so I bought a TrendNet TEW-647 GA wireless adapter device.

I plugged the device into the electrical supply, then plugged in a LAN wire from the PC's LAN socket and then into the TEW-647 GA adapter, and I was up and running!

So, if you are having wireless LAN connection problems (or driver issues), or need to provide a wired LAN connection in a wireless environment, this might be a solution for you.

JavaBen
Alpharetta, GA

"Retirement - when every day is Saturday, and every night is Friday night, and the only thing you have to do is the dishes."

---

### Post by josephmills on 2012-01-04
have you tried [Alpha wireless](http://www.google.com/products/catalog?q=network+card&um=1&ie=UTF-8&tbm=shop&cid=4220336969504803872&sa=X&ei=gNoET7jFOaPx0gGtstymAg&ved=0CMkBEOUNMAI) 
works out of the box well for me at least

---

### Post by javaben on 2012-01-04
> **josephmills said:**
> have you tried [Alpha wireless](http://www.google.com/products/catalog?q=network+card&um=1&ie=UTF-8&tbm=shop&cid=4220336969504803872&sa=X&ei=gNoET7jFOaPx0gGtstymAg&ved=0CMkBEOUNMAI) 
works out of the box well for me at least

No, I didn't, since it didn't apply to my situation.  As noted in my post, I  wanted to be able to direct plug the board's LAN connection.  The device you mentioned is a USB connected device, not a TCP connected device.  Also, a very important aspect of the device I mentioned is that it doesn't require any device drivers of any sort - a USB device would require device drivers.  This device is not observable to Ubuntu - it's just a device upstream that is providing Ubuntu with a LAN connection, but it's actually providing a wireless lan connection to a motherboard that has a wired lan connection.  

Hope that's clear, and thanks for your info!

---

