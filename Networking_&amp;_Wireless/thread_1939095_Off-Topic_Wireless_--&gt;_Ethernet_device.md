---
title: "Off-Topic: Wireless --&gt; Ethernet device"
date: 2012-03-10
forum: Networking &amp; Wireless
---

### Post by duncan12 on 2012-03-10
This isn't exactly to do with Ubuntu - so apologies if this is in the wrong category, or the wrong forum altogether, but I thought people here might know of a device they can recommend.

I have a **Dynalink RTA1025W** Wireless Modem (it has a repeater mode setup page FWIW, see attached screenshot of web interface). I need to connect it to 3 devices over Ethernet without moving it, however putting a wire through the roof is impossible with my house (have tried).

Is there a device that somebody could recommend which 

[LIST]
[*] Receives a Wireless-G signal, or acts as a D-link repeater
[*] Has 4 Ethernet ports on it which the signal gets given out to
[/LIST]

**So basically what I want is a device that is like a switch but instead of receiving Ethernet and giving out Ethernet it receives WiFi and gives out Ethernet**...

It would also be best if the device is D-link for compatibility.

I need the solution to not be too expensive (maybe NZD$100 / USD$85, remembering things cost more in New Zealand) - so power-line Ethernet + a 4 port switch is probably a little too much. However my network is Wireless-G at the moment anyway, so no need for Wireless-N in the device.


Thanks, and again sorry if this is the wrong place to post,
Duncan

---

### Post by duncan12 on 2012-03-16
bump

If somebody can even tell me what the name of the device I'm looking for is that would be useful. Thanks

---

### Post by kurt18947 on 2012-03-16
No first-hand experience so take this for what it's worth.  I *think* what you want is called a bridge.  I've read about Linksys wrt-54g routers with 3rd party firmware doing what you're talking about.

How about something along these lines?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833127256](http://www.newegg.com/Product/Product.aspx?Item=N82E16833127256)

---

### Post by duncan12 on 2012-03-16
> **kurt18947 said:**
> No first-hand experience so take this for what it's worth.  I *think* what you want is called a bridge.  I've read about Linksys wrt-54g routers with 3rd party firmware doing what you're talking about.

How about something along these lines?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833127256](http://www.newegg.com/Product/Product.aspx?Item=N82E16833127256)

Hi

I would use DD-WRT but it only runs on Routers, not Modem-Routers :mad:

That device you linked to looks perfect, thanks.

However I'm now confused about something else, "Dynalink" and "D-link" seem to be different. [dynalink.com]("http://dynalink.com") has a Dutch "end of life" message, [dlink.com]("http://dlink.com") is a normal website for D-link. [dynalink.co.nz]("http://dynalink.co.nz") redirects to [netcomm.co.nz]("http://netcomm.co.nz"). :confused:

Perhaps the two would be compatible? Or more likely it's time for a new modem... I do have a Linksys WAG120N lying around which is Wireless-N but I dumped it for the old ISP-provided modem because the Linksys has none of the features that the old Dynalink has (dual SSID, no-IP dynamic DNS, IP address reservations, SSH config, etc etc) and the Linksys had terrible WiFi stability when about 10 devices are connected.

However, that wireless bridge says it will work with any router, so the above might not be a problem.

So I think my two options are:

[LIST]
[*]Get the Wireless Bridge you linked to, it works with the existing modem, if I upgrade to a wireless-N router in the future it will work with Wireless-N.
[*](Try to) sell the Dynalink and the Linksys, buy a D-link wireless-N modem-router, buy the bridge you linked to.
[/LIST]

Will look into it further. Thanks :)

---

### Post by duncan12 on 2012-03-23
I brought the TP-Link WR740N. It advertises a "WDS Wireless Bridge" feature. (WDS = Wireless Distribution System - the same protocol the older Dynalink is compatible with.)

So I went onto the wireless setup, clicked "Enable WDS Bridging", and entered the details of my main network, disabled DHCP on the TP-link, and went on the primary Dynalink and ticked the box for the TP-link on the Repeater setup page.

It worked perfectly - no matter which router you were connected to, wired or wireless, you could access the internet and you could access both the routers (192.168.1.1 and 192.168.1.2).

Since it did this I know it can work, however 2 minutes later it wasn't working again - and I haven't got it to work since. I didn't change anything in those 2 minutes. Any idea what I did wrong? :confused:

---

### Post by duncan12 on 2012-03-24
I fixed it! :p

If anybody else is having problems with WDS: change your main SSID to have no spaces (change them to underscores or something). That fixed mine.

---

