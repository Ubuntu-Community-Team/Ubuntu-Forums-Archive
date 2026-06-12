---
title: "Ping is not working"
date: 2012-08-15
forum: Networking &amp; Wireless
---

### Post by Skullalive on 2012-08-15
Hello everyone,

I'm running under ubuntu  12.04 LTS on my pc and I can't send an ICMP request (Ping) to my Mac laptop and vice versa. they are both connected on the same network via wifi, they are both able to go to the internet, but I can't ping one machine from another

I tried to check if there is any firewall on both machines. 
When I try to ping my Mac from my Ubuntu machine this is what I get  "Destination Host Unreachable"

and from my Mac to my Ubuntu I get "Request time out for icmp_seq 1"

May be someone already came up with this subject

thank you for your help

---

### Post by Skullalive on 2012-08-15
> **Skullalive said:**
> Hello everyone,

I'm running under ubuntu  12.04 LTS on my pc and I can't send an ICMP request (Ping) to my Mac laptop and vice versa. they are both connected on the same network via wifi, they are both able to go to the internet, but I can't ping one machine from another

I tried to check if there is any firewall on both machines. 
When I try to ping my Mac from my Ubuntu machine this is what I get  "Destination Host Unreachable"

and from my Mac to my Ubuntu I get "Request time out for icmp_seq 1"

May be someone already came up with this subject

thank you for your help


Here's some new info

My machines have a DHCP configuration, their routing tables seems to be normal since each of them can ping the router, and the router can ping them but they still can't ping each other. I also tried to clear each routing tables with the same results

any help ?

---

### Post by Skullalive on 2012-08-15
Finally I just got it all worked by rebooting my router and defining a new ssid for the wireless network

Sometimes things can simpler than you think  :D

---

