---
title: "Slow wireless problem solved Ubuntu 9.10"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by Perry123 on 2009-12-07
This is not intended to be a dicussing thread because it appears I have fond the solution to my problem but Im sure other Ubuntu novices are likely to experience similar problems so I thought I'd post it where it would be easy to find and of use to others....not least because it's taken me about 3 days to find to find the solution.

My problem was very slow wireless for anything except Google. Apparently my problem was caused by IPV6 and this can disabled in Firefox.



[LIST=1]
[*]Type** about:config** in your address entry bar (in Firefox) press Enter
[*]Type "ipv6" in the filter bar
[*]Change the value of "network.dns.disableIPv6" to **true** - I did this by clicking on **false**
[/LIST]
This can easily be reversed if it does not work for you.

This worked a treat for me and everything seems fine at the moment.

---

### Post by coffeecat on 2009-12-07
If you find that disabling IPv6 in Firefox in 9.10 speeds up your internet browsing, it is possible that you have been hit with this bug:

[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757)

If this is indeed so, it won't be a wireless issue - a wired  connection would have been equally affected.

> **Perry123 said:**
> This worked a treat for me and everything seems fine at the moment.

Again **if** this bug is affecting you, I'm afraid that everything won't be fine. You'll get DNS resolution delays and possible timeouts when other parts of the system - such as the update manager - try to access the internet.

I hope for your sake that none of this is true, but I thought I'd post this to warn you if you do find problems elsewhere in the system.

---

### Post by nateperson on 2009-12-07
Yeah, this work around helps firefox and I can live with the slowdowns in the other network connectivities till a better work around or actual fix comes down the pipes...

---

### Post by marcoftheknight on 2010-05-06
Ok so I just did what you said and my internet is working like 5X faster thats kinda scary I didnt even know that a firefox setting like that could cause that type fo problem it's so random. Could anyone explain how this works why it was slowing down my internet and how im super lucky I ran into this thread that liberated me from hours and hours of trouble shooting.

Thanks again ubuntu people rule

---

