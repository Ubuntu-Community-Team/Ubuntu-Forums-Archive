---
title: "Fragroute not working in Intrepid"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by sai438 on 2009-03-30
Hi,

When i'm trying to start fragroute in my Ubuntu 8.10 server, it is starting but when try to send some traffic it is not getting response. 

After examining through packet capture i found that it could able to fragment packets and send it to remote host and if remote host is sending response the packet is not reaching the application. 

I think this is a kernel issue. 

Fragroute is working fine with Ubuntu 7.04 server.

Please help me out of this issue.

Thanks,
sairam.

---

### Post by sai438 on 2009-03-30
From my observations, i found that fragroute is establishing a  tunnel on localhost for the traffic that is originated to a specific host. All packets to and from that particular host will parsed by fragroute. 

I think the issue us with the callbacks in the fragroute. callback used for fragmenting and sending packets to the remote host is working fine, but the callback used for receiving the packets is having issue. 

Can any one help me in sorting out the issue?

thanks,
sairam

---

### Post by sai438 on 2009-03-31
I downloaded the source code for fragroute from ubuntu packages, i saw a README under debian folder in which it was stated that for fragroute to work under Ubuntu Intrepid we need disable rp_filter flag under /proc/sys/net/ipv4/conf/all/ directory. 

For that please run this command:

echo "0" > /proc/sys/net/ipv4/conf/all/rp_filter

Fragroute worked after doing this change.

Please read the attached README file for more info.

---

