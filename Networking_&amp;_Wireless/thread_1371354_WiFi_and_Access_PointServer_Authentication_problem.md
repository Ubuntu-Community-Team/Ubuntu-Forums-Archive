---
title: "WiFi and Access Point/Server Authentication problems"
date: 2010-01-03
forum: Networking &amp; Wireless
---

### Post by beanco on 2010-01-03
Hi Everybody,

Having WiFi problems at work.

I am posting this here... sg I posted in a different forum, on a different site and thought maybe somebody here could help out.

There are 2 of us trying to access the WiFi on Ubuntu but usually with no luck.

Here is the post:

Ladies and Gentlemen,

Who here knows anything about WiFi and network admin and problems?

We all got new laptops and were so happy to be able to get online but the WiFi does not work well. The Sys ops cannot figure out the cause....

And it sucks... many of us cannot get access to the network often. I mean, it is a crap shoot. you either luck out and get access, or do not get it...

Makes surfing Ttips a real bugger in breaks between teaching kids....

Tech info: (Pardon my bad translation of the Hungarian, I know nothing about this tech stuff...)

Given environment:
- WiFi accesspoint with DD-WRT software
- WPA2 Enterprise (RADIUS) authenticsation, TKIP+AES (encoding/secrecy/password,,,, whatever... I have no idea what this is in Eng),
PEAP+MSCHAPv2 (with validation).
- Windows XP SP3 client
- OpenRADIUS server

All participating software is "appropriately configured" (qutaitons sys ops, not mine), that is to say, the system basically works, some users can access it usually, some less often.

(I know the Sys op uses this WiFi system daily, and in teh last two years htere have b een two occasions where he could not access it....)

The error currently is that the authentication does not work, it stops, then times out.

When this happens, the accesspoint does not even reach the RADIUS server... so, the problem is surely to be found in the client-access point communications.... Restarting the access point ( to be more precise the RADIUS client service thereon) usueally resolves the issue.


SO... this really sucks, makes getting work done hard, etc and like I said, I have breaks between lessons and cannot surf ttips... check out weather forecasts and other important things.

Thanks

Robi

---

