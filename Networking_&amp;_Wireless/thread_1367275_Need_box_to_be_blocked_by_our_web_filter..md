---
title: "Need box to be blocked by our web filter."
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by hotstovejer on 2009-12-29
Hi all!

I am currently building kiosks for my company, and I have an image that works just fine, thanks to remastersys! But now, the business is requesting that all websites pass thru the barracuda web appliance to monitor where the users are going. I already added it to the domain, and am trying to get it to where I can control web access via AD, but I am unable to. I put the proxy in for the whole system, in Firefox, anywhere I can find it. Any ideas as to what the problem might be?

Thanks!

Jeremy

---

### Post by doas777 on 2009-12-29
just to clarify, you want to push down settings for firefox on ubuntu systems, using MS's active directory? if that is correct, it's not likely to happen, I'm afraid.

you could just use a dhcp server to push the appliance's IP out as the gateway, but you would have to proxy everything, instead of just firefox's traffic.

---

### Post by hotstovejer on 2009-12-29
I'm ok pushing it out to the entire system. I just have no idea how I would do that in a corporate setting such as ours.

---

### Post by 98cwitr on 2009-12-29
> **hotstovejer said:**
> Hi all!

I am currently building kiosks for my company, and I have an image that works just fine, thanks to remastersys! But now, the business is requesting that all websites pass thru the barracuda web appliance to monitor where the users are going. I already added it to the domain, and am trying to get it to where I can control web access via AD, but I am unable to. I put the proxy in for the whole system, in Firefox, anywhere I can find it. Any ideas as to what the problem might be?

Thanks!

Jeremy

which barracuda did ya'll get? We use the 410 at our office. Set it up inline and you won't have to worry about proxy settings. If you have to have it as a proxy, it needs to be directly behind the firewall and a rule needs to be in place in the firewall to push all traffic from your network to the IP thats in the barracuda.

---

