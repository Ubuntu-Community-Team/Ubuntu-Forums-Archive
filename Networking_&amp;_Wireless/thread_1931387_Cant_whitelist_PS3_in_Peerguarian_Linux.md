---
title: "Cant whitelist PS3 in Peerguarian Linux"
date: 2012-02-25
forum: Networking &amp; Wireless
---

### Post by Sylos on 2012-02-25
Hello.

So as the title says I cant seen to get PGL to whitelist my ps3 media server. Heres the siuation:

Im using pms 1.50.1 which I believe is the current version.

My router is set to static IP my ps3.

I have set PMS to force using a single port for the service.

I have tried whitelisting both the port and the IP in PGL but have no luck with it. Everytime I start PMS with PGL running it blocks the connection.

Any help greatfully received.

Cheers

---

### Post by jre on 2012-03-30
Check /var/log/pgld.log or use pgl-gui to see what is blocked. This way you should be able to make the correct whitelisting.

---

