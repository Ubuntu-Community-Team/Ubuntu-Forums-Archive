---
title: "Wired Connection stops working periodically"
date: 2011-08-06
forum: Networking &amp; Wireless
---

### Post by coolparth on 2011-08-06
Hello All,

I run a couple of machines as servers with Ubuntu Desktop with a Lamp stack on top in our office. One of these machines has a weird problem with relation to Wired Connections. Note that both these machines are always on. 

In case of one of these machines, the Network Connection stops working sometime in the night almost everyday. Once that happens we cant even ping the Machine on the Local network. If we actually connect a Monitor to the machine, we can see that the Wired connection shows as connected & both in Network Manager> Connection Information as well as IFconfig its seen to have an IP.  

If I unplug the cable & plug it back in the connection starts working again. The Machine has two onboard network cards.. i have seen this issue happen with both of them.. So i dont think its a hardware issue.. 

Also this problem does not plague the other machine. I have tried to figure out what happens when the connection breaks .. but the closing of the connection is not seen in vat/log/messages .. Whereas when i remove the cable & reconnect , i can see that in the logs as : 

> Aug  6 09:11:39 tws-in kernel: [69945.968461] e1000e: eth0 NIC Link is Down
Aug  6 09:11:44 tws-in kernel: [69950.730522] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Aug  6 09:11:44 tws-in kernel: [69950.730527] 0000:03:00.0: eth0: 10/100 speed: disabling TSO

Can you please help ? I have setup a ping report on the machine externally & it seems to go down everytime sometime in the night..  The timing isnt exactly the same everyday.. but its more or less around 9 PM to 11 PM at night..

---

