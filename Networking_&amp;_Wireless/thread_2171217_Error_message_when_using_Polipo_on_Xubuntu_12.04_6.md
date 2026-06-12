---
title: "Error message when using Polipo on Xubuntu 12.04 64-bit"
date: 2013-08-29
forum: Networking &amp; Wireless
---

### Post by marinecomm on 2013-08-29
I setup Polipo today and made sure everything was configured to the best of my ability. I set it up where apt-get could access the internet through the proxy as well. When I fired up Synaptic to to update my repositories, I noticed a series of error messages in the terminal window similar to the following:

Couldn't create disk file /var/cache/polipo/extras.ubuntu.com/I3ovcIMHGOSKrHDwTjbWug==: Permission denied

It has denied a lot of requests this way and in Synaptic they are showing as 'Failed' under the 'Status' tab. What do I need to do to correct this? Thank you.

---

### Post by marinecomm on 2013-08-29
Out of curiousity, I wen to polipo's log file and these were the ony two entries:

Couldn't bind: Address already in use
Couldn't establish listening socket: Address already in use

---

