---
title: "DHCP Client getting invalid IP info from ISP DHCP Server"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by brianw on 2009-11-14
Hello,

I am not sure where this all went wrong. All was working until yesterday. Just a quick overview of my network; I have no router presently. I have no switch. I move around my cable modem to where I need the internet (PS3 or my laptop).

So I was streaming a movie from netflix on my ps3. I wanted to work on my laptop, so I yanked the modem and moved it all to the kitchen. The ubuntu box gets an ip and all the rest of the info from the dhcp server. I can ping my own address given, but I cannot ping my default gateway. So I fight with this for a while and decide to see if the same thing happens on my XP dual boot. When it asks the dhcp server, it gets a total different address in a different subnet and everything.

I tried using dhclient3 directly and I still get the other ip info that does not work. Is there a way to force dhclient or NM to forget what address it last got? I think this is where the problem lies. The dhcp client is requesting the old address and the server is obliging...

If you need any info, just ask.

Thanks,

Brian

---

### Post by Iowan on 2009-11-14
You can see if [this]("http://ubuntuforums.org/showpost.php?p=7963396&postcount=2") one helps...

---

### Post by brianw on 2009-11-15
Well I was able to release the IP. But when I asked for another one, it keeps giving me that one. The odd thing is, I boot up rescuecd (a linux livecd) and it gets the same ip. And it doesn't work. Windows gets a total different ip/subnet.... I am totally at a loss.....

Why would one OS get a certain IP/subnet and another get something different? Windows and PS3 work, any linux distro does not....

Brian

---

### Post by dmizer on 2009-11-15
Some ISPs filter connections by MAC address to prevent multiple devices from connecting to their network.

---

### Post by Iowan on 2009-11-16
An inexpensive router might go a long way toward solving the problem (if ISP will allow it to connect)... and save wear/tear on the connector.

---

### Post by doas777 on 2009-11-16
not sure if you haven't tried it, but cablemodems usually don't like being hotswapped. have you tried unplugging it for 10 minutes? I know, it sounds hoakey, but it often works.

---

