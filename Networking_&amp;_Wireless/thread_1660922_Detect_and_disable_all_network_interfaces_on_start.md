---
title: "Detect and disable all network interfaces on startup"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by aschlosberg on 2011-01-06
Excuse my paranoia in advance.

I have up an installation of Ubuntu 10.10 on a USB key so that, if necessary, I have my own computer environment with me at all times.

As a security precaution I would like to automatically disable all network interfaces on startup. Given that I will be running on unknown hardware (hence unknown interfaces) can anyone suggest a method to, at startup, detect all such interfaces and close them?

ifdown came to mind but my knowledge of networking is essentially non-existent. I'm guessing that I'd also want to keep lo up.

Thanks for any help :)

---

### Post by grahammechanical on 2011-01-06
Have you tried to disable networking? Right click the Network Manager icon. Select Enable Networking and click it to remove the tick mark.

Also, go to System>Preferences>Startup Applications. Under the Startup Programs tab you will find Network Manager listed. Select it and click and Network Manager will not load at startup. Therefore you will not have any program that can connect to any networks.

Regards.

---

### Post by aschlosberg on 2011-01-07
I wanted to have this done automatically upon login without requiring any user input.

Solution:

I tried using ifdown but it will not always recognise interfaces because of the differing hardware platforms. Just using ifconfig by itself works though:

sudo ifconfig <interface> down

Now I just need to write a script to parse ifconfig -a and take all interfaces down.

EDIT: Here is the parser that ignores lo

```
sudo ifconfig -a | fgrep -v lo | grep -v '^\s' | grep -v '^$' | awk '{ gsub(/^([^\s]+).*$/, $1); print }'

list | ignore lo | clear lines starting with whitespace | clear empty lines | extract the interface
```

---

