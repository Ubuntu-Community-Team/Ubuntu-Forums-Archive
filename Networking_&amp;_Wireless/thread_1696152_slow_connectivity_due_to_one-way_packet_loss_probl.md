---
title: "slow connectivity due to one-way packet loss problem"
date: 2011-02-27
forum: Networking &amp; Wireless
---

### Post by robertbub on 2011-02-27
I discovered a very strange problem I'm having.

It always feels like, when typing into my ssh session, I was typing into a [COLOR="SeaGreen"]teletype[/COLOR] (ok, so I'm old skool) -- I'd type a letter and sometimes it would hesitate briefly.  I thought it was my keyboard, but recently thought it might be my [COLOR="SeaGreen"]network[/COLOR].

Sure enough, that's what it seems to be.

Here is the odd symptom mixture:[LIST=1]
[*]Pinging *to* my wireless laptop from my desktop machine gets between a 3% and 5% [COLOR="DarkOrange"]packet loss[/COLOR].
[*]Pinging *from* my wireless laptop to my desktop gets 0% packet loss and each ping is quite fast (~3ms).
[*]Pinging to another wireless device (a Nokia tablet and a Windows 7 laptop) from my desktop never drops any packets; in fact, pinging to everything else other than the wireless laptop never loses packets.
[/LIST]

And, of course, my wireless laptop is running [COLOR="DarkOrchid"]Ubuntu Lucid[/COLOR].

I can't understand why it would drop packets in one direction and not the other, and why it would be so much faster in one direction and not the other.  Perhaps a driver problem?

I guess this problem is mostly [COLOR="DarkSlateGray"]annoying[/COLOR] but is also quite puzzling.

---

