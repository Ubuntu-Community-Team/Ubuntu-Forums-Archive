---
title: "Do I need to be logged in for a static IP to work?"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by Roasted on 2010-12-28
I was at the login screen on my desktop and I tried to hit my samba share from my Ubuntu laptop. Couldn't find it.

I logged in, went back to my laptop, oh hey it worked.

I have a static IP assigned to my desktop. Is there any reason why this backfired? I'm just trying to find the proper answer for this. Thanks!

---

### Post by PatchesTheCaveman on 2010-12-29
If it's a wired connection it should work when you're logged out automagically.

If it's wireless, you'll need to right-click on the Network icon on your top panel, click *Edit Connections...*, click on the *Wireless* tab, click the network you're using, click Edit, and check the *Available to all users* check box at the bottom left of the Edit window.  Click *Apply* and it should now work when you're logged out or someone else is logged in.

If it is in fact wired, make sure the *Available to all users* box is checked on the wired connection.  But that's usually the default.

---

