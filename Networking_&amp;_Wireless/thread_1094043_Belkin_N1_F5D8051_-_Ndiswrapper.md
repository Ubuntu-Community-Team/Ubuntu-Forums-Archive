---
title: "Belkin N1 F5D8051 - Ndiswrapper"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by Andyz0r on 2009-03-12
Hi,

I am having trouble getting my Belkin N1 F5D8051 to work using ndiswrapper. It doesn't recognize the card in the network options.

I found the 'netmw245.inf' drivers that had worked for other people in Ubuntu, but I can't seem to get it to work.

I installed netmw245.inf using ndiswrapper and I checked to see if it was using the USB card (1799:8051), which is the same as the 'lsusb'

```

andy@ubuntu:~$ ndiswrapper -l
netmw245 : driver installed
	device (1799:8051) present

```

There is no light on the USB card.

Any help would be greatly appreciated! :)

Thanks,
Andy

---

### Post by SR_ELPIRATA on 2009-11-04
I managed to get my F5D8051v2 to work. Installed the ndiswrapper and used the netmw245.inf that was in the cd. Connected so far and still working! All this time and I didnt knew that the ndiswrapper software was on the cd.

ELP

---

