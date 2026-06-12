---
title: "dynamically swap IP address and monitor network connectivity"
date: 2013-02-10
forum: Networking &amp; Wireless
---

### Post by zmouse on 2013-02-10
I am trying to add networking support in an embedded system and am new to working in this area, so I would appreciate some help and direction. I have some requirements…

The program can be dynamically configured to switch between a DHCP address and a static IP address with gateway/subnet.  I’ve read about Network Manager and the ifup / ifdown commands, and it seems this would best be handled using ifup and ifdown commands called by the running application. To try this,  I commented out the call to start NetworkManager in the init scripts so that ifup and ifdown can completely manage the connections.  It seems to work ok and handle the scenario that I need. Does this sound ok so far?

The program also needs to dynamically monitor the network connectivity so it can determine how to handle some of its operations.  Is there a way for the running application to get a notification when there is a change in a network connectivity – up or down? Or does the application need to poll for network status? If it needs to poll, what is the recommended way to do this?

Thanks for any thoughts and recommendations.

---

