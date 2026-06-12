---
title: "Slow Web browsing / DNS?"
date: 2009-10-17
forum: Networking &amp; Wireless
---

### Post by touchlikefire on 2009-10-17
My web browsing is excruciatingly slow, and I cannot figure out why.

Firefox 3.5 and Chromium both take an extremely long time to render pages, with a variation of 'resolving host' showing in the status bar.  Firefox 3 seems to be marginally faster, but that may just be perception. Also note: I've tried browsing in safe mode with the browsers, to no effect.

However, when issue the following command:
```
$ dig google.com

; <<>> DiG 9.5.1-P2 <<>> google.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 60471
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		196	IN	A	74.125.45.100
google.com.		196	IN	A	74.125.53.100
google.com.		196	IN	A	74.125.67.100

;; Query time: 45 msec
;; SERVER: 192.168.1.254#53(192.168.1.254)
;; WHEN: Sat Oct 17 18:07:33 2009
;; MSG SIZE  rcvd: 76

```

I get ~20-45 msec responses for any site I decide to dig.  Also, entering a URL as an IP address takes just as long.  All other machines on the LAN have a snappy browsing experience, including my similar laptop (Jaunty 64, ffx 3.5, etc).

Any ideas where to start? I tried examining Wireshark's output briefly, but didn't see anything interesting yet.

---

### Post by touchlikefire on 2009-10-20
Any help? This is really, really aggravating. I'm also afraid that when I upgrade to Karmic the problem will remain.

The pages render quickly in either Chrome or Firefox, once the hostname has been resolved, so its not a rendering issue. It seems that for whatever reason, dns traffic from the web browser is extremely slow.

Maybe it's something else, I dunno.

Bump.

---

### Post by touchlikefire on 2009-10-20
Any help? This is really, really aggravating. I'm also afraid that when I upgrade to Karmic the problem will remain.

The pages render quickly in either Chrome or Firefox, once the hostname has been resolved, so its not a rendering issue. It seems that for whatever reason, dns traffic from the web browser is extremely slow.

Maybe it's something else, I dunno.

Bump.

---

### Post by darco on 2009-10-20
You may need to disable IPV6 on the pc...you can search this forum for a how to. Did you just upgrade to x64? Did this problem just start?

good luck

darco

---

### Post by touchlikefire on 2009-10-20
Thanks for the response. I've been running x64 since Dapper, and I came across some other threads that referenced IPv6 disabling, but I'm not sure if I decided against it or not. 

In the meantime, I did some packet analyzing with Wireshark and came up with the following:
1) initial DNS requests from the web browsers are submitted as NB (netbios) three times (failing each time), then finally as a DNS A record request.
2) Even so, the DNS request contains a UDP checksum error
3) The big(ger) problem occurs with the TCP layer on an HTTP get request: it errors out with another TCP checksum error and is responsible for a 2 second delay

Thoughts:
In an effort to get Samba working with Win7/Win6 boxes I tinkered around with some tutorial and vaguely remember turning NetBIOS on. I now realize this was a huge mistake (as I suspected at the time) and want to turn it off, but I don't know how.

However, I don't think this will entirely solve the problem, because DNS UDP packets and TCP packets both have a checksum error, with Wireshark referencing "maybe checksum offloading is enabled". And maybe it is? But I wouldn't know where to verify that in the OS.

Lastly, and heaven forbid, but could this be a driver problem? I'm running an NF4 mobo with built in (nvidia) ethernet, and all previous versions from Dapper have worked fine, so I don't think this is the case. Yet, it could be a regression bug in Jaunty?

I know this all may sound a little bit daunting to some, but all help is appreciated b/c I myself don't know how to resolve this.

---

### Post by touchlikefire on 2009-10-20
I just purged samba, samba-common, samba-client, and anything else 'samba' that I could without affecting other packages, in an effort to get rid of their config files.

Tried removing "wins" option from /etc/nsswitch.conf

Formerly:```
hosts: files mdns4_minimal [NOTFOUND=return] dns wins mdns4
```

Now:```
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
```

Restarting the network via: **sudo /etc/init.d/networking restart** never works (for me), so I'm not sure the changes are live yet.  However, Wireshark is STILL showing **nbns** name queries.

I calculated the lost time loading "bbc.com" (which redirects to bbc.co.uk) in the browser: 7 nbns query attempts losing 1.6 seconds each, for a total of **11.2 seconds**!

This, on a vanilla profile of FFx 3.0. So you can imagine the problem on my FFx 3.5 with its bells and whistles!

Help?
----------
Edit: This above steps of removing "wins" from /etc/nsswitch.conf solved the problem

---

### Post by bab1 on 2009-10-20
> **touchlikefire said:**
> I just purged samba, samba-common, samba-client, and anything else 'samba' that I could without affecting other packages, in an effort to get rid of their config files.

