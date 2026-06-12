---
title: "Wireless question"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by macrohard on 2009-05-29
I was seeing if there would be a way to do the following.

I would like to set up an additional wireless network in my house, and setup my son's Ubu desktop's with wireless cards to connect.

This wireless network in turn would sit on the LAN behind an Untangle UTM, so I would have control of web content they would go to.

Is there a way that I could lock down in Ubuntu on the wireless connection that they could when they sign onto the internet they only go through the designated wireless in my house, and not be able to access anywhere else on a different wireless access point say in the neighborhood?

The wireless of course would be WPA2, no SSID broadcast and have MAC address filtering enabled.

Thanks

---

### Post by t0mppa on 2009-05-30
If your son doesn't know the sudo password, then it's fairly simple, since you can just setup the connection manually and remove any GUI's that enable connecting to other networks.

If you have a tech savvy kid with superuser access though, then things get complicated. There are a few other threads on the forum discussing these problems, but after browsing a few of those out of curiousity, I'd say your effort to block him out of non-wanted sites increases pretty close in proportion to the square of his tech savviness. Well, that sounded awfully grandiloquent, but point being it gets nasty and quick. :)

---

