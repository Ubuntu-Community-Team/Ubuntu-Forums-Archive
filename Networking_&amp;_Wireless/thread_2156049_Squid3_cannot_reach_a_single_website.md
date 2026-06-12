---
title: "Squid3 cannot reach a single website"
date: 2013-06-20
forum: Networking &amp; Wireless
---

### Post by lakekeman on 2013-06-20
Hello,
I installed ubuntu 13.04 and squid3 and used a very basic squid configuartion.
Everything works fine except one single website:

[http://lsbntweb.lsb-niedersachsen.de/](http://lsbntweb.lsb-niedersachsen.de/)

Squid is loading forever and nothing happens.

I have another squid server running which works fine with this website so I guess its a simple configuration error.

Maybe someone can point me quickly to the right solution!
Thanks a lot!

---

### Post by SeijiSensei on 2013-06-20
Try connecting to the site with a browser on the squid proxy server.  If you don't have a GUI, you can install the **elinks** text-based browser.  What happens?

---

### Post by lakekeman on 2013-06-20
Ok I think the problem is not the squid but the ubuntu itself. I cannot access the website from the squid machine using wget, waiting for response and nothing happens:

Connecting to lsbntweb.lsb-niedersachsen.de (lsbntweb.lsb-niedersachsen.de)|212.59.58.34|:80... connected.
HTTP request sent, awaiting response... ^C

This website is reachable whith another squid proxy server or when connected directly to the internet line with a windows machine.

---

