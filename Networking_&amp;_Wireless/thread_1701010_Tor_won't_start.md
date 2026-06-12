---
title: "Tor won't start?"
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by Throne777 on 2011-03-05
So I've been trying to get Tor to work & it I've hit dead end after dead end. Followed all guides to the letter & I still can't get the bugger to work.

I installed Tor (from their repository), I've set up polipo using their config file. I also installed Vidalia as they (Tor's website) lay out.

First run, Vidalia said it connected, but Chrome was refusing to acknowledge anything of the sort (despite setting it up correctly -so sayeth the guides anyway). So I restarted the computer in case polipo hadn't restarted (even though I'd told it to) after I changed the config file. Now Tor won't start at all. The log gives the following:

```

Mar 06 02:34:36.319 [notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Mar 06 02:34:36.319 [notice] Opening Socks listener on 127.0.0.1:9050
Mar 06 02:34:36.319 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Mar 06 02:34:36.319 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
Mar 06 02:34:36.319 [err] Reading config failed--see warnings above.

```

Any ideas?

(Oh, and I tried reinstalling Tor, but that changed nothing)

---

### Post by dirty_harry on 2011-03-07
hi Throne777,

netstat helps you to determine what is running on port 9050. looks like this for me running tor:
```
$ sudo netstat -ap | grep 9050
tcp        0      0 localhost:9050          *:*                     LISTEN      1020/tor        
tcp        0      0 localhost:9050          localhost:56905         VERBUNDEN   1020/tor        
...
```could it be that you have proxivy, polipo and vidalia running on the same port?

I found this very helpful:
[https://www.torproject.org/docs/faq#DoesntWork](https://www.torproject.org/docs/faq#DoesntWork)

and I followed this to install and it is working on my two systems; installation via tor reps and using polipo:
[https://www.torproject.org/docs/debian.html.en#ubuntu](https://www.torproject.org/docs/debian.html.en#ubuntu)
[https://www.torproject.org/docs/tor-doc-unix.html.en#polipo](https://www.torproject.org/docs/tor-doc-unix.html.en#polipo)

you might want to change (back?) to firefox, because Tor-Button & NoScript & UserAgentSwitcher is in my opinion the best compination.

**OT:** [I]to be honest, I use it rarely for irc, because I wanted to hidde my ip like most people do on freenode(correct me if I'm wrong, +x everyone); but my irc-chat-skills are rather poor :-|
forum suits me more.[/I]

---

### Post by Throne777 on 2011-03-08
> **dirty_harry said:**
> hi Throne777,

netstat helps you to determine what is running on port 9050. looks like this for me running tor:
```
$ sudo netstat -ap | grep 9050
tcp        0      0 localhost:9050          *:*                     LISTEN      1020/tor        
tcp        0      0 localhost:9050          localhost:56905         VERBUNDEN   1020/tor        
...
```could it be that you have proxivy, polipo and vidalia running on the same port?

I found this very helpful:
[https://www.torproject.org/docs/faq#DoesntWork](https://www.torproject.org/docs/faq#DoesntWork)

and I followed this to install and it is working on my two systems; installation via tor reps and using polipo:
[https://www.torproject.org/docs/debian.html.en#ubuntu](https://www.torproject.org/docs/debian.html.en#ubuntu)
[https://www.torproject.org/docs/tor-doc-unix.html.en#polipo](https://www.torproject.org/docs/tor-doc-unix.html.en#polipo)

you might want to change (back?) to firefox, because Tor-Button & NoScript & UserAgentSwitcher is in my opinion the best compination.

**OT:** [I]to be honest, I use it rarely for irc, because I wanted to hidde my ip like most people do on freenode(correct me if I'm wrong, +x everyone); but my irc-chat-skills are rather poor :-|
forum suits me more.[/I]

Yeah, I tried doing it on Firefox & it worked. So for some reason Chrome won't use it despite me using the settings that should apparently work for it. Oh well.
Vidalia still won't work, but I think I may know where I messed up for that one.

---

### Post by dirty_harry on 2011-03-08
Chrome & Tor :evil: ?!
You want to use a browser developed by a company that makes money out of harvesting userdata and be anonymous at the same time? Rather strange?

I used this site to check tor and browser anonymity:
[http://what-is-my-ip-address.anonymous-proxy-servers.net](http://what-is-my-ip-address.anonymous-proxy-servers.net)

Chromium 9.0.597.107 is on my lucid system working with tor:
I had to adjust the proxy settings only for socks to 127.0.0.1:9050

Chromium/Chrome seems to be bad for privacy:
[http://superuser.com/questions/170236/where-can-i-find-an-equivalent-of-torbutton-for-google-chrome](http://superuser.com/questions/170236/where-can-i-find-an-equivalent-of-torbutton-for-google-chrome)
[http://www.theregister.co.uk/2009/12/14/chrome_dns_query_bug/](http://www.theregister.co.uk/2009/12/14/chrome_dns_query_bug/)

---

### Post by Throne777 on 2011-03-11
> **dirty_harry said:**
> Chrome & Tor :evil: ?!
You want to use a browser developed by a company that makes money out of harvesting userdata and be anonymous at the same time? Rather strange?

I used this site to check tor and browser anonymity:
[http://what-is-my-ip-address.anonymous-proxy-servers.net](http://what-is-my-ip-address.anonymous-proxy-servers.net)

Chromium 9.0.597.107 is on my lucid system working with tor:
I had to adjust the proxy settings only for socks to 127.0.0.1:9050

Chromium/Chrome seems to be bad for privacy:
[http://superuser.com/questions/170236/where-can-i-find-an-equivalent-of-torbutton-for-google-chrome](http://superuser.com/questions/170236/where-can-i-find-an-equivalent-of-torbutton-for-google-chrome)
[http://www.theregister.co.uk/2009/12/14/chrome_dns_query_bug/](http://www.theregister.co.uk/2009/12/14/chrome_dns_query_bug/)

By Chrome I meant Chromium, my bad.
I'd use Firefox, but currently Firefox is just generally awful. I won't be considering switching until FF4 is properly released.

---

### Post by dirty_harry on 2011-03-11
firefox has its issues... but it is still my first choice form me. also I have to admit that I use chormium for some major flash sites(eg puplic tv-stations stream the program).

nevertheless I was interested in your idea using chromium and tor, but as this post by the tor-project suggests I stay with FF:
[https://blog.torproject.org/blog/google-chrome-incognito-mode-tor-and-fingerprinting](https://blog.torproject.org/blog/google-chrome-incognito-mode-tor-and-fingerprinting)

Edit:
looks like I'm wrong/relying on outdated information, because here is an equivalent of the tor-button for chromium >>
>> [http://blog.zx2c4.com/440](http://blog.zx2c4.com/440)
I haven't tried it though

---

