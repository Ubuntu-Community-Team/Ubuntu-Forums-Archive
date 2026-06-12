---
title: "Linksys WUSB54gv4 system problems"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by ihavenoname on 2006-06-19
There is already a bug report about the system hanging using theres particular wifi cards and the default kernel modules. Many have fixed it with irqpoll, I have not. In any case I wanted to focus on this in light of other issues.

Like the others my system is prone to hang using the Networking gui. However using 

```
sudo dhclient rausb0
```

I could get to the internet. But my system would hang sometimes using this setup. So I blacklisted rt2570. And went on to use Ndiswrapper. (This was using Dapper beta with kernel 2.6.15-22-386 I belive. When I updated to kerne 2.6.15-23-386 ( I am not sure if this is related but I saw it as a relvant point to make) The internet would disconnect after an unspecified amount of time. Using both the default Ubuntu Network gui aswell as NetworkManager. (This problem also exsists in Mepis.) This happend with all the kernels including the 686 kernels.(The 686 kernels also tend to freeze up the system using ndiswrapper( I have not tested this with the rt2x00 drivers)  Trying to bring the network back up was very dificult. Upon reconnting however the internet would only last for a few minutes before once again disconnecting. Restarting however solved the problem. Until the network went down again. This problem persists still even after the Final version of Dapper has been released. 

Does anyone have a suggestion as to why the internet goes down, or why my computer freezes?

Note: Until now I have been convinced that the reason for the freezing was SMP support in the kernel or something purely network related. Recently I used CPU-Z to check the info on my system. It reported that one of my RAM slots contained a pc 2100 while the other had a pc 2700. Would that result in my computer freezing?


Thank you for all of you help.

---

