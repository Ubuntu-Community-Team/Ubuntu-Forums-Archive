---
title: "Can (assigned) IP address cause problems?"
date: 2011-10-24
forum: Networking &amp; Wireless
---

### Post by donsy on 2011-10-24
My Internet connection is with a cable modem directly connected to my PC with an ethernet cable, no router. Yesterday I was having severe connectivity issues which appeared to be DNS related, I couldn't even ping Yahoo! The cable company sent a tech over who checked all outside connections and said everything was ok and the problem was either with my modem or ethernet card. I questioned the cable modem since it was only a few months old, so he brought in his laptop and connected it to the modem with my ethernet cable and everything worked fine.

So now I'm suspecting the ethernet card in my PC, but something I noticed got my attention. I noticed that the DHCP assigned address and the default gateway that he got on his laptop was different from what I was getting. Also, Windows device manager was reporting that the device was working properly. (I have a dual-boot but don't know how to check this in Ubuntu.) So my question this, is it possible that the IP address and default gateway were the cause of the problem and not my ethernet card? I'm currently connected through a USB port.

---

### Post by dandnsmith on 2011-10-24
I've used Ubuntu with both (not at the same time) manually assigned IP address and DHCP assigned IP address. The only time I've had a problem (apart from an ethernet card failing) was when I found that it was trying to use IP6, and that gave the version I was using  problem (I've also had this with Windows7).

I suggest you first check what the address is using ifconfig (cf ipconfig for Windows) from a terminal window.
If it looks OK, then you could try using ping and traceroute to verify the ability to resolve DNS addresses and route.

---

