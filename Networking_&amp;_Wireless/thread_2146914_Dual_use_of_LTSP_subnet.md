---
title: "Dual use of LTSP subnet?"
date: 2013-05-20
forum: Networking &amp; Wireless
---

### Post by morphyrichards1 on 2013-05-20
A general - is it possible? question and perhaps more usefully, "how difficult would it be to ..."

If I have a Edubuntu LTSP server that's serving a collection of raspberry pi that can boot into "berryterminals" or into standard "raspbian". Would the same sub-net work for those raspberry pi's in either mode?

That is to say - a raspberry pi boots into a thin client while at the same time another which is connected to the same NIC on the LTSP server via a switch boots into Raspbian and still has standard network connectivity?

Something like this

```

internet --[edubuntu ltsp server] --(switch)---[berryterminal1]
                                           |--[Raspbian1]

```
Thanks

---

