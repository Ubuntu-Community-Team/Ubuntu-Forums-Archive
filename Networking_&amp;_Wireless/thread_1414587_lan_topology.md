---
title: "lan topology"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by zander1013 on 2010-02-23
hi,

i am adding a new server to my lan. i have a question about the topology.

right now i have the modem connected to server1.

server1 is connected to a wireless router.

my question is where should server2 connect to the network?

both server1 and server2 will have their own ip address.

should i add a switch between the modem and then connect server1 and server2 to the switch?:confused:

both servers are linux. server1 is debian lamp, server2 is ubuntu 9.10 server. i would like to experiment with server2 as ubuntu lamp or cloud configurations.

(internet)
|
switch ---- server2 (new server or cloud)
| 
server1
|
(wireless router)

(wifi computer1), (wifi computer 2), ....



what are the other topologies with this hardware manifest?

please advise.

---

### Post by zander1013 on 2010-02-26
the solution is to use the wireless adapter on the laptop server with the current configuration.

---

