---
title: "Why do I have to type ifup to start my network interface?"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by Haleon on 2009-12-29
Hey guys,

I have a NIC (eth0) that is configured with a static IP address.  After a system reboot, I have to type sudo ifup eth0 to get the thing to work.  Once I do that, it works beautifully, but I would like it to start on its own.  How can I make sure that this happens?  Thanks again for the help!

---

### Post by Project PWNED on 2009-12-29
You can edit /etc/network/interfaces and make an entry in there so when you reboot, you don't have to do this anymore. Please paste the output of 

```
ifconfig
```

I will write you up exactly what to put in there.

---

### Post by iponeverything on 2009-12-29
> **Haleon said:**
> Hey guys,

I have a NIC (eth0) that is configured with a static IP address.  After a system reboot, I have to type sudo ifup eth0 to get the thing to work.  Once I do that, it works beautifully, but I would like it to start on its own.  How can I make sure that this happens?  Thanks again for the help!

add this line to your interfaces file:

```
auto eth0
```

---

### Post by Iowan on 2009-12-29
Do you currently have the interface configured via Network Manager? Does the interface have the "Connect automatically" checkbox checked?

---

### Post by Haleon on 2009-12-29
Thanks for all the help, guys.  The auto eth0 line to the interfaces file fixed it.  Thanks again for the responses. :)

---

