---
title: "SSH tunnel to home computer in order to circumvent The Great Firewall"
date: 2012-07-05
forum: Networking &amp; Wireless
---

### Post by Mezzoforte on 2012-07-05
I have set up SSH to my home computer in Sweden and I have been able to successfully connect to it using an SSH tunnel with key authentication. Furthermore, I have set up Firefox so that it uses the tunnel (manual proxy with SOCKS). It seems to work - if the tunnel is on and the proxy settings set, I can surf the web as usual. If I close the SSH tunnel keep the Firefox proxy settings I can't open any website, which is logical and an indication that the proxy works.

However, with the SSH tunnel and the proxy up and working, I still can't open any sites that are not allowed by The Great Firewall. Like Wordpress, Facebook, Twitter, Google Docs and other websites.

If the data is sent to me over SSH from my home computer (from which these sites can be accessed), how can the data be blocked before it is downloaded to my laptop abroad?

Perhaps I have not quite understood how SSH tunnels work - grateful for any help or clarifications on the matter.

---

### Post by Lyfang on 2012-07-05
Hide these addresses from the forum. Compare your IP address with or without the proxy. [http://www.ip-adress.se/](http://www.ip-adress.se/)

---

### Post by asmoore82 on 2012-07-05
The blocked sites may be hijacked at the DNS level and I think that Firefox uses local DNS by default even when a SOCKS proxy is configured. Try navigating to "about:config" in the address bar, typing "dns" in the filter box, and toggle the key "network.proxy.socks_remote_dns" to **True**. It seems that for this to work you'll also need to be using SOCKS version 5.

Very little extra info on the key is here: [http://kb.mozillazine.org/Network.proxy.socks_remote_dns](http://kb.mozillazine.org/Network.proxy.socks_remote_dns)

And a lengthy, old Firefox bug report on the default setting needing to change based on SOCKS version is here: [https://bugzilla.mozilla.org/show_bug.cgi?id=134105](https://bugzilla.mozilla.org/show_bug.cgi?id=134105)

---

### Post by mitanc on 2013-05-17
> **asmoore82 said:**
> The blocked sites may be hijacked at the DNS level and I think that Firefox uses local DNS by default even when a SOCKS proxy is configured. Try navigating to "about:config" in the address bar, typing "dns" in the filter box, and toggle the key "network.proxy.socks_remote_dns" to **True**. It seems that for this to work you'll also need to be using SOCKS version 5.

Very little extra info on the key is here: [http://kb.mozillazine.org/Network.proxy.socks_remote_dns](http://kb.mozillazine.org/Network.proxy.socks_remote_dns)

And a lengthy, old Firefox bug report on the default setting needing to change based on SOCKS version is here: [https://bugzilla.mozilla.org/show_bug.cgi?id=134105](https://bugzilla.mozilla.org/show_bug.cgi?id=134105)

I don't know if this thread is dead, but I wanted to chime in real quick with my experiences.

For the DNS the above is correct.  You can do it manually through about:config in firefox and it will work just fine.  Another method is to set the pac proxy script (which you can google to find out how that works.)

Another way I have bypassed the DNS issue is setup my linux server to run polipo or privoxy and set that as a proxy in your browser.  Settings in both allow you to use SOCKS5 with name resolution so all the DNS is sent there and it should work fine.

Now the issue I am facing is I have setup the above as I have stated.  I can browse using my SOCKS proxy without any issue, but after leaving this running on my server, all things passing through the tunnel eventually freeze.  For example, I was browsing away just fine yesterday, turn on Chrome this morning and nothing seems to want to pass through the tunnel.  I can see in my logs the requests going through the tunnel, but nothing is coming back from the server.

I am in China and I don't know if this is the GFW detecting some funny business and blocking data coming back in or this could be some other setting I am overlooking.  Anyone know how to check?

Thanks for any replies in advance.

---

### Post by papibe on 2013-05-17
Please don't reply on old threads. It is much better to create a new one. Feel free to link this one if you want.

From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

**Thread Closed**.

---

