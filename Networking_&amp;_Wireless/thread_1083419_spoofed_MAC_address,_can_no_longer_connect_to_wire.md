---
title: "spoofed MAC address, can no longer connect to wireless networks."
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by sp0tz on 2009-02-28
So, I used the following set of commands to spoof my MAC address:

```
ifconfig eth1 down
ifconfig eth1 hw ether 69:69:69:69:69
ifconfig eth1 up
```
(//note: running ifconfig shows that my computer uses eth1 as its wireless connection for some reason.)

thats not actually the MAC address I used, I just threw in random numbers such that each digit was a valid hex value (0-9 or a-f). After doing this, I could no longer connect to my or any other wireless network (and I thank the testing gods for those unsecured ones named 'linksys' and 'netgear')

So, whats the deal? I ran Ifconfig from the terminal and verified that I had, in fact, changed the MAC address, so handshaking with the router shouldn't be a problem like it is with IP spoofing, right? Can you not just make up a mac address? Are there certain ranges that you can and cannot use? I appreciate any help.

---

### Post by puppywhacker on 2009-03-01
a normal oui-48 mac address should contain 6 hex-blocks, instead of 5

and stop using my wireless :)

---

### Post by sp0tz on 2009-03-01
Oh. Mistype. it was six blocks. Is 69:69:69:69:69:69 not a valid address? Why does eth1 carry my wireless connection instead of wlan0?



//edit


oh, snap.
[http://ubuntuforums.org/showthread.php?t=606939&highlight=spoof+mac](http://ubuntuforums.org/showthread.php?t=606939&highlight=spoof+mac)
restricted drivers may not like mac spoofing. Time to chuck this POS laptop out the window. (dell inspiron 1501, wireless card never had any OSS drivers.)

---

### Post by kakotako on 2009-03-15
I am having the same problem with Dell Mini 9. I can change the MAC ID fine but after that I can't pass the router's WPA authentication. I've done this successfully with the same router using Nokia N770. Could it be that the Dell stock driver is also limited?

---

