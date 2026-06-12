---
title: "How To Change Ip Address In Linux?"
date: 2013-07-20
forum: Networking &amp; Wireless
---

### Post by PinStripedTie on 2013-07-20
I'm really surprised there is an extremely minimal amount of info on how to change ones IP address with most Linux forums.

I need to figure out how to change the ip address for personal reasons.

Is there anyone who has a clue on how to do this? I know on Windows, you can buy software to make this happen. But in 
Linux I have yet to see anything regarding this issue.

If you can help, I don't mind you PMing me if that is better or posting is good as well if you would like.

I am on COX Communications(cable) with a Cisco modem/router combo unit (DPC3825).

Any help will be greatly appreciated!

---

### Post by Cheesemill on 2013-07-20
Which IP address are you talking about?

Your internal IP address is probably being assigned by DHCP from your router, you may be able to change this in your router settings.

Your external IP address is assigned to you from your ISP, there is no way of changing this but you can use a VPN service to make it appear as if your traffic is originating from another location.

---

### Post by PinStripedTie on 2013-07-20
External.

But I used to be on DSL and had no problems changing my ip anytime I wished.
WHY is cable so different?.

Do you know who the most inexpensive and good VPN is?

Thanks

---

### Post by Cheesemill on 2013-07-20
> **PinStripedTie said:**
> But I used to be on DSL and had no problems changing my ip anytime I wished.

I'd be very interested in knowing how you managed this. Your external IP address is assigned by your ISP and there is no way you can influence which IP address they give you.

---

### Post by cutesar on 2013-10-10
> **PinStripedTie said:**
> I'm really surprised there is an extremely minimal amount of info on how to change ones IP address with most Linux forums.

I need to figure out how to change the ip address for personal reasons.

Is there anyone who has a clue on how to do this? I know on Windows, you can buy software to make this happen. But in 
Linux I have yet to see anything regarding this issue.

If you can help, I don't mind you PMing me if that is better or posting is good as well if you would like.

I am on COX Communications(cable) with a Cisco modem/router combo unit (DPC3825).

Any help will be greatly appreciated!

You can change ip address using ifconfig command itself. To set IP address example :  192.168.1.5, enter command:
 # ifconfig eth0 192.168.1.5 netmask 255.255.255.0 up
 # ifconfig eth0

or use the link  [how to change ip    ]("http://www.howtogeek.com/118337/stupid-geek-tricks-change-your-ip-address-from-the-command-line-in-linux/")
to change your ip address in Linux . After changing your ip address use [Ip-details.com ]("http://www.ip-details.com/") /whatismyip  to check whether new ip is assigned or not .

---

