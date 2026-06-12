---
title: "Wifi Latency/Delay with my Broadcom 4312 on a Dell D830"
date: 2011-01-08
forum: Networking &amp; Wireless
---

### Post by mattafact on 2011-01-08
Hi, first post here but I did search!

I just put 10.10 on my D830 and I love it except for a delay when I'm using the internet.  When I click on a link while surfing the web it takes about 13 seconds before it responds.  After that it works just fine.  

My Windows 7 PC and my Macbook Pro don't do that so I'm guessing it has something to do with Ubuntu.

I'm still pretty new to Linux so any help is most appreciated.

Thanks,
Matt

---

### Post by FloobenShnooben on 2011-01-08
I am assuming it is just the Broadcom chip. I personally have had troubles with these, but nothing this bad. I personally am not sure how to fix this, but maybe a search on Google or something on "Broadcom 4312 Delay Ubuntu 10.10" for example.

---

### Post by mattafact on 2011-01-08
I've been searching Google and a lot of the replies are still a bit beyond me.  Other than the wifi issue I absolutely love Ubuntu.

---

### Post by TBABill on 2011-01-08
Have you disabled IPV6 in Firefox?

In the URL block up top, type ```
about:config
```

Then search for network.dns.disableIPv6 in the filter block. Set the option to TRUE by double clicking on it.

---

### Post by mattafact on 2011-01-08
> **TBABill said:**
> Have you disabled IPV6 in Firefox?

In the URL block up top, type ```
about:config
```Then search for network.dns.disableIPv6 in the filter block. Set the option to TRUE by double clicking on it.

That did it!!!

Thanks so much!

---

