---
title: "&quot;Probenojoin&quot; on Kismet has me a little worried..."
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by NCSmokeEater on 2009-01-15
Ok, I'm not sure who all is familiar with Kismet and it's alerts. Here is the alert for probenojoin.

```

Alert name:       PROBENOJOIN
    Alert type:       Trend
    Alert on:         Clients probing for networks, being accepted by that
                      network, and continuing to probe for networks.
    Alert message:    "Suspicious client $sourcemac - probing networks but
                      never joining."
    Tool-specific:    No
    Details:          'Active' or 'Firmware' network scanning tools work by
                      letting the card probe for any network and recording
                      those that respond.  These tools include NetStumbler,
                      PocketStumbler, and many others.
                      Kismet raises this alert when a client is seen to be 
                      probing for networks but never joins any of the networks
                      which respond.
                      False positives are possible in noisy/lossy situations,
                      disabling this alert may be desireable in some 
                      installations.

```

OK, i was doing some "wardriving" from home the other day, giving a shot at my own network. i cracked the wep key in 20 minutes (which pretty much forced me want to change over to WPA2 for security reasons). long story short, my neighbor's network has 128bit encryption so i figured i'd give it a shot for shits and giggles, and then id leave it alone. i just wanted to try out packet inject an all that jazz on another router. i got the key, didnt connect or anything and just left it alone.

then the next day i figured id give WPA a shot (my other neighbors router), so i started doin my thing and i noticed i was getting alerts every 2 seconds (literally). they were coming from one particular MAC address and i figured it wasnt a big deal. then a few minutes later THREE more MAC's came up with the same alert as the first, AGAIN alerting me every 2 to 3 seconds. that made it FOUR MAC's, every 2 seconds, with the same alert for over 30 minutes.

what the heck was going on? should i be a little worried?

---

