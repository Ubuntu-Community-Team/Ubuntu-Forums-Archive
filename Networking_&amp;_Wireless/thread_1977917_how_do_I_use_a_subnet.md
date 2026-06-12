---
title: "how do I use a subnet"
date: 2012-05-10
forum: Networking &amp; Wireless
---

### Post by wlraider70 on 2012-05-10
heres my problem.

I have two independent networks setup. Home and office. I have set them up following the same basic guidelines.

10.10.10.xxx
255.255.255.0

The router .1,   server is .2, and so on.


Now I want to VPN from 1 to the other, and I have read that VPNs can have some issue with the same ip configurations on both networks. 


Can I use a subnet to fix the issue?
My router will let me pick all 4 octets, but the lowest subnet I can do is 255.255.255.0

Any advice?

---

### Post by alphacrucis2 on 2012-05-10
> **wlraider70 said:**
> heres my problem.

I have two independent networks setup. Home and office. I have set them up following the same basic guidelines.

10.10.10.xxx
255.255.255.0

The router .1,   server is .2, and so on.


Now I want to VPN from 1 to the other, and I have read that VPNs can have some issue with the same ip configurations on both networks. 


Can I use a subnet to fix the issue?
My router will let me pick all 4 octets, but the lowest subnet I can do is 255.255.255.0

Any advice?

Change one of them to a different subnet so they don't conflict eg 10.10.10.0/24 for one and 10.10.11.0/24 for the other. (Note the /24 is shorthand for 255.255.255.0). Another option I suppose would be to use NAT (both source and destination) so that each sees the other as a different subnet via the VPN. Probably a lot easier to just renumber one of them.


Edit BTW we get this problem at work a lot as we have lots of VPNs to other parties who often have subnets that conflict with us and each other. We have no choice really but to use NAT as renumbering the subnets would not be practical.

---

### Post by uRock on 2012-05-10
Has nothing to do with ubuntu. Moved to *Networking and Wireless*.

---

### Post by redmk2 on 2012-05-10
> **wlraider70 said:**
> heres my problem.

I have two independent networks setup. Home and office. I have set them up following the same basic guidelines.

10.10.10.xxx
255.255.255.0

The router .1,   server is .2, and so on.


Now I want to VPN from 1 to the other, and I have read that VPNs can have some issue with the same ip configurations on both networks. 


Can I use a subnet to fix the issue?
My router will let me pick all 4 octets, but the lowest subnet I can do is 255.255.255.0

Any advice?

You have to have differing subnets.  The subnet mask only defines what is the network ID and what is the host number range.  In your case both networks are [COLOR="Blue"]**10.10.10.**[/COLOR]0 as defined by the subnet mask **[COLOR="Blue"]255.255.255.[/COLOR]**0.

You can't use 255.255.0.0 because it encompasses all 10.10.0.0 subnets of which 10.10.10.0 is one of 254 different subnets.  See below for binary (as the computer sees it)```

[COLOR="Blue"]11111111.11111111.11111111.[/COLOR]00000000 = 255.255.255.0 = subnet mask
[COLOR="Blue"]00001010.00001010.0000**[COLOR="Navy"]1010[/COLOR]**.[/COLOR]00000000 = 10.10.10.0 subnet
[COLOR="Blue"]00001010.00001010.0000**[COLOR="Navy"]1011[/COLOR]**.[/COLOR]00000000 = 10.10.11.0 subnet

```

if you were to use 10.10.10.0 as one and 10.10.11.0 (both with a subnet mask of 255.255.255.0) you would be fine.

---

### Post by redmk2 on 2012-05-10
> **alphacrucis2 said:**
> ...

Edit BTW we get this problem at work a lot as we have lots of VPNs to other parties who often have subnets that conflict with us and each other. We have no choice really but to use NAT as renumbering the subnets would not be practical.

Do you NAT one to 192.168.0.0 or ...?  I've never thought about that.  How do you do it (small tut maybe ???).

---

### Post by wlraider70 on 2012-05-10
I went ahead and renumbered my home network.
I guess I was hoping that there was a way to keep them numbered as they were, but thanks for the help.

---

