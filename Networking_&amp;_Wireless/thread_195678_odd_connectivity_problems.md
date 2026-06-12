---
title: "odd connectivity problems"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by Nikusan on 2006-06-13
Hi all!
I'll try to keep this as brief as possible, but you need some backstory to help me sort this one out. Thanks in advance to anyone who reads all this!

I've recently installed dapper on a friends machine and she's quite happy with it! She connects to the internet through her dad's machine (XP SP2, Internet Connection Sharing) which is connected to an ISDN modem. Her machine connects directly through her dad's, no proxy, with a cross-over cable.

When I first set all this up I completely disabled the XP firewall for the local ethernet and left it active on the modem connection. I don't remember exactly but I think I had to do this for some reason.

Recently she has had some weird connectivity problems. She is able to connect to google talk with gaim and talk to me on jabber. She can open google.com and gmail.com in firefox, but not a single other site. She cannot connect to msn in gaim.

I've instructed her to ping a few websites in the terminal and every domain name we try resolves to an IP and pings fine! We just can't make it work in a browser. apt-get also won't connect, however packages.ubuntu.com resolves correctly.

I'm at a loss as to what to try next. My suspicion is that the firewall settings on the XP machine have been tinkered with. I think that because I disabled the firewall entirely on the local network windows decided to put a shield icon in the tray and bug the user about a disabled firewall, so in my opinion it is likely that this is what has happened. Nobody on their end seems to agree though.

From what I can gather all her IP/gateway/subnet mask/dns details are correct. Her proxy settings are set to direct connection.

Any ideas?

---

### Post by Nikusan on 2006-06-13
I forgot to add that I have also got her to boot into a live cd, set up the networking settings to match what is already there and see what happens. The live CD behaves exactly the same apparently. This just fuels my opinion that the problem lies somewhere other than her machine.

On the off chance that I'm wrong however, if anyone has anything else to try let me hear it! I'll love you forever! :D

---

### Post by georgeous on 2006-06-13
Hi,

I'm a linux newbie, just installed dapper and having a similar problem.

My network adaptor is a broadcom 440x, and although it configures fine, and i can ping the router, websites like google and msn, and 'host www.website.com' resolves an IP straight away.

However no GUI program seems to have web access, firefox just sits there 'loading' indefinately, and synaptic, etc attempt to download software lists but never finish...

Your post has given me an idea though, so i'm off to check firewall settings on the router...

---

### Post by Nikusan on 2006-06-13
Let me know if you get it working :p

---

### Post by matjaz_pirnovar on 2006-06-14
Hi,

I had similar problems. But also with Win XP and later on on Ubuntu 6.06.

I could enter any web site except particular link.

The problem was in my internet service provider (NTL in UK) where on its server some routes went corrupt. So after I called them, they provided me with new proxy addresses which I had to enter manually into browser's (Firefox) proxy settings. And it worked.

They said that sometimes some addresses go corrupt !!!???

I tried everything, from switching of firewall, checking for viruses etc. Similar as you describe above.

Hope this can help.

M

---

### Post by mips on 2006-06-14
Try disabling IPv6 in the browser or globally in the system.

---

### Post by Nikusan on 2006-06-14
matjaz_pirnovar, mips: Thanks for your replies!

matjaz_pirnovar: I'm pretty sure that's not the problem because only one machine is experiencing what I described.

mips: That could very likely be the problem! The [wiki page here]("https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4") Is what I'm going to pass on.

georgeous: Check out the wiki article as well, it might help.

---

### Post by matjaz_pirnovar on 2006-06-15
Hi Daniel,

Ok. I hope your search is successful.

Just regarding connectivity problems I had.

It was specific only for my home laptop. I could reach the link from work or any other computer. Also different browsers or operating systems didn't make a difference (either on Win or linux connection problem was still there...)...until I entered new IP addresses manually in proxy...

But again...it might be different in your case  :) 

Good luck.

M

---

