---
title: "hardy 8.04 LTS Server and Wireless"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by reica on 2009-09-24
This maybe of help to someone setting up the server with a wireless connection.
After setting up the server on an old Dell I8200 with a Netgear PCMCIA card, I found that I could not setup the wireless interface.
After searching high and low it dawned on me that the default kernel of the server did not have RADIO configured.
After changing to boot with the 'generic' kernel, everything fell into place and the wireless interface could be configured.
This may save someone else some time :)
Reica

---

