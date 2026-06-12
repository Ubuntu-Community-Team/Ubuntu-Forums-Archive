---
title: "How to refresh IP address????"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by glenngds2007 on 2008-12-16
The way my network is set up is that my router is a little schizo.  If my internet connection goes down for even one second--I have to reset my router and when it reboots it can assign any of 50 IP's to any computer in any order.  What I need to know is how to get my computers to refresh their IP without rebooting? All my computers have Ubuntu 8.10 installed.

---

### Post by gettinoriginal on 2008-12-16
Sorry, wrong thread

---

### Post by gettinoriginal on 2008-12-16
Ok, now this problem.  I only unplug my router to change mine, but check out this thread to see if there is anything that will help you:  :p

[http://ubuntuforums.org/showthread.php?t=541887](http://ubuntuforums.org/showthread.php?t=541887)

---

### Post by gTinker on 2008-12-17
[QUOTE=glenngds]The way my network is set up is that my router is a little schizo.  If my internet connection goes down for even one second--I have to reset my router and when it reboots it can assign any of 50 IP's to any computer in any order.  What I need to know is how to get my computers to refresh their IP without rebooting? All my computers have Ubuntu 8.10 installed.[/QUOTE]

The title of this post is misleading, what you have described is a situation which exists because of the way that your router is configured, not something about Ubuntu. You may have problems with your Ubuntu installs but they aren't causing what you described.

The DHCP server only issues 50 different IPs because it is configured to issue 50, you could drop that down to the number you need. In addition, most router/gateways can always hand out the same IP to a given computer by being configured to hand them out by the MAC address of the computer's interface card, so they would each get the same IP each time, similar to static addressing. This should all be covered in the router documentation.

As to this question (which appears to be unrelated to the rest of what you are asking:
[QUOTE=glenngds]
What I need to know is how to get my computers to refresh their IP without rebooting?[/quote]

Down the interface and bring it back up if it is set to "auto" DHCP. You might try dhclient to ask for a lease if the interface isn't set to "auto".

---

### Post by Pvt_Ryan on 2008-12-17
you can also manually type:
```

dhclient eth0

```

Personally I would configure your router to use MAC addresses to assign IP address (DHCP address reservation) This way you can make sure all your IP addresses are the same every time.

---

