---
title: "Please help in Network Manager"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by Cyber Junior on 2010-12-28
I may wrong in posting to the other thread ... 

```
http://ubuntuforums.org/showthread.php?t=1654486
```

So let me quote here,

> Hi to all !

I have a prob at my Network Manager - this is caused by my modem. Being  Lack of the electricity unstable, I connect my aDSL modem with UPS. But  my modem restart when Step-Up Generator Relay works also UPS can't stand  at that time. 
The major problem is to change the release time of Network Manager - I  would like to extend the release time until connect to the ISP. (The  default release time is not enough that's why.)
Please explain me how to.

Happy New Year to you all !!! :KS

With much regards,
Cyber Junior

I really need that's helped.

---

### Post by grahammechanical on 2010-12-29
I do not understand your explanation of your problem. Please may I describe the problem in my own words? It will help me understand.

In the area where you live the electrical supply is unstable. You have an UPS and a Step-Up generator. When the power supply fails the modem switches off and Network Manager displays a Disconnection message. When the Step-Up generator starts providing power the modem reboots but Network Manager does not reconnect to the modem. Am I correct?

Is your wireless connection set up to Connect Automatically? Right click the Network Manager icon and select Edit Connections. Select the wireless tab and select your wireless connection and click Edit. Put a tick mark against the box marked Connect Automatically.

When the modem reboots it will broadcast (send out) a signal. Network manager will detect this signal and re-establish a connection. I think that this will happen.

If you are using an UPS then the modem should not switch off. What kind of computer are you using? Is it connected to the UPS? Is it a laptop? If it is laptop then the problem may be caused when the laptop switches from mains power to battery power.

If this is not helpful, then someone else may offer advice.

Regards.

---

