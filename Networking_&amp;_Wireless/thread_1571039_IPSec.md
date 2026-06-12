---
title: "IPSec"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by observer1 on 2010-09-09
[FONT=Verdana][SIZE=2]Hi!

I am trying to establish an IPSec connection to my homeoffice router using ShrewVPN/IKE.[/SIZE][/FONT] [FONT=Verdana][SIZE=2]
While it works running Windows XP - exactly the same VPN-profile won't work in Ubuntu 10.04 32Bit.
As soon as the tunnel is established, I won't be able to ping or access anything.
I have already seen that there is an entry in the Shrew FAQ ([http://lists.shrew.net/mailman/htdig/vpn-help/2008-November/001827.html](http://lists.shrew.net/mailman/htdig/vpn-help/2008-November/001827.html)), however even using 
```
sudo tcpdump -n icmp 
```I cannot see any ping going outbound (As long as the tunnel is established).
I also tried to uncomment net.ipv4.conf.all.rp_filter & net.ipv4.conf.default.rp_filter in the /etc/sysctl.conf and set both to 0. However, this didn't work out either.
[/SIZE][/FONT] [FONT=Verdana][SIZE=2]I do not have enough Linux/Ubuntu networking knowledge to retrace this error any further and would be very glad if anybody had any idea or hint.

Thanks a lot in advance.
[/SIZE][/FONT][FONT=Arial][SIZE=2][FONT=Verdana]Greetings[/FONT]
[/SIZE][/FONT]

---

### Post by puppywhacker on 2010-09-09
If you connect the IPsec tunnel your network adaptor and its ipaddress will change. if you do an tcpdump without a specific interface it will take the default eth0 where only IPsec packets will be visible, tracing the IPsec interface may show more. But if you're IPsec tunnel is established the default gateway may also have been changed (or not) and that means that you have to update your routing tables

look at the following commands before and after you have connected the tunnel
```
sudo ip link
sudo ip addr
sudo ip route
```

---

### Post by observer1 on 2010-09-09
Thanks for your reply/help. 
It seems that my problem was to not RTFM properly. 
Uncommenting net.ipv4.conf.all.rp_filter & net.ipv4.conf.default.rp_filter in the /etc/sysctl.conf and set both to 0 is indeed the solution - when you do it right #-o

---

### Post by EyesOnFire on 2010-09-20
I have been trying for months to get this to work. I finally read the same thing on lists.shrew.net. 

Stupid sysctl.conf and your net.ipv4.conf entries! I blame the Communists.

---

### Post by Darley Stephen on 2010-09-25
Hope this helps
[http://x2d3d.com/res/darley.stephen/IPSEC.pdf](http://x2d3d.com/res/darley.stephen/IPSEC.pdf)

---

