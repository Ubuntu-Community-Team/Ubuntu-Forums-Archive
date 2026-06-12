---
title: "Dell e6400 intel 5100 wifi random disconnect (11.04)"
date: 2012-05-10
forum: Networking &amp; Wireless
---

### Post by biodojo on 2012-05-10
We have a computer cart of 30 laptops running 11.04. The only thing we did to get them to work wel was to add the line [COLOR=#000000][FONT=Arial]iwlagn swcrypto=1[/FONT][/COLOR][COLOR=#000000][FONT=Arial] to /etc/modules[/FONT][/COLOR] (the wifi was really slow without this). The laptops work really well until randomly 3-10 of them will disconnect from wifi and cannot reconnect without a restart. Even disabling and re-enabling networking via Network Manager or the hardware switch doesn't work. Any ideas on how to troubleshoot, or force reconnect without a restart? Would sudo modprobe -r iwlagn then sudo modprobe iwlagn be worth a shot or is that essentially what Network Manager does when you disable wireless?

---

