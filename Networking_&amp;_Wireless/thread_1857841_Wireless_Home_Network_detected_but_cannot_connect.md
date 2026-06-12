---
title: "Wireless Home Network detected but cannot connect"
date: 2011-10-11
forum: Networking &amp; Wireless
---

### Post by nilrezei on 2011-10-11
As the title says it. I am trying to connect to a Windows 7 host desktop with a Ubuntu laptop client. Other Windows laptops can connect to this network.

The Network Manager detects my home network; however, the home network icon does not look like a wave antenna (like other vicinity networks appear). It has a small pc monitor symbol. When I click it, nothing happens.

If I click other networks (those with icons shown like antennas) it tries to connect.

I've searched the forum and Google but nothing concrete on this. Any help? Thanks in advance.

---

### Post by JSchultheis on 2011-10-11
> **nilrezei said:**
> As the title says it. I am trying to connect to a Windows 7 host desktop with a Ubuntu laptop client. Other Windows laptops can connect to this network.

The Network Manager detects my home network; however, the home network icon does not look like a wave antenna (like other vicinity networks appear). It has a small pc monitor symbol. When I click it, nothing happens.

If I click other networks (those with icons shown like antennas) it tries to connect.

I've searched the forum and Google but nothing concrete on this. Any help? Thanks in advance.

I would like to make a humble effort in trying to help, but I am unclear of what exactly I am reading, or rather, what it is you mean to express. Can you take a screenshot (should be under ```
Application>Accessories>take screenshot tool
```then in a reply, scroll below 'message' box to 'manage attachments' and upload.


Otherwise, let us try another method.
Open:```
System> Administration> Windows Wireless Drivers
``````
Configure Network>Wireless
```

Can you see your network there?

---

### Post by nilrezei on 2011-10-11
> **JSchultheis said:**
> I would like to make a humble effort in trying to help, but I am unclear of what exactly I am reading, or rather, what it is you mean to express. Can you take a screenshot (should be under ```
Application>Accessories>take screenshot tool
```then in a reply, scroll below 'message' box to 'manage attachments' and upload.


Otherwise, let us try another method.
Open:```
System> Administration> Windows Wireless Drivers
``````
Configure Network>Wireless
```Can you see your network there?

Thanks for your intention to help.

I can't do screenshot. There is no "Windows Wireless Drivers" option appearing in my System -> Administration...
I'm using Ubuntu 11.04 (Natty) 32 bit

...........................................

I repeat, in hope I can make things clearer:

1. I have a Windows 7 desktop (the host) that has a wireless ad-hoc working connection. It is working, since any other Windows laptop (the client/s) can connect to it.

2. I have a laptop with Ubuntu 11.04 on it. This Ubuntu client sees my network but cannot connect to it. 
When I am saying "cannot connect to it" I mean it doesn't even try, no sign of any connection attempt, no rotating circle is happening, nothing. It is just like never clicking...

If I attempt to connect to other detected wireless networks, it tries to connect to them this time. A small rotating circle of connection in progress appears...

Strange aspect (thought it might be important): The other wireless networks detected, their icons look like antennas (in "V" letter shape, but with waves), while my home network icon looks like a computer monitor (square shape).

...........

EDIT: The square shape must be particular to ad-hoc networks, while the antennas icons to routers... Nevermind... 
It seems there are so many bugs related to wireless connection when it comes to Linux, and too many in particular regarding Atheros...

---

