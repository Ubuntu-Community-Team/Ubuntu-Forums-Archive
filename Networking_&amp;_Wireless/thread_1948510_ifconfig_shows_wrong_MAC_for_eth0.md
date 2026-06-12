---
title: "ifconfig shows wrong MAC for eth0"
date: 2012-03-28
forum: Networking &amp; Wireless
---

### Post by youngmit on 2012-03-28
I have a thinkpad laptop that i use on a wired network a lot. for some reason, when i run ifconfig it says that the MAC address for eth0 is aa:00:04:00:0a:04, while network manager is saying that it is F0:DE:F1:8D:3B:6C. I am pretty sure that the latter is correct and that somehow ifconfig is confused. I can still connect to the network and get an IP from the DHCP server, but it is giving me an address from the dynamic pool, while i should be getting a static based on my MAC address.

any ideas as to why ifconfig and network-manager are showing different hw addresses?

I also tried to set the mac address manually with ifconfig, which changed it, but upon reboot it goes back to the other address...

here is my hw from lspci:

```
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
```

Also, how would one find the hw address that is actually burned onto the network interface (the absolutely right one)?

thanks for any help!

---

### Post by haqking on 2012-03-28
> **youngmit said:**
> I have a thinkpad laptop that i use on a wired network a lot. for some reason, when i run ifconfig it says that the MAC address for eth0 is aa:00:04:00:0a:04, while network manager is saying that it is F0:DE:F1:8D:3B:6C. I am pretty sure that the latter is correct and that somehow ifconfig is confused. I can still connect to the network and get an IP from the DHCP server, but it is giving me an address from the dynamic pool, while i should be getting a static based on my MAC address.

any ideas as to why ifconfig and network-manager are showing different hw addresses?

I also tried to set the mac address manually with ifconfig, which changed it, but upon reboot it goes back to the other address...

here is my hw from lspci:

```
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
```

Also, how would one find the hw address that is actually burned onto the network interface (the absolutely right one)?

thanks for any help!

That mac address is synonymous with DECnet protocols installed.

I answered a similar thread the other day see here [http://ubuntuforums.org/showpost.php?p=11792246&postcount=6](http://ubuntuforums.org/showpost.php?p=11792246&postcount=6)

---

### Post by youngmit on 2012-03-28
thanks a lot, it worked!

---

### Post by haqking on 2012-03-28
> **youngmit said:**
> thanks a lot, it worked!

no worries.

you are welcome.

Peace

---

