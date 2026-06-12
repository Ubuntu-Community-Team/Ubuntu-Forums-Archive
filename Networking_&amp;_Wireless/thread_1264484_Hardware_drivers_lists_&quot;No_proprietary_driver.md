---
title: "Hardware drivers lists &quot;No proprietary drivers are in use on this system&quot;"
date: 2009-09-12
forum: Networking &amp; Wireless
---

### Post by verbis on 2009-09-12
So I know I'm looking for bcm4306. I seem to be having issues.
I wasn't able to browse for a minute even with an ethernet connection until adding a dns server to the list. I don't even know what a dns server is.

Anyway, clearly I'm a newb.
Thank you!

---

### Post by keplerspeed on 2009-09-12
Ok slow down and work through this with us.

Your wireless card: a broadcom bcm4306. Please confirm this by entering this command to the terminal:
```

lspci | grep Network

```

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)

As you can see we need the revision of the card. The above command should give us this.

And before you start changing things, please do an update, as in go to system>admin>update manager. Then try hardware drivers and enable the driver. The driver will ONLY appear after an update. This means you will need to get a wired connection for a bit....

---

### Post by Earl_Maroon on 2009-09-12
A DNS is a Domain Name Server. It is important as it provides the links from human-usable URLs like [http://www.google.com/](http://www.google.com/) into IP addresses that computers need to find websites like 209.85.229.104. Your IP (service provider) should have a DNS and you should have the IP address of it printed somewhere in the information they gave you when you signed up with them.

---

