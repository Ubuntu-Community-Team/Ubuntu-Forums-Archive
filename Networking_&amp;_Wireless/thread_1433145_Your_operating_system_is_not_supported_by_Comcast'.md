---
title: "Your operating system is not supported by Comcast's Installation Wizard. Please call"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by NoPoChris on 2010-03-18
Here's a funky one.

When I try to go to any Wikipedia page I get this message:

Your operating system is not supported by Comcast's Installation Wizard. Please call 1-800-COMCAST to setup your account.

This only happens with Wikipedia and I've tried it on both Chrome and Firefox browsers. It doesn't matter if I click on a link from Google, select a bookmark, etc. Any suggestions? I'm using Ubuntu 9.10.

---

### Post by Brandel Valico on 2010-03-18
Mainly a bump and some info. I also run Comcast and can say that it's not a usual issue. I goto Wikipedia with Firefox on their system all the time and never have this issue. Hopefully someone will be able to help out.

Best of luck

---

### Post by jrssystemsnet on 2010-03-18
> **NoPoChris said:**
> Here's a funky one.

When I try to go to any Wikipedia page I get this message:

Your operating system is not supported by Comcast's Installation Wizard. Please call 1-800-COMCAST to setup your account.

This only happens with Wikipedia and I've tried it on both Chrome and Firefox browsers. It doesn't matter if I click on a link from Google, select a bookmark, etc. Any suggestions? I'm using Ubuntu 9.10.They're most likely screwing you with bad DNS.  Try dropping to a shell and using the **dig** command:

```
you@box:~$ dig wikipedia.org

; <<>> DiG 9.4.2 <<>> wikipedia.org
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 2113
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 3

;; QUESTION SECTION:
;wikipedia.org.			IN	A

;; ANSWER SECTION:
wikipedia.org.		1056	IN	A	208.80.152.2

;; AUTHORITY SECTION:
wikipedia.org.		83551	IN	NS	ns1.wikimedia.org.
wikipedia.org.		83551	IN	NS	ns2.wikimedia.org.
wikipedia.org.		83551	IN	NS	ns0.wikimedia.org.

;; ADDITIONAL SECTION:
ns1.wikimedia.org.	1909	IN	A	208.80.152.142
ns0.wikimedia.org.	1166	IN	A	208.80.152.130
ns2.wikimedia.org.	2388	IN	A	91.198.174.4

;; Query time: 37 msec
;; SERVER: 192.168.0.10#53(192.168.0.10)
;; WHEN: Thu Mar 18 17:21:50 2010
;; MSG SIZE  rcvd: 159

```

Now try using the dig command again, but this time **specifying a known good DNS server**:

```
you@box:~$ dig @4.2.2.1 wikipedia.org

; <<>> DiG 9.4.2 <<>> @4.2.2.1 wikipedia.org
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 30766
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;wikipedia.org.			IN	A

;; ANSWER SECTION:
wikipedia.org.		3549	IN	A	208.80.152.2

;; Query time: 39 msec
;; SERVER: 4.2.2.1#53(4.2.2.1)
;; WHEN: Thu Mar 18 17:24:18 2010
;; MSG SIZE  rcvd: 47

```

In my case, the answers matched from my default DNS provider and from 4.2.2.1 (a publicly available DNS provider).  If they DON'T match in your case, then that's your problem, and the fix is to stop using Comcast's DNS and to use a good provider instead (configure your router and/or your machine to use 4.2.2.1 and 4.2.2.2 as DNS providers instead of using whatever Comcast is pushing to you by DHCP).

If the answers match on both **dig** commands, but you're getting that Comcast installation wizard crap, try one more thing... do **wget -O - [http://en.wikipedia.org/](http://en.wikipedia.org/)** and tell us what result you get from that.

---

### Post by jrssystemsnet on 2010-03-18
... also note that the output of **dig NS wikipedia.org** should look like this:

```
;; ANSWER SECTION:
wikipedia.org.		83114	IN	NS	ns1.wikimedia.org.
wikipedia.org.		83114	IN	NS	ns2.wikimedia.org.
wikipedia.org.		83114	IN	NS	ns0.wikimedia.org.

;; ADDITIONAL SECTION:
ns1.wikimedia.org.	1472	IN	A	208.80.152.142
ns0.wikimedia.org.	729	IN	A	208.80.152.130
ns2.wikimedia.org.	1951	IN	A	91.198.174.4

```

---

### Post by chili555 on 2010-03-18
If fixing DNS doesn't do it, you might try changing useragent on Firefox. We can assist you if you get to that.

---

### Post by NoPoChris on 2010-03-18
Thanks jrssystemsnet, changing the DNS worked

---

### Post by ScottinSoCal on 2010-03-18
> **NoPoChris said:**
> When I try to go to any Wikipedia page I get this message:

Your operating system is not supported by Comcast's Installation Wizard. Please call 1-800-COMCAST to setup your account.

They're trying to install something when you go to Wikipedia? Huh. I wonder if they let people know before they install?

---

### Post by Skaperen on 2010-03-18
I'm using Comcast from home.  I just fired up my netbook because it has a relatively unmodified Ubuntu, which uses the DNS that comes from DHCP, which my wireless router gets from Comcast.  I even verified the DNS was Comcast's numbers.  I went to a Wikipedia page and got it with no troubles.

I don't know why you are having trouble with just a particular site.  Maybe they have some setting wrong that's specified to your area.  Or maybe your account has been deactivated or uninstalled.  But, I'd think that would affect all access and not just Wikipedia.  If Comcast had a grudge against Wikipedia and decided to interfere, I suspect we'd all be affected by that (and it would be quickly on Slashdot, which they might also then try to block).  However, I've not seen any such issue with Comcast.  I have been relatively happy with their server (of course, I'd love to have gigabit bandwidth for a dollar a year, too ... ain't gonna happen).

FYI ... I had no trouble setting up with Comcast, initially.  I just told them I was attaching a wireless router ... which I was doing (a WRT54GL running Linux).

---

### Post by NoPoChris on 2010-04-04
I'm marking this as unsolved. It seems that now I can access Wikipedia, but I get the error message when I visit Google.

Edit:
Just thought I'd mention that everything works fine on my roommate's laptop with Vista. Not really a surprise, but I figured it might be helpful.

---

### Post by kaldor on 2010-04-04
> **NoPoChris said:**
> I'm marking this as unsolved. It seems that now I can access Wikipedia, but I get the error message when I visit Google.

I got an error like that on one site. I changed my agent from Firefox to Internet Explorer 7 using a plugin, and the problem went away.

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

In a nutshell, you can mask your Firefox as IE running on XP.

---

