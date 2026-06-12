---
title: "Configuring a bridged connection"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by princeofindia on 2010-04-22
Can anyone please tell me how to configure a bridged connection in where we are required to enter username and password.I am currently using PPOE type connection of my modem(A Nokia siemens  ADSL modem).:confused:

---

### Post by spiky001 on 2010-04-22
what do yo mean by a bride connection?

---

### Post by Iowan on 2010-04-22
> **spiky001 said:**
> what do yo mean by a [COLOR="Red"]bride[/COLOR] connection?Bridged?

There's a section in [here]("https://help.ubuntu.com/8.10/serverguide/C/network-configuration.html") on bridging - but it's a couple of versions old (8.10).

---

### Post by computer13137 on 2010-04-22
It sounds to me like you are trying to setup a Linux router as a gateway to a DSL (or some other PPPOE) style Internet connection...

What I would do, is get the system connected to the PPPOE, I have never had a PPPOE connection so I'll not be of any use helping you to do that.  But once it's connected to the Internet, it should be a simple matter of packet forwarding to get the routing portion to work.

In short, don't overthink the router part. You need to get connected to the PPPOE first. Once your Ubuntu box has an Internet interface, sharing that connection with the rest of your house is simple.  I don't think it's called bridging, I think it's packet forwarding.  But the terms aren't really what's important.  Please correct me if I have misunderstood what you are trying to do... I will remain subscribed to this thread in case there's anything I can do assist you.

You may find this tutorial useful, if I understood what you're doing right. It discusses how to do it with a PPPOE connection as well.
[http://www.yolinux.com/TUTORIALS/LinuxTutorialIptablesNetworkGateway.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialIptablesNetworkGateway.html)

Cheers,
Kirk

---

