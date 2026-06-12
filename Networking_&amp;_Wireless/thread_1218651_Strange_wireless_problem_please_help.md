---
title: "Strange wireless problem please help"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by dmbminaret on 2009-07-20
I have a really unique problem that I can't figure out, any help will be appreciated.

Up until the weekend I had adsl modem to wireless router with a mixture of windows and linux mint (ubuntu) machines working fine. On the weekend I installed clark connect in gateway mode on a server and changed the router to be an access point only. All seemed to be working fine for a day with the wireless until my laptop would no longer open a webpage while logged into linux. If I boot into windows, works fine as do the other windows machines while the 3 linux machines all present the same problem with 3 different wireless drivers.

I did the network restart command (sudo /etc/nist.d/networking restart) (sorry can't remember exact) which worked for a little while then I cleared out all the keyring and passwords stored and deleted the wireless connection settings in network manager to no avail. 

I thought it had something to do with network manager and it holding an incorrect wep key. Everytime I go to edit the connection, it has a long hexidecimal key in there instead of the 7 digit wpa key, but 1 machine has wicd on it and is clearly the correct key. The other strange thing is if I turn the key off at the access point, they work. So it's somewhere between the wireless security of the access point and the networking in ubuntu.

It was working strangely enough, before clark connect and changing to access point, with same key. Ethernet works fine and as far as I can tell it is the latest version of network manager. I have tried manual connection and dhcp etc and all the normal stuffing around but now am stumped.

So to summarise, wireless security if fine - windows is working. Network manager is fine - ethernet and wireless work without security. Wireless driver is fine - 3 different machines, 3 different wireless drivers and all connect and can ping the gateway, just no further. I think clark connect is coincidence, it's gotta be wireless security to ubuntu connection not being friendly.

Thanks all for any ideas to try.
Russ.

---

### Post by dmbminaret on 2009-07-27
This is now fixed. For those who google their way here for a similar problem, make sure your gateway is 192.168.1.1 and wireless switch 192.168.1.2 or similar but not the same. Try to use one wireless encryption eg AES or TKIP not the option of both. Last but not least, this is the big one, make sure the cable is not in the 'internet in' port but rather just a normal port on the router. I didn't know this as I had never had to do this setup before. Seems weird that windows still worked, must be some difference in resolving stuff there.

---

