---
title: "Home Network Monitoring Tools?"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by Jeenyus on 2009-01-27
I live in an apartment with 6 other roommates all sharing one internet connection.  We have the standard Linksys Wireless b/g router which connects 5 of our laptops through wireless connections and also connects a desktop computer, a Playstation 3, and an Xbox 360 through wired connections.  I've been browsing around webpages reading about all of these different network monitoring tools but still haven't been able to fully understand what each of them can/can't do without having to install each one and give it a try.

So my question is, does anyone have any suggestions for a network monitoring tool that can provide me the standard (or what I call standard :) ) features such as total download/upload, bandwidth consumption, etc. and perhaps also one that is able to see these figures not only by IP address but also by MAC address or some other form that is tied to the computer hardware (we don't use static IPs so it would be kinda tough to tell who's computer is who's all the time).

I apologize if some of this doesn't make a lot of sense, and feel free to correct me about anything I mentioned, I'm fairly savvy with computers themselves but I don't have a lot of knowledge with networking.

Thanks in advance,
Jeenyus

---

### Post by bgerlich on 2009-01-27
I think this would suit you just fine:
[http://bandwidthd.sourceforge.net/](http://bandwidthd.sourceforge.net/)

The only problem is - like all such software it has to run on the router/switch to do it's job properly.

No all is lost, your router may actually run Linux, what model is it exactly?

---

### Post by Jeenyus on 2009-01-27
The router model is the Linksys WRT54G.

Thanks for the quick response.

---

### Post by bgerlich on 2009-01-27
You should check this out:
DD-WRT [http://www.dd-wrt.com/wiki/index.php/Linksys_WRT54G/GL/GS/GX#Identifying_Your_Version](http://www.dd-wrt.com/wiki/index.php/Linksys_WRT54G/GL/GS/GX#Identifying_Your_Version)

Openwrt [http://wiki.openwrt.org/OpenWrtDocs/Hardware/Linksys/WRT54G](http://wiki.openwrt.org/OpenWrtDocs/Hardware/Linksys/WRT54G)

ot this Tomato [http://www.polarcloud.com/tomatofaq#how_do_i_find_my_linksys_wrt54](http://www.polarcloud.com/tomatofaq#how_do_i_find_my_linksys_wrt54)

to check if your router is compatible with any of those linux distros for Linksys WRT routers.

---

