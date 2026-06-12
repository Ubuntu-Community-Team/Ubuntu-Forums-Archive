---
title: "How to make my 4G usb activate as backup connection"
date: 2012-05-16
forum: Networking &amp; Wireless
---

### Post by JLouie on 2012-05-16
Is there any way to make my 4G usb device to be used as a backup connection when my primary cable connection goes down automatically? Any way to set this up through terminal? This is for my small home server box. I'm guessing there must be some kind of script or program. Thank you in advance. Always been a huge fan of Ubuntu, but new to the forums.

---

### Post by sanderj on 2012-05-17
I assume you googled for this and you didn't find anything?

If so, I can only give you some concepts:

With the "ip route" command you can see and you can define the default route. So you can switch between your fixed and 4G connection.
With "ping -I <interface> 8.8.8.8" you can ping a host from a certain interface.

So, combining these commands, I would make such a script (attention: this is pseudocode):

```
while ALWAYS:
   ping 8.8.8.8 from fixed interface
   if unreachable:
      ping 8.8.8.8 from cellular interface
      if reachable then switch default gateway to cellular interface
   else set fixed as default gateway (if wireless was set)
   wait 5 seconds

```

HTH

---

