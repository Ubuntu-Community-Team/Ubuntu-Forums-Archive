---
title: "Why tor needs polipo to provide http proxy"
date: 2012-06-07
forum: Networking &amp; Wireless
---

### Post by vikkyhacks on 2012-06-07
I installed TOR ,,,,, the firefox packed with TOR lacks flash and many other plugins ... So i made chromium use the proxy localhost:9050 (default tor-socks) port but it gave me an error message and din work...... After installing polipo and with a few editing in its config files i was able to use chrome by using the proxy server as localhost:8123 with tor's anonymous network ... 
My question is why do i need such a proxy like polipo between tor and my browser ... why cant i just use localhost:9050 as my proxy

---

### Post by Lauscher on 2012-06-07
Be careful using Chrome - it sends a Chrome-ID, something else than your torified IP, so you will never be anonymous using Chrome.

Tor is a SOCKS-proxy and no HTTP-proxy, only a few browsers support this directly. 

Firefox doesn't need Privoxy or something else. In Firefox you can set your proxy configuration using SOCKS-Host 127.0.0.1  Port 9050. Leave the other entrys empty. Choose SOCKS v5. Now Firefox is using Tor directly.

You can check your anonymity on this site: [http://ip-check.info/](http://ip-check.info/)
Also check the fingerprint of your browser: [https://panopticlick.eff.org/index.php?action=log](https://panopticlick.eff.org/index.php?action=log)

If you want to get really good anonymity with tor, use Firefox with [Jondofox-profile.]("https://anonymous-proxy-servers.net/en/jondofox.html")

Greetings from germany, Lauscher

---

### Post by vikkyhacks on 2012-06-09
Hmm those links were really very useful ... and even browsers like firefox don seem to support direct socks service ....

---

### Post by Lauscher on 2012-06-09
> **vikkyhacks said:**
> even browsers like firefox don seem to support direct socks service ....
Firefox supports direct socks service. Look here:
 > In Firefox you can set your proxy configuration using SOCKS-Host  127.0.0.1  Port 9050. Leave the other entrys empty. Choose SOCKS v5. Now  Firefox is using Tor directly.

---

