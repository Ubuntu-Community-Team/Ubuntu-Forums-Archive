---
title: "Static IP @ Home. Search Domain??"
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by Roasted on 2010-08-04
I like to have a static IP on my main desktop at home since it's also a file server, so it's nice having the static IP in case the DNS doesn't update properly, which seems to happen from time to time.

The thing is, on a static IP, I often have issues after a while where I will retain an active connection to IRC, Pidgin, etc, but I'll lose connectivity to web sites. Each site I go to it simply bombs out. If I unplug ethernet and plug it back in after 10 seconds, it's fine, but this issue happens almost daily.

So to test, I set up a 2nd network profile (btw being able to make network profiles is fricken nice) and set it to full DHCP, and haven't had a problem with it since.

BUT I want to have a static IP...

IP - 192.168.1.149
SM - 255.255.255.0
GW - 192.168.1.1

Then for DNS I put 192.168.1.1.

To test, I also put 192.168.1.1 in search domain. Nothing happened.

Anyway, what's up? What else can I do?

---

### Post by oldfred on 2010-08-04
Is you .149 within the range that your router uses for DHCP. I could not even use any within the range. You have to use a number outside the default assignment range the router has set. Or all the numbers for DHCP are in effect used. Overlap of numbers then can cause problems.

---

### Post by Roasted on 2010-08-04
> **oldfred said:**
> Is you .149 within the range that your router uses for DHCP. I could not even use any within the range. You have to use a number outside the default assignment range the router has set. Or all the numbers for DHCP are in effect used. Overlap of numbers then can cause problems.

Hmm, good thought. But I didn't think it would matter as long as I didn't have enough devices on the network to get that high and use up IPs to hit the 149 area. I figured choosing the high end was smart. So are you saying it should be outside of the default 50 IP addresses for DHCP? aka, 192.168.1.0-192.168.1.149? I wonder if 150 would be a winner.

---

### Post by oldfred on 2010-08-04
You just reminded me. I use NFS to sync my portable to my desktop and have the desktop set to :20 in the scripts. But I just converted full time from Karmic to Lucid and did not change to fixed address from DHCP.

---

### Post by Iowan on 2010-08-04
Have you considered setting up a static lease in your DHCP server (based on MAC address)? It'd still need to be outside the lease range.

---

