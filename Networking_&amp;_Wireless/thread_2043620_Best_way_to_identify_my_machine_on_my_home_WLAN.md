---
title: "Best way to identify my machine on my home WLAN"
date: 2012-08-17
forum: Networking &amp; Wireless
---

### Post by dewdrop_world on 2012-08-17
Hopefully not a difficult question -- but, the last half-hour of Web searching has not turned up a very good answer, so I need to ask.

I want to synchronize my [org-mode]("http://orgmode.org") data to my mobile devices, using a webdav server hosted on my laptop[1]. To do this, I need to provide MobileOrg with a URL to its index file.

What's the best way to identify my computer?

I can imagine these options:

- My computer gets its address from DHCP, and I have to check every time to make sure the address didn't change. Not so much fun.

- Static IP address. I've tried several online tutorials, but all of them result in LAN access only but no connectivity outside. I suspect the DNS is not being located properly. In Network Manager, use "Manual" and:

IP = 192.168.1.200
Netmask = 255.255.255.0
Gateway = 192.168.0.1

- Publish the name of my computer on the LAN, and use the name in the URL. I started looking around at this, but when they talk about setting up your own DNS on the router, I'm out of my depth. (It doesn't help that it's a Chinese router with no English configuration screens.)

Currently I'm doing the first, not quite happy with it. I would be okay with #2, provided it will work with the Internet as a whole. #3 would also be fine, if it isn't too much effort to set up (without being able to read the router's configuration pages).

Thanks in advance --
James


[1] Most people synchronize using Dropbox, but that service is blocked in mainland China, where I live. I also tried Ubuntu One, but it hasn't proven reliable -- either random authentication failures or the connection gets dropped mid-transfer. So synchronizing over my home WLAN is the best for me.

---

### Post by sanderj on 2012-08-17
In other words, a solution would be: the webserver on your laptop should be accessable from Internet using a URL like yoursystem.somedomain.com?

If so, you need to do a few things:
- register a free dyndns name, for example at no-ip.com
- set up a dyndns client, which can be done in your modem or on your laptop. A dyndns client tells the dyndns service its current IP address
- make sure your laptop always get the same IP address via DHCP
- setup port forwarding for port 80 from your modem to your laptop

So ... this is not easy at all. If you have other ways to sync, please consider them.

---

### Post by dewdrop_world on 2012-08-17
> **sanderj said:**
> In other words, a solution would be: the webserver on your laptop should be accessable from Internet using a URL like yoursystem.somedomain.com?

No, that's exactly the kind of complication I want to avoid.

I plan to sync only when I'm at home -- or at least, only when my computer and the mobile things are on the same WiFi router. I most definitely want to avoid involving the whole Internet! (That's why I said "synchronizing **over my home WLAN**.") Currently the url is "http://192.168.1.xxx:80/webdav/index.org" but xxx (currently) can change.

In other words, the desired data flows:

Computer <<---->> Internet

Mobile <<---->> Internet

Computer <<-- WLAN -->> Mobile

I would be 100% satisfied with a static IP on my computer. But, all the instructions I found online left me with local-only connectivity and no ability to reach the network outside. After setting up the static IP, I had Computer <-> Mobile and Mobile <-> Internet, but Computer <-> Internet was broken.

Because of that problem, I thought, maybe there's a better way to accomplish the three data flows that I want, and I just don't know what it's called. So I was asking what the options are. (I agree with you, connecting the computer and the mobile by way of the Internet at large seems rather the opposite of a better way.)

James

---

