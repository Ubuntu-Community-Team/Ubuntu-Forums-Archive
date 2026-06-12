---
title: "Browsing problems"
date: 2010-08-09
forum: Networking &amp; Wireless
---

### Post by rustysheriff on 2010-08-09
[COLOR=#000000][FONT=Times New Roman][FONT=Tahoma]Hi All,



I've been running Ubuntu on 2 of my laptops for a few months now with no problems. Last week, for no apparent reason, I stopped being able to browse on the wireless connection in my house. It connects, appears like the signal's solid, but just can't browse. As far as I remember, I didn't install any major updates, just the standard Ubuntu ones as and when they become available. Any idea why this would happen, and how to rectify it? (In very simple terms please :))

Thanks in advance for any help.

Brian
[/FONT][/FONT][/COLOR]

---

### Post by lovinglinux on 2010-08-09
Disable ipv6 on Firefox Preferences, by setting the **network.dns.disableIPv6** preference to **true**.
[LIST=1]
[*]Type **about:config** in the address bar, press Enter.
[*]Find network.dns.disableIPv6 in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]

---

### Post by rustysheriff on 2010-08-09
Thanks for the suggestion, I did as you said, but it hasn't made any difference :(

---

### Post by lovinglinux on 2010-08-09
What exactly happens when you try to browse a web site?

Can you install applications normally with the package manager?

Can you reach a web site with IP number?

---

### Post by rustysheriff on 2010-08-09
> **lovinglinux said:**
> What exactly happens when you try to browse a web site?

Can you install applications normally with the package manager?

Can you reach a web site with IP number?

It just tried to connect, but never gets there. When I say 'connect' I mean connect to the site rather than to the wireless/internet. Then times out eventually. Can't install apps either. I'm surfing using my mobile as a modem just now, so at least still have access.

I tried putting Chrome on in case it was the browser but no joy, same thing happens.

No tried reaching a site using an IP number, I'm not really sure how to do it, but I can try if you explain?

Thanks for your help so far!

---

### Post by lovinglinux on 2010-08-09
> **rustysheriff said:**
> It just tried to connect, but never gets there. When I say 'connect' I mean connect to the site rather than to the wireless/internet. Then times out eventually. Can't install apps either. I'm surfing using my mobile as a modem just now, so at least still have access.

I tried putting Chrome on in case it was the browser but no joy, same thing happens.

No tried reaching a site using an IP number, I'm not really sure how to do it, but I can try if you explain?

Thanks for your help so far!

So your problem is not on the browser, but in the wireless connection itself, otherwise you would be able to install packages. Unfortunately, I dunno much about that.

---

### Post by lukeiamyourfather on 2010-08-09
Do you have another device or computer to test the wireless to make sure the problem is not the access point/router itself? I have some cheap router from the cable company and the wireless will often "break" but resetting the router makes it work again, so it might not be the laptop causing the issue.

---

### Post by rustysheriff on 2010-08-09
> **lukeiamyourfather said:**
> Do you have another device or computer to test the wireless to make sure the problem is not the access point/router itself? I have some cheap router from the cable company and the wireless will often "break" but resetting the router makes it work again, so it might not be the laptop causing the issue.

I've got 3 laptops all running Ubuntu, and the same thing happens with all of them. Could well be that the problem is the router/access point, but it seems strange that the connection appears 'active' on the laptop, but browsing is not possible. Of course, when I phoned up the ISP they just say that they don't provide support for OS other than windows. I've tried re-setting the router but it doesn't make any difference.

---

### Post by lukeiamyourfather on 2010-08-09
> **rustysheriff said:**
> I've got 3 laptops all running Ubuntu, and the same thing happens with all of them. Could well be that the problem is the router/access point, but it seems strange that the connection appears 'active' on the laptop, but browsing is not possible. Of course, when I phoned up the ISP they just say that they don't provide support for OS other than windows. I've tried re-setting the router but it doesn't make any difference.

If three machines are having an issue its probably the router. Double check the wireless settings on the router itself to make sure all of the security features are setup correctly. For example if the MAC address filter is enabled on my router, machines can still connect and it shows full signal strength but they can't access the network.

---

