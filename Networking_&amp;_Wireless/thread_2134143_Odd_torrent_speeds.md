---
title: "Odd torrent speeds"
date: 2013-04-10
forum: Networking &amp; Wireless
---

### Post by ohzopants on 2013-04-10
I'm running deluge as a daemon on my Ubuntu (12.04) HTPC/server that I access through the WebUI on my laptop. This setup has worked fairly well for a couple of years now, but has seen decreasing amounts of use since my discovery of usenet.

I've set Deluge to use a manual range of ports (15000-16000) and these ports are forwarded (TCP and UDP) to the static IP of my server in my router's settings.

I'm running the latest version of deluge that is available in the official repositories.

Yesterday I noticed that my download speeds were atrocious (like 15-45 kB/s) so I fiddled with some settings, to no effect. I then fired up the Transmission bittorrent client and it started downloading the same torrent at 2-3 mB/s. I use the Ubuntu ISO torrent as my "speed test" torrent, so it's not a seed/peer problem.

The global and per torrent settings are identical in both setups (upload speed, number of connections, etc.).

Why is Transmission getting way better speeds than Deluge?

Does the uPnP option in Deluge negate the manual port selection?

---

