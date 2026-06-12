---
title: "Can't connect to network"
date: 2011-05-31
forum: Networking &amp; Wireless
---

### Post by a_banana on 2011-05-31
My roommate who has Ubuntu on his notebook could not connect to our router (D-Link DSL-684GT) yesterday. I switched it on and off and gave him a static IP address in Ubuntu's connection settings and it worked fine again. After that, my PC (Windows) could not use the connection properly which was fixed after turning off DHCP and giving me a static IP as well.  Today, the network on the Ubuntu machine did not work again while mine continued to be fine. Things I tried to get the Ubuntu machine to work. The behaviour this time was as follows:
Ubuntu said that a "network connection [was]established", but it did not manage to connect anywhere. DNS does not work, nor does even pinging our router and  reaching its web interface (using its IP address) and of course it does not show up in Samba on the other machine. Things tried unsuccessfully to get it working:


[LIST]
[*]Switching DHCP/static IP again
[*]Turning the router off and on
[*]Trying a different RJ45 cable
[*]Connecting it to two more routers. It still could not reach the other ones' web interfaces
[*]Resetting the router to factory settings
[*]Try and get a decent connection on a fresh Ubuntu OS (Live CD of 9.04)
[/LIST]
Any other suggestions for diagnostics?
Ubuntu downloaded an update for its network-manager on May 29th. Could that be a reason for the dysfunction? How can I get rid of it without uninstalling network-manager completely?

---

