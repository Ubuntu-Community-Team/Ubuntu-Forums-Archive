---
title: "intel 4965 AG(N) iwlagn freezes up"
date: 2009-09-11
forum: Networking &amp; Wireless
---

### Post by threetwoone on 2009-09-11
I've been getting a very strange problem with my wireless when connecting to a wpa-psk network (I haven't gotten a chance to test it on other network encryptions).  I am connected manually, network-manager was giving me trouble so I removed it.

At somewhat random times (but almost always when downloading a file) my internet will stop working.

[LIST]
[*]It is not an issue with the router because other computers are not having this problem
[*]I remain fully connected to the network (verified on my end and the router's end)
[*]I am unable to ping anything and when trying to ping the program will go unresponsive for a about a minute then it will comeback with a could not be found error
[*]my system logs show nothing of interest/concern
[*]running wpa_supplicant with the -dd parameter shows no errors
[*]after a could of second to a minute everything will be fine again
[/LIST]
I have no idea why this is happening but the only thing I can think of is a driver issue and according to [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel) iwlagn was updated on Wednesday.  However, I have not seen anyone else with this problem.  I've only been using this router for a few days so that might be part of the issue.

Edit:
I believe I have fallen prey to IPv6 troubles.  Still looking for a solution.

Any help would be appreciated

---

