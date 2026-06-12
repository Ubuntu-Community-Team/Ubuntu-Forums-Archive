---
title: "Port Forward to VPN Client"
date: 2012-11-14
forum: Networking &amp; Wireless
---

### Post by ff8jake on 2012-11-14
Hello,

I've run into a bit of a puzzle and haven't had much luck finding a solution. Right now I am (sadly) connected to the net via Verizon 3G. They filter all incoming traffic so it is impossible for me to open ports to accept connections.

I currently have a linux virtual machine at linode.com, and the thought crossed my mind to install pptpd and attempt to do some iptables port forwarding. I have pptpd installed and my home machine connects happily. That said, here's some general info:

Server WAN IP: x.x.x.x on eth0
pptpd IP: 192.168.3.1 on ppp0
Client VPN IP: 192.168.3.100

To verify I wasn't going insane, I attempted some connections from the server to the open ports on the client, and the client does accept the connections via the VPN IP.

What I want to accomplish is this:

Internet -> WAN IP:Port -> Forward to Client VPN IP:Port

So for instance, if I had port 6000 open on my client, a person could telnet in to x.x.x.x:6000, and the server would catch that and forward it to 192.168.3.100:6000.

I have tried at least 20 different Googled up iptable configs and none have worked yet. Does anyone have any ideas, or perhaps even a totally different approach I might not be aware of? The goal here is to listen through a horribly firewalled connection, preferably both TCP and UDP traffic.

Thanks!

---

### Post by ff8jake on 2012-11-15
Just closing the thread, the issue has been solved. If anyone else needs to do something like this, you can find the solution I used here: [http://unix.stackexchange.com/questions/55791/port-forward-to-vpn-client]("http://unix.stackexchange.com/questions/55791/port-forward-to-vpn-client")

:popcorn:

---

