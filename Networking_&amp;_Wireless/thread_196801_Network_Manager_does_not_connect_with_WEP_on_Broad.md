---
title: "Network Manager does not connect with WEP on Broadcom BCM4306 802.11b/g"
date: 2006-06-14
forum: Networking &amp; Wireless
---

### Post by meusmetus on 2006-06-14
I have Ubuntu 6.06  with Linksys Wireless G PCMCIA card with Broadcom BCM4306 802.11b/g and I used this post to configure it:

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

It works but Network Manager does not connect with WEP. When I disable WEP on my access point I can connect without problems. Connection is very slow. When WEP is enabled Network Manager is asking me for passphrase and when I put it in it does not connect.

Any idea?

---

### Post by Krusty Ruffle on 2006-06-14
My card is different than yours, but the problem sounds simular to what I had. To fix it I did:
```
sudo gedit /etc/network/interfaces 
```

and added this:

```
 	
auto eth1
iface eth1 inet dhcp
wireless-essid nameofsession
wireless-key hexcodeforpassphrase
wireless-enc restricted

```

though your card may not be eth1, but the idea is the same. name of session is pretty self explanitory, & is likely to already be there, the wireless key may also be using text, it depends on what your setup is I think, if you need the hexcode there are several websites that can translate it, or you can use a hex editor to get it. The last line is the one that was really getting me, it tells the card to only transmit if it's encoded. That was the setting that was keeping me from connecting.....

I don't know for sure that all of this is going to be the same for your card, but it'll hopefully help you out :)

---

### Post by meusmetus on 2006-06-14
Hey, thanks for the reply. I also have wireless card on eth1 but my /etc/network/interfaces file is all commented out with &#8220;#&#8221; because I use Network Manager to connect.

In Network Manager I chose 64/128 Hex Key and enter it. 

After I posted my original question suddenly I was able to connect. Now I am afraid to reboot because last time I rebooted I could not connect again.

---

