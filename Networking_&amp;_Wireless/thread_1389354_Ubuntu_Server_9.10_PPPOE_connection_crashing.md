---
title: "Ubuntu Server 9.10 PPPOE connection crashing"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by lordyarox on 2010-01-24
I've summarised my problem in 4 images (below). Addition information can be found at the very bottom of my post.

[IMG]http://i46.tinypic.com/295d1fo.png[/IMG]
[IMG]http://i49.tinypic.com/wu40e9.png[/IMG]
[IMG]http://i46.tinypic.com/246ludx.png[/IMG]
[IMG]http://i50.tinypic.com/qmxtar.png[/IMG]
[IMG]http://i46.tinypic.com/25jifbo.png[/IMG]

Additional information:
This is definitely a PPPOE error, as my linux machine had stable internet access while connecting through the router's DHCP. Since the router literally crashed and can no longer assign IP addresses (it's functioning like a switch), this is the only way I can connect. I am interested in solving the problem at hand, not getting a new router / attempting to port forward a workign router (I must use the ISP's router, and they only have the one crappy model).

Thanks in advance for all of your replies!

---

### Post by lordyarox on 2010-01-24
I did some more research and it appears I'm not the only one experiencing this issue. Any ideas? Didn't find an answer elsewhere :S

---

### Post by lordyarox on 2010-01-27
Anyone :(?

---

### Post by lordyarox on 2010-02-25
Has this issue been fixed yet?

---

### Post by lordyarox on 2010-03-02
Bump!

---

### Post by lordyarox on 2010-03-06
Anyone?

---

### Post by r939ick on 2010-03-06
> **lordyarox said:**
> Anyone?

It's a little difficult to follow your post, which might explain the lack of responses.  In this case, I think a few words might be worth a thousand pictures.  In addition, using images instead of text will prevent searches from finding your post.

If I read your post correctly, it seems you can successfully establish a pppoe connection, but that it drops unexpectedly and must be manually restarted.  Is that correct?

If that's the case, what do the ppp logs show when the connection disconnects?

---

### Post by lordyarox on 2010-05-29
For anybody experiencing this issue - I figured out it's probably a modem related issue (short disconnects) and due to the fact that Ubuntu server doesn't automatically reconnect the connection stays down.

However, shortly after I stopped checking this thread, I found a solution which reconnects the connection (monitors every minute) and I haven't had an issue since, even after abandoning the GUI (Gnome) altogether, and sticking to command-line with SSH (Putty).

For those of you who are interested in setting up an auto-reconnecting PPPOE connection for Ubuntu (and most variants), see [this](http://www.khattam.info/2010/03/07/howto-auto-re-connect-to-dsl-pppoe-in-linux/) link. I have archived the contents of the article, in case the link is dead (view attached .txt).

---

