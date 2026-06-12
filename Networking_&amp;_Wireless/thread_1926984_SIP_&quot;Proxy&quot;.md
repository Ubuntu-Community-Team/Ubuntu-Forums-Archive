---
title: "SIP &quot;Proxy&quot;"
date: 2012-02-17
forum: Networking &amp; Wireless
---

### Post by Shihan74 on 2012-02-17
Hi folks,

Been a while since I really touched voip in any real big way and all I really want is a bit of software I can run on my router that'll do something simple;

1) connect to my voip provider
2) terminate all calls on the router itself, then forward them thru to the voip provider.
3) any incoming calls ring all connected sip phones on the internal network
4) voice mail for incoming calls would be nice too (happy to drop this bit).

Currently I do do this with asterisk, but I want to get rid of it. I find I play with it too infrequently these days to remember the configuration all that well and its kinda like a ten-ton hammer for such a small task. I've played with a few bits of software trying to do this (like siproxd, openser, opensips), but really havent had any luck with it. Any suggestions what other bits of software out there might do this?

---

### Post by jonobr on 2012-02-17
I have used [Kamailio]("http://www.kamailio.org/w/") for this and for my lab testing.

One thing to watch for though is that kamailio is a proxy and asterisk is a sip server.

The difference between the two is that kamailio and other proxies set up calls between endpoints allowing them to negotiate their codecs whereas  asterisk stays in the middle of all sessions.

The big reason I mention that is that if your client is using eg a G729 codec and the other endpoint has a G711,
using Kamailio the call will never work due to the codec mismatch.

However, with asterisk, it trans codes, converting from G729 to G711 and vice versa, something Kamailio doesn't do.

---

### Post by Shihan74 on 2012-02-19
Kamailio and opensips i spent about a couple of days trying to understand and got absolutely nowhere. Im still not certain I even really understand what each of them is really trying to achieve exactly.

From what I can tell they are simply register and proxy servers. What I got stuck on though was how you would have severals phones internally talk to each other, but make outgoing calls to an upstream authenticated voip provider, and I couldn't find any suggestions on how that was possible and I began to believe it wasnt. I didnt even bother really looking how inbound calls might work after that (i just want every phone to ring).

In asterisk, it is quite achievable cause the voip provider just sees asterisk which deals with the auth/channels between itself, the voip provider and the phone making/receiving the call.

---

