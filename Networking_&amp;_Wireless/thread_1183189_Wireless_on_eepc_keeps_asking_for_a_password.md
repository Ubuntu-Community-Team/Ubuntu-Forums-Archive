---
title: "Wireless on eepc keeps asking for a password"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by fr3dd on 2009-05-28
i there. i just install ubuntu. i was a windows user. i'm enjoying so far but the problem is that its not connecting to wireless conections with password.
if the connection has password just keeps asking for it. seems like doesnt record.

can anyone please help me? 
im using a eee pc. all works fine. if the network doesnt have a password also works good.

---

### Post by cariboo on 2009-06-09
Moved to Networking & Wireless as a seperate question.

---

### Post by superprash2003 on 2009-06-10
are you using WEP? you may be trying with the wrong encrytion type , try 64bit,128bit etc

---

### Post by PoopyTheJ on 2011-01-02
Same issue here, I know the password is correct, but the Network Manager keeps asking for the password and not connecting. Not seeing any issues when looking at the router, so it's seemingly got to be ubuntu. BTW this network connection worked fine for the past year.

---

### Post by vilunki on 2011-01-02
Hello everyone, same problem here.

Story:
Bought EeePC 1001 px about a month ago to take with me on a trip. Tried 10.10 netbook edition from flash drive - everything I tried seemed to work perfectly. Crapped windows and installed netbook edition.

Found out that mic's not working and can't solve the problem (even with support from this forum). Upgraded ubuntu about a week ago and now also having problems accessing USB flash drives. Also lost internet connections completely (which worked fine at the beginning).

This sucks and time to time even regret crapping the windows. Propably will install 10.04 (which has worked perfectly at home-laptop). But still would like to get connection to internet from my netbook, would make easier to make an installation usb flash drive etc.

So the question:
- Netbook doesn't make any connection to internet. Wireless keeps asking the password again and again, and when sticking in the cable and clicking on wired network, it only tells that wired network is disconnected. Can anyone help me?

---

### Post by PatchesTheCaveman on 2011-01-02
Hey guys, go to Applications > Accessories > Terminal and run the following commands, pressing Enter after each one:
```
lspci -v
ifconfig -a
sudo iwconfig
```

Then copy and paste the output to a new post on this forum.  It gets really confusing when we have to troubleshoot different peoples problems in one thread.  Even if they seem similar, more times than not they're totally unrelated.

---

