---
title: "Transmission torrent breaks internet"
date: 2012-07-20
forum: Networking &amp; Wireless
---

### Post by thomsmells on 2012-07-20
I've had this problems over 3 distros now, Lubuntu 11.10, Linux Mint LXDE and Lubuntu 12.04, but not on Crunchbang, so I don't know whether it's an LXDE problem or Ubuntu.

Basically transmission torrent breaks my internet after a while, could be an hour, could be 5 minutes. Afterwards my computer won't shut down properly and has to be turned off.

I had issues with Crunchbang, so don't want to go back to it, but this problem is really annoying.

Any fixes?

---

### Post by ajgreeny on 2012-07-20
If you open transmission with the terminal do you get any useful error messages that might give you any clues?

---

### Post by Cheesehead on 2012-07-20
Cheaper home routers cannot handle large numbers of simultaneous connections and need to be reset.

---

### Post by thomsmells on 2012-07-29
No error messages, the internet just stops working.

And why would this problem not occur on a particular distro if it relates to the router?

---

### Post by Laiquendi on 2012-07-29
Maybe you have flood defense active on your router? I have a quite cheap router and I had the same problem, after turning off router firewall the problem disappeared (yes I know I should not use it without firewall;)

---

### Post by mikewhatever on 2012-07-29
> **thomsmells said:**
> No error messages, the internet just stops working.

And why would this problem not occur on a particular distro if it relates to the router?

Can you post some info about the wireless hardware:

lspci -nnk | grep -iA2 net

ifconfig

I suspect the problem may be related to the wireless driver rather then the router. Ubuntu, Lubuntu and Mint are essentially the same, at least as far as wireless connectivity is concerned, because all of them use the same Ubuntu packages and configs. Crunchbang is not based on Ubuntu, so it's a similar, and yet different three.

---

