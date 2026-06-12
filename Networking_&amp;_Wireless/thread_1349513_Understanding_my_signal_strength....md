---
title: "Understanding my signal strength..."
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-12-08
As a relatively new KDE user, I'm having an easy time adapting to the interface but there's one thing I'm not too sure about.

Currently I'm at work, which has a wifi network with WPA2 security. There's about 20 access points that all share the same SSID and such, connected to a console. I know there are dead spots in this building, and I know where the access points are. So I should see a variation in signal strength depending on where I'm at... and I do. Sort of.

If I watch my network manager (where the current in-range wifi networks can be seen) there's two sections.

One with my IP address + Signal Meter
One with my SSID + Signal Meter

So, what's the deal? Even downstairs where there's zero wifi, the SSID + Signal Meter stays pegged at 100%, however the IP address + Signal Meter fluxuates. 

Can anybody kind of relay what's going on here?

EDIT - Right after posting this I checked my signal strength. The signal meter with the IP is 0, while the signal meter with the SSID is 100%, and I still have network connectivity. 

This is confusing, because downstairs where there's zero wifi, I had 100% on the SSID signal meter, yet 0 on the IP signal meter. I figured maybe the IP meter was my true signal, since I expected none downstairs. Yet I have none here - and I can post. Whaat?

---

### Post by Roasted on 2009-12-08
So I went into the Kubuntu IRC chat and somebody was nice enough to help me out there on the spot. They said they had the same problems I did and installed WICD instead.

So I decided - why not? So I fired up WICD and immediately I was in heaven. First of all, the gizmo just works. Secondly, it gave me the MAC addresses of the access points. Not only that, but it listed all available access points in the area. Some of you are probably like, okay, so what?

At work, we have a wifi network with 20 access points. I have to log each MAC address with the cooresponding location of that access point. This is something I was going to be doing later this week. Well, now WICD does the work for me. No lugging a ladder around, removing ceiling tiles, etc. 

But anyway from a functionality standpoint, I really like it. Our 20 access points are on the same console, same SSID, etc. The default KNetworkManager was kind of sloppy with rolling from access point to access point as I moved with my laptop. Don't get me wrong, it did the job, but I had a hard time telling when I dropped 1 AP and gained another, because the signal strength meters... kind of... sucked. With Windows XP when I tested it, I'd lose more and more signal, 2/5 bars, okay 1/5 bars, then BAM 5/5 bars - I knew I hit a new AP then. The KNetworkManager wasn't all there for me with testing this. WICD, however, was not only "all there" but it gave me more information than I bargained for, which is nice for a techie.

So, this begs the obvious question - why isn't it the default network manager for *buntu? Granted if you're on a wired network, who cares, right? But for us wireless folks, this is mighty nice...

---

