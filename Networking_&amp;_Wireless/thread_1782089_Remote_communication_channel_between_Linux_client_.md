---
title: "Remote communication channel between Linux client server socket Application"
date: 2011-06-14
forum: Networking &amp; Wireless
---

### Post by chouhan.raj1978 on 2011-06-14
hi,

I have one Linux gateway application written in C. Currently Linux Gateway behave just like server for the local communication(LAN).
 
LAN scenario is like that....
mobile device =====> search gateway======> small controlling electrical devices

Mobile Device send the command (method) to the gateway and gateway send the signals to the small controlling electrical devices so that we can control the electrical devices.

Command execution code written in Gateway.

Now we want to implement WAN version (Remote Communication) :
mobile device ==========> Linux server Application =====> search gateway======> small controlling electrical devices

I want to develop an Remoting Channel Application which can communicate to the Linux Gateway application remotely.

Linus Server have the public ip.
Linux Gateway have the private ip assigned by dhcp.
command (method) in the form of string.

So that mobile device send the command to Linux Server Application, Linux Server application search the appropriate gateway (in which the particular controlling device attached) & send the command to gateway, Gateway send the signal to controlling devices & vice versa for acknowledge.

So now Linux gateway behave just like a client but all the command execution code written in Gateway.

My Steps:
(1)Linux Gateway establish the connection with linux server.
(2)Linux Gateway wait for command (method) from Linux server. Linux server get the command from mobile device and just pass that command (method) to the Linux gateway.
(3)After establish the connection anybody (Linux Gateway and Linux server) can send the message to each other.

I want to develop a remote communication channel (code in Linux and C) or some mechanism between Linux Gateway and Linux server , so that After establish the connection anybody (Linux Gateway and Linux server) can send the message to each other.

what could be the fine tuned way to achieve the same? What are the other possible thoughts to implement the same thing?

Any thoughts / link/ sample application will be appreciated.

Regards,

RJ

---

