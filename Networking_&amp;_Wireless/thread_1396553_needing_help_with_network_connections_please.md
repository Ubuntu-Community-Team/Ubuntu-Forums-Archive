---
title: "needing help with network connections please"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by jayze on 2010-02-02
every so often network manager tells me i have a "link local network that is incompatible with the system" and disconnects it for me....in the meantime it sneaks back and non of the network tools will allow me to modify. its a bit tiresome. has anybody got any ideas please. thanks:cool:

---

### Post by Daveski on 2010-03-04
What is the configuration of your network? Are you just plugging 2 machines together, or do you have a broadband router etc. ?  Is this Wireless or wired?
I think you need to be a bit more specific about what your situation is and what you are trying to do.

Thanks.

---

### Post by jayze on 2010-03-04
Its a link local by virtue of the geography (only other option would be satellite)...my isp uses the LAN connection...i have an external router with the wireless disabled. I am not trying to do anything in patricular...but just understand why an ubuntu system would use a windows network...in the first instance...my ip does not use a proxy by the way

---

### Post by Daveski on 2010-03-05
So you are cable connected to your router? I would expect the router to be configured as a DHCP server issuing local LAN IP addresses to any machine plugged into the network. I thought that link-local network addresses were only assigned to a network adapter if it does not get a DHCP assigned address:

[https://wiki.ubuntu.com/ZeroConfNetworking]("https://wiki.ubuntu.com/ZeroConfNetworking")

Can you open a terminal and post the results of this command:

```
ifconfig
```

do this again when you get the message and see of anythng has changed.

---

### Post by jayze on 2010-03-18
thanks for the individual messages.....I will respond when I can...in the meantime it might help some or any of you to read my conclusion to my other thread on the same issue (again under networking)

---

### Post by zeny123 on 2010-03-18
> **jayze said:**
> every so often network manager tells me i have a "link local network that is incompatible with the system" and disconnects it for me....in the meantime it sneaks back and non of the network tools will allow me to modify. its a bit tiresome. has anybody got any ideas please. thanks:cool:

ya this problem is very tiresome .If i will got some detail  definetly i will post it on your threads. you also get some information **_"Microsoft trouble Shooting_" **on[B]
[www.outlooktroubleshooting.com:D]("http://www.outlooktroubleshooting.com")
[/B]

---

### Post by jayze on 2010-03-18
:confused: but shukria anyway

---

