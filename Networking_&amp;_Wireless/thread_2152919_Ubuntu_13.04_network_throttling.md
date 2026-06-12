---
title: "Ubuntu 13.04 network throttling?"
date: 2013-06-09
forum: Networking &amp; Wireless
---

### Post by csete on 2013-06-09
I've recently upgraded my Ubuntu-based server machine to 13.04 and I'm noticing considerably slower performance on internet access from inside the firewall.  While the server machine reports 25M download via speedtest.net, machines on the private network show a maximum of around 2.5M download.  I'm not sure what may have changed or how to improve things. 

I have a semi-complex topology:

```

                                                +- Windows KVM
                                                |
Cable   <->  Vonage <-> Linux <-> Linux <-> Linux --+- Other private network nodes
Modem       Adapter      eth0       eth1       br0


```

I also have Shorewall enabled for firewall.

How can I figure out where the throttling is occurring?  What is the most likely culprit?

Thanks,
Craig

---

### Post by RichLouth on 2013-06-09
Try connecting your ubuntu machine, and then each device in turn, directly to the cable modem.

Also try turning off your cable modem and back on again. You know, for kicks :)

---

### Post by csete on 2013-06-09
I'm not having any trouble with download speed at the "edge" of my network, so I'm not concerned about the cable modem speed.  It is inside my private network that things seem to be slowing down more than I would expect.

---

