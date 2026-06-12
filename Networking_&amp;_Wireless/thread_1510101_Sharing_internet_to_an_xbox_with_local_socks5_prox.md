---
title: "Sharing internet to an xbox with local socks5 proxy"
date: 2010-06-15
forum: Networking &amp; Wireless
---

### Post by Brendan_ST on 2010-06-15
Hello, I have a bit of a strange network situation going on here. We have to access the internet through a http proxy with our user names & pass's here over wireless which is fine but I have an xbox I want to connect to the internet but cannot directly because they dont have the proxy options in them that I need.

This is what I need to do to get around it all: I have PuTTY setup on my computer to host a local socks5 proxy to my VPS that i can connect my browsers to too access internet, which I've done successfully but I need to some how route my ethernet connection which I have plugged in to my xbox to go through this socks5 proxy I have setup. On Windows I've managed to bridge the ethernet through out my wireless easily but this just throws the xbox up against the proxy again, I need it to somehow connect to 127.0.0.1:13337 where my socks5 is set up but I haven't found any such functionality anywhere after alot of Google and tinkering.

I'm running Ubuntu 10.04 at the moment and i have access to windows 7 if you know of ways to do it on windows thats fine, what ever works.

xbox --ethernet cable-- > laptop --PuTTy-- > wireless > internets!!

Is it possible to do this? If so, how?

Thanks!

---

### Post by Brendan_ST on 2010-06-15
Bumpady bump 5 hours later, maybe someone on the other side of the planet can help. Gnight Australia.

---

### Post by Brendan_ST on 2010-06-19
Bump again, sorry to those who have no idea and are putting up with this thread floating around but I've still not managed solve this. You don't need to have an Xbox or even know anything about them; I just need to connect my Ethernet port to my local socks5 proxy somehow but I have little experience with networking so I am stumped for ideas.

---

### Post by hydrogen18 on 2010-06-20
Under Ubuntu 10.04 you need to configure iptables to rewrite all requests coming on on the ethernet adapter of your laptop to the SOCKS5 proxy. This essentially means reading the existing tcp/ip header(trivial with iptables), then rewriting the packet into a SOCKS5 request to the proxy while preserving its content( nontrivial). For Xbox Live functionality you will need the SOCKS5 proxy to be capable of forwarding traffic in reverse, I have no idea if putty implements this.

---

### Post by Brendan_ST on 2010-07-14
Thanks for the response & sorry it took me so long to check up on the thread.

"Under Ubuntu 10.04 you need to configure iptables to rewrite all requests coming on on the ethernet adapter of your laptop to the SOCKS5 proxy. This essentially means reading the existing tcp/ip header(trivial with iptables), then rewriting the packet into a SOCKS5 request to the proxy while preserving its content( nontrivial)"

I can understand the basics of this but my computer skills extend to only having written a small bash script and some PHP things for fun so I would need someone a bit more experienced to help.
I will Google around in the meantime as I have been but if anyone can do this I would appreciate it if you instructed me (held my hand) through all the things I need to tinker with.

"For Xbox Live functionality you will need the SOCKS5 proxy to be capable of forwarding traffic in reverse"

I'm not entirely sure what this means but I can both upload and download through the proxy with web browsers and torrents perfectly fine.

---

### Post by Brendan_ST on 2010-11-12
Bumping again, trying to tackle the problem again so I'll try re-explain the situation a little differently...

I've managed to share internet from my laptop, which is on wireless, to another computer connection via Ethernet using the Network Connection GUI in Ubuntu only I need to direct this connection through my VPS any way possible to bypass a firewall.

If anyone can guide me or maybe noobify what hydrogen18 was saying I'd very very happy.

Also, I'm not trying to do anything Illegal here it is just that the login system really complicates connecting to the internet.

---

### Post by Brendan_ST on 2010-11-13
One more try I guess.. been trying to find help with this for about 10 months now :(

---