Tried removing "wins" option from /etc/nsswitch.conf

Formerly:```
hosts: files mdns4_minimal [NOTFOUND=return] dns wins mdns4
```

Now:```
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
```

Restarting the network via: **sudo /etc/init.d/networking restart** never works (for me), so I'm not sure the changes are live yet.  However, Wireshark is STILL showing **nbns** name queries.

I calculated the lost time loading "bbc.com" (which redirects to bbc.co.uk) in the browser: 7 nbns query attempts losing 1.6 seconds each, for a total of **11.2 seconds**!

This, on a vanilla profile of FFx 3.0. So you can imagine the problem on my FFx 3.5 with its bells and whistles!

Help?

What happens now if you ping google.com or yahoo.com from the CLI ?

---

### Post by darco on 2009-10-20
> **touchlikefire said:**
> I just purged samba, samba-common, samba-client, and anything else 'samba' that I could without affecting other packages, in an effort to get rid of their config files.

Tried removing "wins" option from /etc/nsswitch.conf

Formerly:```
hosts: files mdns4_minimal [NOTFOUND=return] dns wins mdns4
```

Now:```
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
```

Restarting the network via: **sudo /etc/init.d/networking restart** never works (for me), so I'm not sure the changes are live yet.  However, Wireshark is STILL showing **nbns** name queries.

I calculated the lost time loading "bbc.com" (which redirects to bbc.co.uk) in the browser: 7 nbns query attempts losing 1.6 seconds each, for a total of **11.2 seconds**!

This, on a vanilla profile of FFx 3.0. So you can imagine the problem on my FFx 3.5 with its bells and whistles!

Help?

wow, removing samba, a little overkill wouldnt you say? 
That why I asked if the problem recently started. If it WAS right after you tweaked samba then maybe so..netbios is in windows right?

darco

---

### Post by Marlonsm on 2009-10-20
It happened to me some time ago.

What you need to do is this:

Open the terminal and run:
```
sudo apt-get install resolvconf
```

The resolvconf package manages the DNS, so you just need to tell it to change the DNS.

now run:
```
sudo gedit /etc/resolvconf/resolv.conf.d/base
```
It'll open a text file, copy this inside it:
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```
Those are the DNS you'll use.
Save.

Log out, log in and it should be solved.


If you can't log out right now, also run this (if you log out and log in, it'll be done automatically by resolvconf):
```
sudo gedit /etc/resolv.conf
```
and add these lines to the begin of the file:
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```
Save and it's done.

---

### Post by stugatzz on 2009-10-21
None of these solutions really worked for me. 

This did: [http://linuxwonderland.blogspot.com/2009/10/slow-web-browsing-in-ubuntu-904.html](http://linuxwonderland.blogspot.com/2009/10/slow-web-browsing-in-ubuntu-904.html)

(too much to copy/paste)

---

### Post by heldal on 2009-11-02
> **stugatzz said:**
> None of these solutions really worked for me. 

This did: [http://linuxwonderland.blogspot.com/2009/10/slow-web-browsing-in-ubuntu-904.html](http://linuxwonderland.blogspot.com/2009/10/slow-web-browsing-in-ubuntu-904.html)


That's irrelevant to the issue with what appears to be slow DNS. 

I suspect this has to do with a badly configured combination of DHCP and DNS servers. If the DHCP-server (e.g. a wlan or broadband router) responds with a domain-name and/or domain search-list, the client resolver may start looking for nonexistent hosts (wanteddomain.com becomes wanteddomain.com.yourlocaldomain). 

To dermine if this is the problem simply remove the "domain" and "search" statements from /etc/resolv.conf and restart your browser. 

The ideal solution is to set up a proper server for these services, but there are workarounds. One is to edit  /etc/dhcp3/dhclient.conf and remove "domain-name" and "domain-search" from the list of attributes the DHCP-client is asking for.   Some broadband/wlan routers also offer options to make it ignore domain/search requests, or the ability to specify the root-domain (.) for networks where there is no proper DNS-setup on the LAN-side.

----

It turns out that my problem really was a WLAN-router (D-link DIR655)which, when configured for DNS-relaying, failed to pass NXDOMAIN-responses back to the client. When queried directly, the upstream DNS-server immediately responds with NXDOMAIN. However, the behaviour has of the dns-resolver has obviously changed in karmic as the first request on the wire for a name always has a search-domain appended to it.

---

### Post by touchlikefire on 2009-11-16
I thought I closed out this thread by indicating it was solved, but apparently I did not.  Thank you everybody for your suggestions! It turned out to be the **wins** option in my **nss.conf** file, per my previous post.  Once I removed that and restarted the machine, web browsing was back to normal.

---

