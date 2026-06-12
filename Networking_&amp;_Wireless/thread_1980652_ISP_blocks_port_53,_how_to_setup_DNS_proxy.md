---
title: "ISP blocks port 53, how to setup DNS proxy"
date: 2012-05-15
forum: Networking &amp; Wireless
---

### Post by efrens on 2012-05-15
So here's what's going on.

Lately I've been getting a lot of DNS timeout errors while browsing using my mobile broadband connection. The most sensible thing I remember doing was to change the DNS server settings on my connection profile on Network Manager. I set it up to use Google Public DNS 8.8.8.8, 8.8.4.4. Connection Information says that indeed I changed it to be so, BUT, the problem persisted.

Then I discovered that when doing nslookup, the Domain resolver used is still the one provided by my ISP. Since Connection Information says otherwise, and aided by ignorance and lack of patience on my part, I filed a bug at launchpad. [bug 997242]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/997242") I since converted it to a question, [https://answers.launchpad.net/ubuntu/+source/dnsmasq/+question/197196]("https://answers.launchpad.net/ubuntu/+source/dnsmasq/+question/197196")

[IMG]https://launchpadlibrarian.net/104669804/yunosame.png[/IMG]

While doing further Google-ing on the matter, however, I discovered that my ISP is in fact routing all port 53 transactions to use their own DNS resolver. SO it is, I think,  the reason why even after setting up on network manager for my connection to use a custom dns server, it still ends up using my ISPs unreliable DNS resolver just the same.

The solution for this, I found out, is to use something called DNS Proxy. Our Windows friends undergoing similar ISP oppression, according to this blog, is using a DNS Proxy software called Acrylic. Instructions can be found here: [http://goo.gl/4z7ke]("http://goo.gl/4z7ke") (I tried it on my Windows 7 Virtualbox, and it works like breeze.)

The idea is to setup a DNS Proxy that listens at port 53, tell Ubuntu to direct its DNS queries to it, and then setup the DNS Proxy to redirect DNS lookups to DNS services on the net that accepts transactions on a non-standard port not (yet) tinkered by my oppressive ISP, such as OpenDNS which I hear conducts business on port 5353.

Now, my question is, networking guru's of ubuntuforums, how do I set about doing this?

Thanks in advance.

---

### Post by efrens on 2012-05-16
I was trying out OpenDNS's DNSCrypt a while ago as per [this]("http://www.webupd8.org/2012/02/encrypt-dns-traffic-in-linux-with.html") instructions but it still uses UDP port 53 and the only way to make it transact on another port was to use TCP, which is slow for the purpose of DNS resolution, among other issues.

SO, anyone? A good DNS proxy that can help me adopt [this instructions for Windows]("http://goo.gl/4z7ke") to Ubuntu?

---

### Post by SeijiSensei on 2012-05-16
12.04 now uses dnsmasq as a local server on all machines, even desktop clients.  You might be able to fiddle with its settings to have it forward queries to a remote server on a non-standard port.

---

