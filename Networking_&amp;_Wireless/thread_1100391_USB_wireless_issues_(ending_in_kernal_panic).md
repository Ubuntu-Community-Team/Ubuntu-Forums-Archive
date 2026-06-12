---
title: "USB wireless issues (ending in kernal panic)"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by David Battley on 2009-03-19
I hope that someone is able to help me - I was uncertain whether this belonged in "Absolute Beginner Talk" but on the basis of my lack of knowledge about Linux it would be helpful if any solutions are given in beginners language if possible...

I have been using Ubuntu 8.04 (386) as a dual-boot system, maintained and updated to the latest version as at the beginning of this month and it has worked flawlessly, UNTIL...

I have a wireless connection via a USB dongle which worked until I foolishly disconnected it live (I pulled the wrong wire out of the back :)) and now it will not recognise the wireless adaptor at all.

On the advice of my more experienced friend I disconnected the stick, deleted the /etc/udev/rules.d/70-persistent-net.rules, and rebooted and sure enough this replaces itself without the reference to the USB dongle. The theory was that reconnecting the USB stick would then "reinitialise" the connection. There is a load of gumpf in the system log when I do which ultimately suggests that it has failed to initialise correctly.

Having done this, if I simply reboot with the USB stick in I get a kernal panic, but taking the stick out loads correctly, apart from no internet connection (though it still works in Windows).

I would be happy to post eg the system log or any other outputs here as advised but as you can probably appreciate this is tricky and very time consuming given the need to reboot twice everytime to get back to the internet...

Any help/advice gratefully received!

Kind regards,

David

---

### Post by David Battley on 2009-03-19
No ideas?  Any suggestions would be much appreciated

Kind regards,

David

---

