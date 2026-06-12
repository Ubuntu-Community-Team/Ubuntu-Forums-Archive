---
title: "Change DHCP client IP?"
date: 2006-01-28
forum: Networking &amp; Wireless
---

### Post by JamesNorris on 2006-01-28
Hi, I have two comps, onw windows one ubuntu, the ubuntu connects to the internet and the windows connects via the ubuntu machine.

Somehow, the IP address of the client machine has changed and all my samba links to the windows machine no longer work. It also doesn't seem to want to connect to the internet anymore.

Is it possible to change the IP address of the windows machine back to what it used to be?

---

### Post by Lambert on 2006-01-29
Don't know much about configuring windows here but you could do two things.

1. If you want a consistent ip then don't use dhcp, set the box with a static ip
2. Not knowing your setup but your dhcp-server on your router should allow you to set a consistent ip based on the connecting device's mac address, this way you have a consistent ip.

I would have to believe also that you could configure windows to always request a specific ip also but that depends if it's available and not handed out to another pc.

---

