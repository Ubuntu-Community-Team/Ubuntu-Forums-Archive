---
title: "Huawei MT882 and Linksys Router connected together, Huawei blocks ports"
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by themusicalduck on 2011-01-18
I have a modem and router combination as described in the title. The problem is that I can open the correct ports on my router, but the modem tends to block them anyway.

Is there a way to disable all blocking on the modem, considering that the router should handle all security itself? I assume the problem is to do with the NAT settings. On the NAT settings page for the modem I have the options of DMZ, NAT, Redirect or None and redirect lets me port forward certain ranges. The problem is I don't know what IP I need to use for the modem, considering it's connected to the router and so the static IP I set up for my PC will not be right. I tried forwarding ports for the IP address that my router uses as it's gateway, but it didn't work.

Is this just impossible to do with kind of modem? All I want is to be able to SSH into my PC. :| If I try to do that, I get Connection Refused.

edit: setting it to any kind of bridged mode doesn't work, the internet just stops working.

---

### Post by pricetech on 2011-01-18
From what you describe, it sound like your modem has a built in router.  Have you tried using that and leaving your router out of the picture ??

You might also be getting blocked by your ISP.  Some of them do that.

---

### Post by themusicalduck on 2011-01-18
I could do, but the connection is shared so I was hoping to use the wireless capabilities of the router.

I have had it working before bringing the router into the equation, so there shouldn't be a problem with the ISP.

Also, I just tried setting the modem to bridged mode rather than PPPoA, but had no luck. It stopped the internet working entirely.

---

### Post by pricetech on 2011-01-21
I've never used a modem in bridged mode, but I have read support pages that say the provider doesn't support them in that configuration, so I've haven't felt compelled to try it.

You should be able to forward everything to your router through your modem and make that work.  Try making the router's IP the DMZ address.  That should work.

Keep us posted.

---

### Post by themusicalduck on 2011-01-26
Finally figured it out using your suggestion.

If you look on the DD-WRT router page there is an IP under System Information called WAN IP. If you set that IP rather than the LAN IP as the DMZ IP on the modem then it works.

Thanks very much.

---

