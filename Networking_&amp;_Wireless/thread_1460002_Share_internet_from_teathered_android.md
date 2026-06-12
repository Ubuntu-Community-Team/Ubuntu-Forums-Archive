---
title: "Share internet from teathered android"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by zephyrcat on 2010-04-22
I have a Droid Eris teathered over USB. I would like to share the the internet connection over WiFi. Currently, I forward tcp:8080 to tcp:8080 with the android tools. (I'm using the proxoid application.) Then I set firefox to use localhost:8080 as a proxy.

How can I share this connection over WiFi?

---

### Post by computer13137 on 2010-04-22
I have never tethered a phone before in my life - nor have I ever done it on Ubuntu.  But, if the phone creates an interface, like eth1 or something, that is just a normal Internet interface, then setting up a routing script to forward the traffic, using your netbook as the default gateway, shouldn't be difficult.

However, I think sharing your cellular Internet over a WiFi connection is about the most unstable and least reliable thing I could ever imagine doing.

If your Android is creating an interface, you can probably amend this tutorial to suit your needs: [http://www.yolinux.com/TUTORIALS/LinuxTutorialIptablesNetworkGateway.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialIptablesNetworkGateway.html)

If it does not... then that brings us to the age-old question I've had for a year or so. "Can I forward all my Internet traffic through an SSH tunnel?"  And the answer I've always gotten is that it's not possible. 

If your Android creates an interface and you need help setting up a Linux router, I can certainly help you with that.

Cheers,
Kirk

---

