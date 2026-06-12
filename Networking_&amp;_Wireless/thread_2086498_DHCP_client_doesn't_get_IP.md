---
title: "DHCP client doesn't get IP"
date: 2012-11-21
forum: Networking &amp; Wireless
---

### Post by mv77 on 2012-11-21
Hi!

I've just switched my internet provider. The new one has a cable modem that is working in default bridge mode. The idea is to connect just one PC, and sure enough, it works. 
If I connect my XP laptop and leave lan settings on automatic, I get an IP, dns, and gateway right away.

But, I have a small LAN and I use ubuntu box as a router, always have. I need this modem to transfer the 'outside' ip to my lan card, just like it does in XP test.

But, it doesn't work!!

I've tried putting this in my etc/network/interface file:

auto eth1
iface eth1 inet dhcp

but it didn't work.

Since I still have an old internet provider active, I've tried using the modem/router from that one to see if I would get an IP, and I did.

So, my conclusion is that the I need to somehow tweak the dhcp client in ubuntu (fresh install 12.1 server) to work with this modem (like it does with XP pc), but I have no idea how to even start troubleshooting this and fix it.

Can anyone help me?

I'm not a complete newbie, but I'm far from being a guru, so a detailed help would be great.

Thanks!

---

### Post by Lars Noodén on 2012-11-21
Are you sure it is eth1?  eth0 is usually the default.

---

### Post by mv77 on 2012-11-21
Thanks for the reply.

Yes, I'm sure, eth0 is on my LAN side, eth1 is the one that's connected to the modem. Also, I'm accessing the server trough static ip eth0 so...

---

### Post by Lars Noodén on 2012-11-21
What happens when you run dhclient against eth1 manually?

```

sudo dhclient -v eth0

```

---

### Post by mv77 on 2012-11-22
> **Lars Noodén said:**
> What happens when you run dhclient against eth1 manually?

```

sudo dhclient -v eth0

```


Well, it was actually a modem problem, not the linux box (although I've installed at least 2 ubuntu servers and 1 slackware during the last day and a half).

The stupid internet provider's modem gets locked to a first MAC you plug it into. After I figured that out and powered the modem off and on again, the ubuntu server got it's IP right away.

Thanks for the replies btw!

---

### Post by Lars Noodén on 2012-11-22
Ok.  Good it's figured out, but what a stupid modem.  I didn't know there were still ones that do that.  Rather than reseting the modem each time, you could just set the MAC address to what the modem is expecting.

---

