---
title: "ssh -f -C2TN -D PORT username@hostname"
date: 2012-09-17
forum: Networking &amp; Wireless
---

### Post by hlxshady on 2012-09-17
Hi all,

I have been using a VPN via following connection to the server:
ssh -f -C2TN -D PORT username@hostname

and have the system proxy setting configured as:
proxy server: localhost
port: PORT

This used to work for a long time until recently distributions of linux.(Because I don't like the new unity interface, I had been using a pretty old ubuntu until it is no longer supported.)
The symptom is that the browser always shows failed to connect to the proxy.

I did a bit search over the internet and found a software name gSTM (gnome ssh tunnel manager), which does more or less the same thing as the ssh connection above does.

With the same setting in the system proxy, from the browser I got:
SSH-2.0-OpenSSH_5.9p1-hpn13v12
Protocol mismatch.


Does anyone know if I missed any setting?
or if there is any change to the mechanism of the linux proxy?


Cheers,
Stephen

---

