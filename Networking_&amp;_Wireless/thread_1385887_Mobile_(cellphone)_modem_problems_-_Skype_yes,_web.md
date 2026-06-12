---
title: "Mobile (cellphone) modem problems - Skype yes, web surfing no."
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by niceguy123 on 2010-01-20
I have been trying to configure my Nokia E71 as a modem for my loptop connecting via USB cable. The phone shows up in the network connects under Mobile Broadband, but when I cut off my other wireless connection and connect to the mobile I can not surf the web. At first I though that it is not connecting at all and searched the web for answers, called the cell provider, who it turns out doesn't support Linux. And played around with network configurations. At some point I saw on another forum that someone with simalar problem relized that they were able to use skype via this connection. I checked and saw that I could do that too but still no web surfing. 

What's worng, how can I make it right?

Thanks.

---

### Post by GeorgeVita on 2010-01-20
Hi **niceguy123**, an idea is to check DNS and default route settings.

While connected (mobile broadband): right click network-manager icon > Connection information
Default route for my connection shows: 10.64.64.64

You can also check: Edit connections > Mobile broadband > click on provider > Edit > IPv4 settings > Method=Automatic (PPP)
Using 'Automatic (PPP ) addresses only you can 'adjust' DNS

Some other tests at [http://ubuntuforums.org/showpost.php?p=8652529&postcount=2](http://ubuntuforums.org/showpost.php?p=8652529&postcount=2)

Regards,
George

---

### Post by niceguy123 on 2010-01-20
Thank you GeorgeVita you solved my problem. I am now connected via the cell modem.

---

