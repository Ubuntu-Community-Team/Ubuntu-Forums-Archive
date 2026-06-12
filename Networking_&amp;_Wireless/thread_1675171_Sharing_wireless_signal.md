---
title: "Sharing wireless signal?"
date: 2011-01-25
forum: Networking &amp; Wireless
---

### Post by Juhla Mokka on 2011-01-25
Hi, I'd need some advice! This is rather general though? Sorry if I'm in the wrong place.

We cannot get cable internet at home, so have to either get (A) a mobile internet dongle or (B) catch a wireless signal from our neighbour's house if we put our receiver outside (the signal is weak, quite far and many obstacles). We have our neighbour's permission.

If we do (B) with one wifi receiver using maybe a satellite dish to get a better signal, is it possible to then share this connection somehow within our three home computers? Does some hardware do it and what about software?

We're running a dual boot Ubuntu/Vista, a mini laptop with Ubuntu light edition and an old XP. We're in the UK.

We're not sure about option (A) because have heard of intermittent/slow connections and download limits. We'd like to stream occasionally etc. Would have to get one of the mi-fi dongles to share the connection as well. Also it's quite expensive.

Any ideas people? Thanks :)

---

### Post by antmenj on 2011-01-25
Have a look around this site.

[http://martybugs.net/wireless/](http://martybugs.net/wireless/)

Some of it is a bit dated but it should give an idea on what is posable and the conditions under which it can be done.

[img]http://melbourne.wireless.org.au/maps/img/net_map.png[/img]

The above map from  [http://melbourne.wireless.org.au/](http://melbourne.wireless.org.au/)  gives an idea of what distances are posible.

---

### Post by Juhla Mokka on 2011-01-25
Thanks! Good site. I had a look, but I am yet to understand fully how routers/wireless etc work. :-k

Am I right that I can make my PC to act as a **wireless access point** as long as it can access the internet itself via the wireless signal from my neighbour's house? If that's true then all our PCs could use that access point to connect to the internet, nice.

About building an antenna to get a strong signal, would I use a wireless USB adapter that connects to my PC via an USB cable? I have seen pictures where people have just fixed an adapter onto a normal satellite dish to gather the signal. If I don't use an USB adapter, how would I get the signal into my PC?

I quite happy reseraching myself but need to get the basics right first! ;)

---

### Post by Juhla Mokka on 2011-01-25
I have looked around, and have found these: [Thread on setting access point]("http://ubuntuforums.org/showthread.php?t=1553521") and [WifiDocsWirelessAccessPoint]("https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint"). They say that normally the PC that would become an Access Point would have wired connection to the internet - mine doesn't, it connects wirelessly. Is this a problem? Secondly, the Ubuntu Doc says you need a spare PC as it will become a server. Do I have to so that? Can my PC be an Access Point and still use it as a normal PC, as before? :-k

EDIT. I do have a spare wireless router - can I utilise this anyhow? I have no wired connection though - how to get the wireless signal into the router??

---

### Post by grahammechanical on 2011-01-25
I am not an expert. You have an interesting problem. I am looking at the user guide that came with my motherboard which has a built in wireless adapter. At the moment my machine is set up in Infrastructure mode and the wireless Access Point is my modem/router.

In your case your neighbour's wireless modem/router would be the Access Point. If you only wanted one machine to connect to your neighbour's modem, then I would say that it should be set to Infrastructure mode. But as you want other machines to connect to the first,  I would guess that the machine that connects to the wireless Access Point would have to be set in Ad-hoc mode. In this way the other machines can connect to the first one.

Regards.

P.S. Could the spare wireless router be used just as a router? It would not connect to an ISP but could it be used to route the transmissions between the three machines?

---

