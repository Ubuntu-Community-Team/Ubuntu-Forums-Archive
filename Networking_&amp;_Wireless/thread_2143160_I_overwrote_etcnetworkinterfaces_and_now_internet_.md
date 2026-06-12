---
title: "I overwrote /etc/network/interfaces and now internet doesn't work"
date: 2013-05-08
forum: Networking &amp; Wireless
---

### Post by Maheriano on 2013-05-08
I have a server which was running on a static IP perfectly for a year. Friday night it rebooted during an update so I had to copy everything off of it and reinstall Ubuntu to get it working again. I didn't want to have to configure the static IP again so I copied out /etc/network/interfaces, did the reinstall and then copied it back. Before I copied it back the machine was running great, I was connecting to the internet just fine on the default DHCP settings. Then I copied the file back and now nothing works. No matter what I add or remove in the file, ifconfig always shows a configuration for lo but nothing else. If I try and run ifdown for eth0 I get:
```
ifdown: Interface eth0 not configured
```

I've made many edits to the interfaces file to just give it the default settings for DHCP and it still won't connect. I can't get any internet on this machine and all I did was replace this one file. Can't I just revert it back or copy the default settings? Why doesn't it work?

---

### Post by steeldriver on 2013-05-08
it's hard to help since you haven't actually posted your current /etc/network/interfaces file - I'd start by looking for typos (I remember spending a morning chasing down a networking problem years back - turned out to be the /etc/resolv.conf got renamed as /etc/re**sl**ov.conf) - after that checking logs like dmesg and syslog for any errors related to the interface hardware / drivers

---

### Post by Maheriano on 2013-05-08
I managed to get it by changing eth0 to em1 (for some reason). But now I can only connect to it from my internal network, not externally. Even though I can use the external IP to connect to it, people outside my network can't.

---

### Post by Maheriano on 2013-05-09
Guess I just had to wait for other DNS to update the domain. It worked after a while. Weird.

---

