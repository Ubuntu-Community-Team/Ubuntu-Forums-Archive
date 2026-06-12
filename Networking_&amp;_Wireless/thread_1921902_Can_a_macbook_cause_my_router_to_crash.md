---
title: "Can a macbook cause my router to crash??"
date: 2012-02-07
forum: Networking &amp; Wireless
---

### Post by Immolatus on 2012-02-07
Ok, here's a fun one. My Lan consists of two desktops and two laptops normally there are no problems at all with connectivity. However, for the last two weekends in a row when my sister is home from college with her Macbook (pro) the wifi router just craps out. It wont even let me log into it on the desktop that is pluged in to it. If I power cycle it, it will work for about twenty minutes and then go down again. I haven't had this problem concerning this Macbook for over a year, so it just stared.

The really interesting thing is if I ping the router (wired connection) I get 100% packet loss.
If I ping [www.google.com](www.google.com) I get about 10% packet  loss. Odd no.

I'm thinking it's just old and cranky (5yrs). I just don't want to go and buy a new one and have the same problem.

Any thoughts???

---

### Post by ratcheer on 2012-02-07
My only thought is that both of my sons have Macbook Pros, and my LAN is fine with them. Sorry I don't have anything else to offer.

Tim

---

### Post by Immolatus on 2012-02-07
Well I'm leaning towards a new one as this one is wifi b/g and all the laptops have b/g/n cards so a speed boost might be nice anyhow.

---

### Post by ratcheer on 2012-02-07
Sounds good.

If you don't mess around with your router much, you might look at the Apple Airport Extreme. It's a little expensive, but I've heard from many places that they're very fast and stable.

Tim

---

### Post by LillyDragon on 2012-02-08
It's been five years since you last bought a new router? Might be time to upgrade if the issue becomes more frequent. Routers crash for a lot of reasons, but your older unit's resources are  probably under a lot more strain now then it was when you bought it.  From what I understand, and please correct me if I'm wrong, as  internet-based applications (Web browsers, IM clients, etc.) become more  complex with each newer version, the programs are a little more  demanding on the router's aging hardware. The Macbook connecting to your  network might have been the straw that broke the camel's back.

Also, setting up it up manually from the web browser helps too, but something tells me you might already know that. I only say this because some setup wizards do a really sloppy job of setting it for you, and will cause the router to crash a lot too. I had that sort of problem with a Netgear router, and it crashed at least three times a day, but it behaved just fine after I set it up manually!

In my experience, an older, wired router worked as advertised for four people browsing the web with Firefox 2, but it flipped out and crashed when even two systems tried running Firefox 3 or 4 simultaneously. Thankfully, the newer, more recent wireless router didn't have any problems with five devices communicating through it at once.

So yes, it could just be "old and cranky". :P

---

### Post by Immolatus on 2012-02-09
I read somewhere that you can do a firmware upgrade on these so I'll look in to that later today. Otherwise it's upgrade time.

---

### Post by Seq on 2012-02-09
> **Immolatus said:**
> I read somewhere that you can do a firmware upgrade on these so I'll look in to that later today. Otherwise it's upgrade time.

You might also try turning off any features the router has (UPNP, Disk/Printer sharing, QoS, etc). Try enabling them one by one and see if any of those start causing issues.

---

### Post by ratcheer on 2012-02-09
My fairly old router (a Netgear WNDR3300) is flashed with **dd-wrt**. It still does everything I need it to do, although it is way short on RAM.

Tim

---

### Post by 1clue on 2012-02-09
There are several things to talk about here.

First, SOHO (small office/small home) routers almost always have some sort of flaky behavior.  I've been trying to figure out how to make an open-source SOHO router test suite for awhile now, but it's not such a simple task.

Second, how old is that MacBook?  More specifically, how old is the OS?  If the router is old and has some of those flaky attributes I was talking about, and the Mac is new, then it's possible IMO that something the MacBook does might disable your router, but if so it's probably something like Bonjour, which is what Apple uses as a discovery mechanism and nobody else really seems to.  If your router has a beta version of that, maybe try to turn it off and see what happens.

Third, How fast is your Internet connection?  Your router and cable modem/dsl modem/whatever might be restricting your throughput.  I have what was advertised to be a pretty fast connection for a few years, but had never seen the type of performance they claimed.  I got a near miss with a lightning strike, and it took out my cable modem.  I went to get another one, and realized that even some of the new ones were slower than my advertised Internet speed.  My old router was 10Mb/Sec, which at the time I bought it seemed huge.  My Internet is supposed to be 50Mb/sec.  I got a new modem that is good for 100Mb/sec and my Internet speed was suddenly amazing during off-peak hours.  So my point is this:  Make sure your equipment is fast enough to deal with your connection or you're paying for something you can't use.

Fourth, you seem to have your modem connected directly to a computer.  This is a security risk.  Yes, chances are there is some sort of firewall software on that computer, but if you get a self-standing appliance then you get defense in depth, which gives you much much more security and for not a lot of cash.

Don't know your financial situation, but IMO a new cable modem and possibly a new router might be a good idea.  If you have wireless and you're not using Wireless N then you should think hard about that too.  If you have old ethernet wire sitting around, that copper can corrode right near the connector or repeated motion can loosen the connection and will start injecting errors which also reduces performance.

One computer CAN definitely saturate a high speed Internet connection, as unlikely as that sounds.  Even if you're not using the full bandwidth you might be suffering from large latencies of old equipment.

Finally, once you get new equipment it's a really good idea to put the newest equipment nearest to the Internet connection.  If your existing equipment is all that old though you might consider just contributing it all to the Salvation Army or something.

---

