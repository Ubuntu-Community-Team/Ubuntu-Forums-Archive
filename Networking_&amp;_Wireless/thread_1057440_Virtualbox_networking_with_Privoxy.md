---
title: "Virtualbox networking with Privoxy"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by zoqaeski on 2009-02-01
Hello all

I've got VirtualBox running Windows XP on an 8.10 host. The host machine uses Privoxy (optionally with Tor, but I've currently disabled it), but the guest machine ignores my proxy settings. How can I set up VirtualBox so that it uses my Privoxy settings? I tried using host networking, with bridges and taps, following a number of tutorials which a "Famous Web Search Engine" found for me, but they cause other issues like messing up the networking on the host machine, or disabling the guest from accessing the external network.

On a similar note (this is somewhat dependent on the above networking issues), I'm running Apache server on loopback so it is effectively hidden from the big wide world, but I want to be able to access it from any virtual machines without opening it to broadcast everywhere.

Can anyone suggest how I might achieve this?

---

