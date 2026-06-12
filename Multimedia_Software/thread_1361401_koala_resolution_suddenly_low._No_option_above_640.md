---
title: "koala: resolution suddenly low. No option above 640x480"
date: 2009-12-22
forum: Multimedia Software
---

### Post by bobdobbs on 2009-12-22
Hi all.

I booted my computer and started ubuntu, only to find that the resolution was very low.

I eventually found the menu to reset it. But, there is no option above 640x480.

I'm using an nvidia card.

How can I fix this ? 

I used envy to uninstall and reinstall the drivers. I've tried both nvidia's proprietry drivers and the community drivers. I still get the same problem: neither nvidia-settings and the ubuntu display settings offer options above 640x480.

---

### Post by bobdobbs on 2009-12-22
Kind of fixed.

I scratched my xorg.conf. Reinstalled nvidia's proprietry drivers using the hardware drivers manager. I reinstalled an old xorg.conf that I had posted on these forums. Then I ran nvidia-xconfig.

After all that, I now have good resolution and compiz working.

I won't mark this thread solved, because the underlying problem still exists: the sudden reversion to low resolution.

---

