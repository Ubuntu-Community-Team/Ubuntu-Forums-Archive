---
title: "Failure to lookup certain websites"
date: 2013-04-13
forum: Networking &amp; Wireless
---

### Post by monkeypigs on 2013-04-13
Got a strange problem here, on of my machines (64 bit running 13.04) frequently struggles to lookup my own websites (hosted with namecheap if that's of any significance)
Yesterday, the machine completely stopped resolving any of my domains. Firefox, thunderbird, epiphany are all affected. 
I can ping the domain no problem, all other sites load without issue. 

Now this initially sounds like a namecheap issue, however, other machines on the network load the sites OK (Including the 12.10 Gnome remix I'm on at the moment)
Interestingly a Windows 7 VBox on the affected machine with a bridged NIC loads the sites fine

Now I initially thought, OK, I'm using a beta OS, can't be guaranteed to work as expected, so I tried a 13.04 live CD, same problem. Also tried 12.10 both 32 and 64 bit live CDs, still no joy. 

Our only Windows machine on the network is also finding the sites just fine, so it's not a network or hosting problem.

Also tried installing another NIC in the affected machine (wireless) to rule out any random issues with the actual network cable, still no joy.

lspci shows 

```
02:00.0 Ethernet controller: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet (rev c0)
```

I've also had a look at putting an entry in the hosts file, disabling dnsmasq, replacing network-manager with wicd

I'm at a total loss as to why this is only affecting our own sites and only on one specific machine. 

If anyone has any ideas or wants to test, try loading kingsbridgecourt.com (I'm sure it will load just fine for you!)

Hope that someone has some suggestions!
Many thanks
Iain

---

### Post by prodigy_ on 2013-04-13
```
$ dig @8.8.8.8 kingsbridgecourt.com 

; <<>> DiG 9.8.1-P1 <<>> @8.8.8.8 kingsbridgecourt.com
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 22970
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;kingsbridgecourt.com.          IN      A

;; ANSWER SECTION:
kingsbridgecourt.com.   1200    IN      A       198.187.29.15

;; Query time: 265 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Sat Apr 13 14:31:50 2013
;; MSG SIZE  rcvd: 54
```

Looks fine to me. Try that on your client machine. If it works, there's something wrong with DNS settings on that machine.

---

### Post by monkeypigs on 2013-04-13
> **prodigy_ said:**
> [code]

Looks fine to me. Try that on your client machine. If it works, there's something wrong with DNS settings on that machine.

Thanks for checking, however it can't be related to the dns settings due to having tested with a live CD......?

---

### Post by prodigy_ on 2013-04-13
> **monkeypigs said:**
> live CD...
...does not mean the DNS server you query returns correct and/or up to date responses. That's why I explicitly specified a Google DNS server in my example. It's known to be robust and reliable. If **dig @8.8.8.8** returns expected results (i.e. the same result on all clients), you should look at your IP configuration and see which DNS server you normally query. If it does not, you probably want to **traceroute 8.8.8.8** for a sanity check.

If you're sure everything's OK but the website still doesn't load:
```
sudo traceroute -T 198.187.29.15
telnet 198.187.29.15 80
```

If the above works, look at your web server / site configuration.

---

### Post by monkeypigs on 2013-04-13
> **prodigy_ said:**
> ...does not mean the DNS server you query returns correct and/or up to date responses. That's why I explicitly specified a Google DNS server in my example. It's known to be robust and reliable. If **dig @8.8.8.8** returns expected results (i.e. the same result on all clients), you should look at your IP configuration and see which DNS server you normally query. If it does not, you probably want to **traceroute 8.8.8.8** for a sanity check.

If you're sure everything's OK but the website still doesn't load:
```
sudo traceroute -T 198.187.29.15
telnet 198.187.29.15 80
```

If the above works, look at your web server / site configuration.

I know that the DNS servers are not at fault as every other device on the network uses the same DNS servers set by the router. 

It's not a web server issue for the above same reason......

---

