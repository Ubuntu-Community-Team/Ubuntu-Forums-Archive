---
title: "Can't find Network Tools"
date: 2012-10-24
forum: Networking &amp; Wireless
---

### Post by Mesanna on 2012-10-24
I'm not sure if I'm having a dumb moment here, but where is the Network Tools package in 12.10? I thought it was called net-tools (though I might be mistaken). It's the one where you can ping and do Whois lookups and so on. When I search for network from the Dash, I get "Network Connections", "Network" and "System Monitor", none of which is what I want. When I tried to launch net-tools from the terminal, it tells me command not found. According to Synaptic, net-tools is definitely installed.

Have I broken something, or has something been renamed?

---

### Post by wojox on 2012-10-24
Should be there. Try:
```
sudo apt-get update; sudo apt-get install gnome-nettool
```
Search the Dash for portscanner

---

### Post by Mesanna on 2012-10-24
Thank you Wojox! That fixed it. :)

I'm not sure why my installation didn't include it, unless they've stopped installing it by default? Either way, I'll know in future what it's called. Thanks again!

---

