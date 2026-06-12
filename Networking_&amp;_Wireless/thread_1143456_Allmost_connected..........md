---
title: "Allmost connected........."
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by jitsonfire on 2009-04-29
Hi, I very new to ubuntu.
My isp provides me with a cable connection(should be pppoe).
In my network settings it shows me no connections.
When I type in ifconfig it shows me lo,eth0 if i am not conneced to internet.
What I do is type sudo pppoeconf (which should be my connection type).It shows me screen "I found ethernet device eth0 then looking for pppoe ,modify /etc/ppp/peers/dsl-provider/ and so on ,which you all must be knowning.
Latter asks me for the Username and password.
If I am lucky when I type ifconfig again i get to see ppp0,eth0,lo 
Which means I am connected to internet.
I do this on trial and error basis.Some times there is hit at first go or 5 and some times I shut it down.
Thks in advance................

---

### Post by coffeeaddict22 on 2009-04-29
Hi,
Welcome to Ubuntu!
Can you run the commands you have already, but post the output back to the forum; it means people can confirm what you think you're getting from the results.  Otherwise, we spend all day fixing something that isn't the actual problem...

In particular, ```
lshw -C network
```
```
sudo ifconfig
``` and if you're running the network manager, 
```
nm-tool
```
should give enough detail.

Having ppp show up as one of your interfaces probably isn't quite where you want it.  Are you on a wireless link at all or is it all cabled?
Are you running Ubuntu/ Kubuntu/ Xubuntu?  Are you using network manager or wicd?

---

### Post by JK3mp on 2009-04-30
Should be an easy setup routine in nm-applet for gnome, not sure, believe KDE uses KPPP, and not sure as far as many others.

---

