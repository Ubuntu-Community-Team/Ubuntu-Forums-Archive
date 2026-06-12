---
title: "How can I stop my wifi roaming?"
date: 2010-03-23
forum: Networking &amp; Wireless
---

### Post by ireneshusband on 2010-03-23
How can I stop my wifi roaming when I don't want it to? I connect to the internet through one of a number of hotspots in my area, all with the same name. Frequently, sometimes several times an hour, my machine will spontaneously switch to a much weaker hotspot than the one I normally use. This causes an enormous amount of disruption, with today's disruption really taking the biscuit: I was in the middle of an international VOIP conversation with a potential employer.

I can't remember whether things were better when I was using wicd instead of network manager, but wicd had a huge hit on my system resources (2% or more of CPU), so it's not a great solution. In the KDE interface to Network Manager you can specify which ESSID to connect to, but these settings are ignored. 

Any help with this one very gratefully received because I'm getting pretty frustrated and desperate.

---

### Post by blurpo on 2010-06-12
I'd also be interested in stopping my wireless from roaming.
It's not that I'm in the middle of a conversation with a potential employer, but it's roaming about EVERY 5 SECONDS. I get barely any throughput at all.
After a while - 10, 20 minutes - Network Manager gets tired of itself and it just disconnects completely.
Disabling networking completely (from the Network Manager menu) and re-enabling restarts things, and this gets me roaming again (and connected, at times). This is a sample from my daemon.log:

```

Jun 12 14:17:52 paullaptop2 NetworkManager: <debug> [1276345072.006653] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1B:2F:E6:FE:EA (blurpotres)
Jun 12 14:17:58 paullaptop2 NetworkManager: <debug> [1276345078.007364] periodic_update(): Roamed from BSSID 00:1B:2F:E6:FE:EA (blurpotres) to (none) ((none))
Jun 12 14:18:04 paullaptop2 NetworkManager: <debug> [1276345084.006662] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1B:2F:E6:FE:EA (blurpotres)
Jun 12 14:18:10 paullaptop2 NetworkManager: <debug> [1276345090.003338] periodic_update(): Roamed from BSSID 00:1B:2F:E6:FE:EA (blurpotres) to (none) ((none))
Jun 12 14:18:16 paullaptop2 NetworkManager: <debug> [1276345096.002725] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1B:2F:E6:FE:EA (blurpotres)
Jun 12 14:18:22 paullaptop2 NetworkManager: <debug> [1276345102.002658] periodic_update(): Roamed from BSSID 00:1B:2F:E6:FE:EA (blurpotres) to (none) ((none))

```

I use
[LIST]
[*]Dell Inspiron 1525 with Broadcom 4328 wireless
[*]Proprietary drivers (Broadcom STA...)
[*]Lucid 10.04 64-bit
[/LIST]

I tried the wicd but I can't use it to connect. I think this is because my router insists on "shared key" WEP authentication instead of "open system", and I don't have that option in wicd.
I tried b43-fwcutter but perhaps I should have removed the proprietary driver before or after installing it? I didn't do that and installing b43-fwcutter didn't seem to make a different whatsoever.

Thanks for any help!

---

### Post by blurpo on 2010-06-12
I've found that under System --> Prefs --> Network Connections I should be able to enter the BSSID that I want to stay with. This is ignored though (no change in behaviour). I can also enter the MAC address of the router, but if I do that, Network Manager refuses to connect...

---

### Post by ireneshusband on 2010-06-12
I've switched from networkmanager to wicd and I don't have any problem any more.

---

### Post by dvalfre on 2012-09-29
Maybe a bit late, but for the record you can write down the MAC address of the AP you prefer to connect to and add it on the BSSID field of the network configuration.

Better explanation can be found at [http://askubuntu.com/questions/11990/how-do-i-ban-a-wifi-network-in-network-manager](http://askubuntu.com/questions/11990/how-do-i-ban-a-wifi-network-in-network-manager)

saludos
daniel

---

### Post by Liberator on 2012-10-26
I had the same problem.  As usual, Network Manager is broken.  Network Manager is constantly getting broken and then tenuously repaired, then broken again.  In fact, it's late 2012 and Linux *still* has innumerable networking problems.  (For example, you still can't create a secure ad-hoc wifi network as far as I know due to that being broken in the kernel for years now).

Wicd seems to solve this problem so far on my Linux Mint 9 machine.  Getting away from the oft-broken Network Manager seems to be a prudent idea in any case.

---

### Post by overdrank on 2012-10-26
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

