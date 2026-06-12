---
title: "opendns - all connections rather than 1 by 1?"
date: 2010-11-13
forum: Networking &amp; Wireless
---

### Post by tomdelonge on 2010-11-13
So I'm going to try out opendns as an internet filter. But I'm not doing it on a network/router, just on my local machine. Using ubuntu, I read that I need to select each connection and change the dns settings.

Is there a way to generically add the dns settings so that if I connect to a new network I don't have to manually update it's settings?

---

### Post by Boondoklife on 2010-11-13
If you are just doing it on your box then the only way I know of would be to set each connection to use it. The reasoning behind this is DHCP will give you all the DNS settings when you logon to the network.

Why not just get a good hosts file that gets rid of most the ads and what not? This would allow you to block sites regardless what network you are on.

---

