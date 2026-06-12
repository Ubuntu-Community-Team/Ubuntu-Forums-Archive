---
title: "LTSP - problems"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by BWGuy on 2009-07-04
Ok, Ubuntu LTSP is supposed to work out the box, that just didnt happen

So I have DHCP working, LTSP installed but still my client doesnt take any IP offers
any ideas?:)
BWGuy

---

### Post by smaclean on 2009-09-08
When you restart DHCP server, did you run sudo ltsp-update-sshkeys and then sudo ltsp-update-image? Any time the IP of the server changes, you need to update the sshkeys and the image, in that order.

---

