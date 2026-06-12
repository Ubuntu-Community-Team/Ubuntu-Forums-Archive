---
title: "Watching Youtube via the TOR network"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by vblurker on 2009-05-02
Is there a way to watch youtube via the TOR network? As some of you might notice, some youtube videos aren't available to certain areas.

I have tried some normal http proxy or the TOR network. No success!

---

### Post by crazy ivan on 2011-03-31
Yeah sure, just add [foxyproxy]("https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard/") to firefox after installing tor

```

sudo apt-get install tor

```

then go to 'Firefox > Tools > Fox Proxy Standard > Options > File > Tor Wizard'

select "without privoxy" 

then you're at the Proxy Settings, change the gmail standard to the pattern Name "youtube", URL pattern "http:*youtube.com*" (don't change "enabled" and "whitelist").

When going to (or searching) a blocked youtube page you can go to 'Firefox > tools > foxy proxy standard > use proxies based on predefined patterns'. 

When you want to see a video that is not blocked, disable the proxies since else you are going to loose a lot of speed.

That was easy.. Finally I can watch Justin Bieber from Germany :lolflag:

---

### Post by Joe of loath on 2011-03-31
I highly suggest against using tor for youtube.

The reason being, many Iranians, Chinese etc depend on TOR to see what's going on in the world. Their need for freedom is greater than your need to watch music videos.

Just use a web proxy. There are dozens of free proxy lists online.

---

### Post by crazy ivan on 2011-03-31
also nice to create a wildcard for [http://showip.net/](http://showip.net/), so you can see where you are browsing from ;)

---

### Post by doas777 on 2011-03-31
> **Joe of loath said:**
> I highly suggest against using tor for youtube.

The reason being, many Iranians, Chinese etc depend on TOR to see what's going on in the world. Their need for freedom is greater than your need to watch music videos.

Just use a web proxy. There are dozens of free proxy lists online.
+1. 
tor makes no decisions about where you go on the internet, but the operators count on us to make only reasonable demands of their network.

---

### Post by crazy ivan on 2011-03-31
I also thought about the issues of people needing privacy vs. circumventing music industry marketing agreements, but as far as I get it, the Tor network is getting stronger with every user.

from [https://www.torproject.org/about/overview.html.en]("https://www.torproject.org/about/overview.html.en"):
> 
...
Law enforcement uses Tor for visiting or surveilling web sites without leaving government IP addresses in their web logs, and for security during sting operations.
...
As Tor's usability increases, it will attract more users, which will increase the possible sources and destinations of each communication, thus increasing security for everyone. We're making progress, but we need your help. Please consider running a relay or volunteering as a developer.
...


---

### Post by doas777 on 2011-03-31
> **crazy ivan said:**
> I also thought about the issues of people needing privacy vs. circumventing music industry marketing agreements, but as far as I get it, the Tor network is getting stronger with every user.

from [https://www.torproject.org/about/overview.html.en](https://www.torproject.org/about/overview.html.en):
thats true, but TOR requires designated nodes, so yes, every operator willing to route tor traffic for an area makes it stronger, but most TOR users are not node operators.

---

### Post by crazy ivan on 2011-03-31
I guess everyone should run 'vidalia' once in a while to set the "relay" options in a way that contributes back to the cloud..

[http://www.torproject.org/docs/tor-doc-relay.html.en]("http://www.torproject.org/docs/tor-doc-relay.html.en")
[URL="https://help.ubuntu.com/community/Tor"]
https://help.ubuntu.com/community/Tor[/URL]

---

### Post by SeijiSensei on 2011-03-31
This is just such a bad idea.  There's absolutely nothing on YouTube that you need to see that makes it worth interfering with the ability of people in dangerous circumstances to communicate privately.  

Plus I bet (hope) you'd get awful throughput.

If you want to avoid region blocking, use a proxy, or rent a virtual machine in another country like the US and set up an OpenVPN tunnel.

Or, you know, just deal with being blocked.

---

### Post by doas777 on 2011-04-01
> **SeijiSensei said:**
> This is just such a bad idea.  There's absolutely nothing on YouTube that you need to see that makes it worth interfering with the ability of people in dangerous circumstances to communicate privately.  

Plus I bet (hope) you'd get awful throughput.

If you want to avoid region blocking, use a proxy, or rent a virtual machine in another country like the US and set up an OpenVPN tunnel.

Or, you know, just deal with being blocked.

well, actually there is some benefit to the use of tor for less serious circumstances. i agree with you that resources are limited and that is the primary concern, but if that were not so much the case, then it would be desirable to have people using tor for any-old-thing, not just sensitive communicades. its much easier to hide amongst the crowd, than it is when single yourself out. 

imagine this scenario: you wish to encrypt all your traffic out to your proxy server. however your isp generally sees less than 1% of user traffic being encrypted over their network. traffic from your connection appears to be 100% encrypted. that means that on any statistical breakdown, you are a significant outlier (eg: you stick out like a sore thumb).  if the isp was used to 20% of its customer traffic being encrypted, and >5% encrypt everything, then you would not stand out nearly so much. if 80% were encrypted, then you would be practically invisible. 

in order for privacy technologies to be effective, they must either be completely invisible to the outside observer (tor is not entirely) or their use must appear to be in line with the usage patterns that fit the societal norms in your region.

---

### Post by SeijiSensei on 2011-04-03
I run OpenVPN tunnels all the time when connecting to the servers I manage off-site.  So a lot of my traffic is encrypted.  I haven't heard a peep from any ISP I've ever used, and I've been running encrypted tunnels for years.

---

