---
title: "General, practical 802.1X question"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by decoherence on 2011-10-20
Nothing Ubuntu-specific here.... just wondering if anyone has done anything like the following:

You have a network drop that has a point to point wireless shot to a switch port which is configured to do 802.1X. The fact that it's wireless shouldn't really matter -- the point is there's **something** between the network drop and the switch.

Here's the thing: getting the switch to allow access shouldn't be a problem but how do you tell it when the authenticated session is over? If the network drop went directly to the switch, simply unplugging the supplicant would be sufficient. When the link state changes to 'down' the port returns to its unauthorized state (at least with a Catalyst switch.) The monkey wrench here is that since the supplicant isn't directly plugged in to the switch, that link will never go down from the switch's perspective.

I should mention here that I only have about a day's worth of experience working with 802.1x so it could very well be that I'm missing something obvious. I've got a switch configured to authenticate to a RADIUS server and bring the port up for me when a supplicant provides the right credentials but that's about it. Surely what I'm suggesting isn't too uncommon? Are there access controllers that take care of this? (we have a bunch of 4IPnet stuff and we're getting in a bunch of Ruckus stuff but I haven't played with any of it yet.) And if so, what method do they use?

Thoughts, anyone?

thanks,

---

