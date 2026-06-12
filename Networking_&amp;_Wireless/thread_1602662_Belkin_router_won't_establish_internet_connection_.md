---
title: "Belkin router won't establish internet connection from modem"
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by themusicalduck on 2010-10-21
I have a Belkin F5D7231-4 router connected to a Scientific-Atlanta modem with an ethernet cable. For a little while, the modem stopped working and I couldn't get an internet connection. I plugged my netbook directly into the modem with the ethernet cable and it couldn't even resolve an address.

After fiddling with the cables and restarting the modem a few times, I could connect to the internet again, directly through the ethernet cable.

Now that I've plugged the modem back into the router, the router can't find the internet connection. The globe icon on the front of the modem just blinks and the configuration page says that there is no internet connection, no IP address, DNS address gateway or subnet mask.

Strangely, when the modem wasn't working, it said that there was a connection. Now that it is working, it claims that there isn't a connection. I can still connect to the modem through ethernet though and get internet. I've restarted the router a few times but have had no luck.

If I try to ping the modem through the router, I get no response, but I can open the configuration page of the modem when connected by ethernet. If I log onto the configuration for the modem and look at the logs, this is the only thing that seems to stand out:

DHCP WARNING - Non-critical field invalid in response

It doesn't give a date or time though, so I'm not sure if it is recent. Also, according to Google that isn't something to worry about anyway.

---

