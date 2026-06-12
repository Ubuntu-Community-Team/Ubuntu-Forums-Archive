---
title: "DHCP Server Range=1 Question"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by BCven86 on 2009-11-06
I have a question about setting up a dhcp server, specifically on setting up /etc/dhcp/dhcp.conf. I want to set the range of ip addresses to hand out to equal 1, but I want the server to be able to hand this ip address to multiple computers. 

i.e.
```

subnet 10.77.65.0 netmask 255.255.255.0 {
   range 10.77.65.2 10.77.65.2;
   default-lease-time 600;
   max-lease-time 7200;


```

The problem is that when the server hands out a lease to the first computer, when I unplug and reconnect to a second computer the server will not hand out the same ip address and the second connection will not be made. I need a way for this same ip address to be handed out to both computers without having to wait for the previous dhcp lease to end. I have tried setting the lease time to very short (i.e. 10 seconds) which seems to work, but I don't know enough about dhcp to know the disadvantages of this solution. The only problem I can forsee at the moment is that the /var/lib/dhcp/dhcp.leases file will get huge. Can someone help me with this solution? Will my solution work? Is there a better solution?

Thanks a lot!
Bob

---

### Post by Iowan on 2009-11-06
You knew someone was gonna ask it so...
Why? One DHCP address to be shared between computers? 
Looks like what you did should work...
BTW, you could also crank down the subnet mask to 255.255.255.252 to allow only two hosts (.1 and .2)

---

