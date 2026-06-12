---
title: "Run script when TV is plugged in; how to detect?"
date: 2009-06-03
forum: Multimedia Software
---

### Post by jonaskoelker on 2009-06-03
Hi all.

I'm using my Ubuntu laptop as a media center with Elisa and wminput (for wiimote control).

I'd like to run a script whenever I plug my TV into my computer (which replaces compiz by metacity, sets up the right resolution, starts up elisa and connects with my wiimote).

How can I detect when this happens?

I'd also like to run a "reverse" script (switch back to compiz, kill the wiimote connection, etc.) whenever I unplug my TV.  How can I detect when my TV is unplugged?

---

### Post by eldragon on 2009-06-03
> **jonaskoelker said:**
> Hi all.

I'm using my Ubuntu laptop as a media center with Elisa and wminput (for wiimote control).

I'd like to run a script whenever I plug my TV into my computer (which replaces compiz by metacity, sets up the right resolution, starts up elisa and connects with my wiimote).

How can I detect when this happens?

I'd also like to run a "reverse" script (switch back to compiz, kill the wiimote connection, etc.) whenever I unplug my TV.  How can I detect when my TV is unplugged?

if its a usb device. i think you could do this with udev rules.

---

### Post by jonaskoelker on 2009-06-03
> if its a usb device. i think you could do this with udev rules.

I plug it in via the VGA plug.  In the future, I might also use the S-video plug.

---

