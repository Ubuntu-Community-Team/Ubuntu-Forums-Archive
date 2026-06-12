---
title: "Connecting to WPA2 Enterprise 8.04"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by polarbear10 on 2009-01-26
Playing around with various bits and pieces can drive a person insane or it could be fun!

I'm a bit more on the insane side.  I decided it would be fun to install a radius server at work to protect our WAPS, so I did it at home first.  I cheated a litte, I used a mac os x server with Leopard RADIUS (which is just freeradius tweaked a little).  The server has an Open Directory on it and I wanted to authenticate my wireless users to it.  I changed a couple of settings so I could use it with standard routers.  Now both a WRT54 and D-link DIR-655 are tied to it with a shared secret set to WPA2 Enterprise and are set to authenticate users to the directory on the server.  The laptop I'm using is an old dell i2500 with a pc wireless card in it (running it with NDIS and tmimo3p driver).  I could connect an xp laptop and a osx laptop fine, but for the life of me I couldn't get the ubuntu 8.04 on...  I won't run through the entire list of things I tried but I will point out that no matter what I tried with the SSID's hidden, I could not connect.  I don't know why I thought of it but I'm glad I did, but I just enabled the SSID's on both AP's and now I can connect, authenticate and surf on either access point!

BTW I used the nm-applet exclusively to do the connection - no cl.  The thing that got me hung up was that when I swapped to configuring the connections manually with the network manager - I could connect to the AP's if they were set to no security - even with hidden SSID's - so I never thought to turn them on.

If anyone gets stuck like I did, hopefully enabling the SSID will help.  My preference would be to keep them hidden but with the RADIUS now sitting in the mix I feel pretty good about it.  Too bad 8.10 won't run on this clunker, I'd love to see if the hidden SSID bit is functioning there.

---

### Post by pytheas22 on 2009-01-26
If you're not content to leave well-enough alone, you could try using [wicd]("http://wicd.sourceforge.net") instead of Network Manager to manage the connection in Ubuntu.  It might have better luck dealing with the hidden SSID (which of course doesn't really protect your network from anyone who wants to find it, you know...).

---

### Post by polarbear10 on 2009-01-27
Hi Pytheas22,

You're right, for me it's just that one extra step - there are plenty of visible AP's in the area and hopefully a hacker would start with those.  I guess for the select few, the more difficult you make it the more attractive the target.

For the moment I'm enjoying seeing the signal strength bars so I'm going to pass on wicd (for now at least).  Can't say I'm not curious tho ;)

---

