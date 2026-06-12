---
title: "configuring internet on kubuntu"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by remy_cook on 2009-08-24
Hi, I have configured the internet (broadband) in kubuntu 9.04 at my home using pppconfig ( I have on board lan card.); It is working perfectly 
But when I tried to configure internet at my friend's home(same ISP), then it is not working.  He had dual boot. And his internet works fine over windows
The problem is when I run the command, [COLOR="DarkRed"]sudo pppconfig[/COLOR], it accepts all necessary details.
But when I try to start it by using say [COLOR="Sienna"]pon provider[/COLOR], then it doesn't show any output. And there is no process of pppd.

Then I manually written the file dsl-provider as it is exists in my machine. after [COLOR="DarkRed"]pon dsl-provider[/COLOR]; it just says "[COLOR="DarkRed"][COLOR="SandyBrown"]rp-pppoe.so loaded[/COLOR][/COLOR]". But no compile message as it shows in my machine.

So if anybody has any idea about it, please guide me.

Thanks

---

### Post by Iowan on 2009-08-24
Dunno if [this]("https://bugs.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/339882") bug still applies to Kubuntu and PPPOE...

---

