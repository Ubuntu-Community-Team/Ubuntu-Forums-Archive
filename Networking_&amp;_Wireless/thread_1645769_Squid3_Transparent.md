---
title: "Squid3 Transparent"
date: 2010-12-15
forum: Networking &amp; Wireless
---

### Post by sureshk89 on 2010-12-15
Hi,
I installed squid3.
I want to make it as transparent proxy.I looked over the internet and tryed all options.
I edited my http port in squid.conf file
"http_port 4880 transparent"
Then i forwarded packets using iptables and shorewall. it dint work.

"iptables -t nat -A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.0.1:4880
iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 4880"
eth0=internet
eth1=local computers
My squid is working manually when i change my proxy settings in browser

Thanks and Regards
Suresh

---

### Post by furlabs on 2010-12-15
Hi, I'm no iptables expert (I do everything in shorewall) but according to this link here: [http://www.faqs.org/docs/Linux-mini/TransparentProxy.html#s5](http://www.faqs.org/docs/Linux-mini/TransparentProxy.html#s5) you want the redirect to apply to the interface the packets come in on. In your case, they come in on eth1 and out eth0.

```
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 4880
```

As far as I can tell the DNAT is not required.

---

### Post by sureshk89 on 2010-12-15
Hi
I even tryed that,not working. manually working after chabging in browser.
can you tell how to forward port in shorewall

Thanks
suresh

---

### Post by furlabs on 2010-12-19
Here is what works for me (with squid running on port 3128 ):
```
REDIRECT        loc        3128         tcp     www      -
```

---

### Post by X1R1 on 2011-01-21
same problem here, Proxy works great but the transparency doesnt work.

I followed the tutorial here:

[http://kuscsik.blogspot.com/2008/01/transparent-proxy-with-squid-3-on.html](http://kuscsik.blogspot.com/2008/01/transparent-proxy-with-squid-3-on.html)

Did you managed to get it working?

---

### Post by kashif_max on 2011-12-25
Yes even mine is not working as transparent. I also tried this http_port IP:3128 transparent but same result...

---

### Post by kashif_max on 2012-06-09
It's now working. I enabled packet forwarding and applied iptable rule as mentioned by furlabs... ;)

---

### Post by gillecaluim on 2012-09-06
well, I still can't get it working transparently:confused:
I created a macro.Squid =

[B]#ACTION    SOURCE    DEST    PROTO    DEST    SOURCE    RATE    USER/
#                PORT(S)    PORT(S)    LIMIT    GROUP
PARAM    -    -    tcp    3128[/B]

and using these rules I'm able to manually proxy http requests:
[B]Squid/ACCEPT    loc    $FW
Web/ACCEPT    all    all[/B]

but I've tried all kind of different configs and am still not able to get transparent proxying to work.  Could someone please spell out exactly their squid/shorewall configuration that is working for transparent proxying....
Thanks

---

