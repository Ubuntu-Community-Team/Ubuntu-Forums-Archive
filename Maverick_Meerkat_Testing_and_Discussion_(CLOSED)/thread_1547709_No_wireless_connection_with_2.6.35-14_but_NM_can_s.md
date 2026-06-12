---
title: "No wireless connection with 2.6.35-14 but NM can see my modem."
date: 2010-08-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by k3lt01 on 2010-08-07
I have finally got back into testing after a bit of a hiatus. I did a clean install of Lucid (Karmic actually which I updated to Lucid) and then updated to Maverick. The wireless was working in Karmic and Lucid absolutely perfectly after I installed ndiswrapper etc but as soon as I updated to Maverick and got the new 2.6.35-14 kernel my wireless will not connect, and this is even though NM can see there is a connection there.

I'll work on it a bit tonight and if I can't fix it I'll look for a bug report tomorrow. I see [this thread]("http://ubuntuforums.org/showthread.php?t=1502738&highlight=wireless") has a very similar, if not identical issue but it was back in June. Is there something with the new kernels that can be easily fixed with a work around?

Fyi I have re-installed the kernel, ndiswrapper etc, and the wireless driver with no change at all.

---

### Post by alexfish on 2010-08-08
hi

I think you may have to elaborate is a  wireless connection or a modem connection

wireless card or pci info
if modem is IE broadband etc or DSL

---

### Post by scradock on 2010-08-08
One thing to check - the wireless network properties. I occasionally find that the security setting has changed from "Shared Key" to "Open", which means that the connection fails. Simply setting it back to "Shared Key" seems to do the trick....

---

### Post by k3lt01 on 2010-08-08
> **alexfish said:**
> hi

I think you may have to elaborate is a  wireless connection or a modem connection

wireless card or pci info
if modem is IE broadband etc or DSLI don't think any elaboration is required at all, wireless means wireless.

> **scradock said:**
> One thing to check - the wireless network properties. I occasionally find that the security setting has changed from "Shared Key" to "Open", which means that the connection fails. Simply setting it back to "Shared Key" seems to do the trick....Thanks, I'll try this tonight when I don't need the laptop to do anything else while I'm popping in and out of the forum. I don't have any security settings anyway as my nearest neighbour is 500 metres away and my old wireless modem wont broadcast that far.

I did find another thread, about 1/2 an hour after starting this one where it seems there is more than me having this issue. After looking at the bug report posted by the other person it is looking like it is a change within the kernel since 2.6.34. 2.6.35 is the first kernel that wont work for some people.

---

