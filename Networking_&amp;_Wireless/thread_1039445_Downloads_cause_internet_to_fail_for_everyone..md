---
title: "Downloads cause internet to fail for everyone."
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by sgtcodfish on 2009-01-14
Hi,

I installed Ubuntu 8.10 today, although I have used Linux a little before.

I've noticed that when I download things (files from the internet and Ubuntu updates are what I've seen to cause the problem so far, haven't tested anything else) my normal HTTP traffic coming through port 80 fails and I can't access the Internet until the download is complete. The rest of the computers on my network at home (all Windows XP machines) also have to wait for my download to finish.

Other uses of the Internet, however, seem fine. I can still chat on Pidgin while downloading, and I believe the windows users can still use Windows Live Messenger.

I suspect this is a problem with Ubuntu hogging all HTTP bandwidth (assuming updates come through port 80) - anyone know how to sort this out?

I have a Netgear DG834G router, everyone connected wirelessly.

Thanks in advance,

Ash

---

### Post by ASchweitzer on 2009-01-14
Does the router have QoS settings? It sounds to me like you've got something set in there. And as far as I know, updates DO run on 80.

---

### Post by sgtcodfish on 2009-01-14
A look in the router settings doesn't seem to show anything for QoS. I was at first inclined to think this was a config issue with Ubuntu, since I can download quite happily from HTTP on Windows XP without ruining everyone else's connection.

If updates do run on 80, then that'd pretty much pinpoint the problem.

---

### Post by ASchweitzer on 2009-01-14
From a quick google search it appears this thing has built-in QoS that is non-configurable, but set up for voice. Maybe that's the cause. Sorry, but I can't help any further really.

---

