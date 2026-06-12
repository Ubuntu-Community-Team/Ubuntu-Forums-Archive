---
title: "Squid Proxy, with SOCKS and ssh"
date: 2011-06-16
forum: Networking &amp; Wireless
---

### Post by androssofer on 2011-06-16
Hi, 

I use ssh to port forward my browser(firefox) using SOCKS to a "server"(ubuntu desktop with ssh ;-) ) I have in the UK, to watch iplayer etc wen traveling... I forward port 1024 (default port for SOCKS? **mite b untrue..). the "server" is running ubuntu 11.04. 

i was wondering could i set up a transparent proxy(squid) on the "server" in the hope tht it speeds up the connection etc... my thot was get squid to listen on port 1024, or set up the ssh port forwarding to the squid port... 

would tht work? is the a better/different way to do it? 

the issue is tht sometimes the ssh connection can b slow at times, and was hoping using a transparent proxy could help a tad...?

---

### Post by androssofer on 2011-06-17
to conclude:

due to a misunderstanding of proxies etc... this post was almost pointless... :-(

I set up squid to listen on its default port as a transparent cache...

using this tutorial/how to:
[http://ubuntulinuxhelp.com/speed-up-and-improve-web-surfing-with-an-ubuntu-squid-server/](http://ubuntulinuxhelp.com/speed-up-and-improve-web-surfing-with-an-ubuntu-squid-server/)

then ssh'd onto the machine to forwarding port 8080.

eg: ssh -L 8080:localhost:3128 user@hostname

this forwards all port 8080, thru my transparent proxy. didnt need to worry about socks.. who knew?

then configured firefox to use localhost:8080 for all its protocols. 

job done!

---

