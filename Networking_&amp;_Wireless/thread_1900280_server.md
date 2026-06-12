---
title: "server"
date: 2011-12-25
forum: Networking &amp; Wireless
---

### Post by william_lane on 2011-12-25
Hello everyone, i have desided to convert my server to ubuntu server. For years i have been running opensuse but I like the fact that ubuntu tends to work better with vbox and it pretty universal, but it has given me a lot of snags and I have been logged in ssh for over a day try to get it to behave the way I'd like. I have the internet coming in on a static ip (eth1)"74.*.*.*" and need to route(Using NAT) it to a static network on (eth0)192.*.*.*. I do not want dchp I configured the internal network, It's static and functional a example is i can log in the main server with ssh and log into a box behind the server with ssh no problem, subnet gateway ips dns are all configured right on the internal network but I can't get this box to route(w/NAT) and port forward to a box inside.
any help with this would be appreciated.
I've been trying 
    IP Route 
    route  command
working with iptables and ufw but i am new to ubuntu server and the text i'm studing barley touchs on this.
Goal, 
route(w/NAT) 74.*.*.* on eth1 to 192.*.*.* to eth0/ port 8000 to 80 0n a internal box for apache2.
Thank you to anyone who responds I have been all over the internet and i have not found a explanation that didn't make it more confusing.

---

