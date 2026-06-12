---
title: "ssh -D tunnel not working under Ubuntu, but does work in Putty?!"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by snek on 2010-09-01
I have the following ssh command I use to setup a tunnel for port 8080 so that I can bypass some work firewalls for checking out some gaming sites (mind you I am the system admin here):

ssh -C -D 8080 [email]user@domain.com[/email] -p 2266

Using Foxyproxy I can not use this tunnel.
However, when setting it up under Windows with the exact same configuration it DOES work. Thus I am thinking it is a problem on the client side, not server side..

Anybody have any ideas about this?

---

### Post by BkkBonanza on 2010-09-01
It will definately work with Firefox because I do it all the time. I don't know about FoxyProxy though and what it supports. You must choose SOCKS5 proxy at localhost:8080 for it to work with Firefox.

The -C option apparently slows down things on fast connections and I've never used it. You may want to do some tests and see how it affects your browsing. I suspect it makes no difference.

I usually use **ssh -fND 8080 user@ip** which puts ssh into the background. Also, for a desktop it's worth checking out gSTM package as it gives you a gui interface for managing ssh tunnels/proxies. It's only shortcoming is that it can't auto switch the system proxy setting which would be awesome for things like Firefox and TBird. I keep several possible servers config'd and then just click on the one I want as I need it.

Also, note with Firefox you may want to set the about:config remote dns option to prevent dns leakage locally. By default FF still does DNS local even when using a proxy.

---

### Post by snek on 2010-09-01
Hey, thx for the quick reply.
I used to always use Foxyproxy on my laptop with the same ssh command without problems, which is why I am so confused. I have it set to use localhost 8080 like you said, with SOCKS5.

I will try setting the proxy manually in firefox, to rule out that Foxyproxy is causing me problems and get back to you.

---

### Post by snek on 2010-09-01
[IMG]http://2.bp.blogspot.com/_eIRZl6Cv0yo/R1baI-jyveI/AAAAAAAAAss/ADfq4MlOR1s/s400/homer_doh.gif[/IMG]

It indeed works when set in Firefox, I guess Foxyproxy is broken for some reason.
I also set the remote option in Firefox to get around the DNS blocking I have setup through OpenDNS on our corporate network.

Guess I'll let the Foxyproxy guys know about this.

Thanks for the help!

Btw, I use the -C option because our corporate internet connection is only 200KB/s SDSL.
My upstream at home is already higher than that and I want to limit the amount of bandwidth I actually use so as not to negatively affect other users.

---

