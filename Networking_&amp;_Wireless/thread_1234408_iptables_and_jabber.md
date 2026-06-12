---
title: "iptables and jabber"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by syrgak on 2009-08-07
Hi everybody,

I hope you're guys doing well. :)

Last few hours I spent trying to get my iptables work.

Preface: I've got two PCs in our local network. First one with windows installed and second is an Ubuntu desktop (9.04) as a server. I have apache2 working on ubuntu and it listens to 80 and 5222 ports. 

Right now I am testing javascript jabber client from windows machine against the server (ubuntu), but the problem is I cann't reach 5222 port because of a firewall in the LAN (which of I have no control).

However I'm able to reach other ports on the server such as 21, 22, 23 ...etc. So I've decided to connect to an available port and make redirect the port to the desired 5222. Doing this I used iptables:

I've tried rules one by one in the list below, unfortunately none of them doesn't seem to work:

# iptables -A INPUT -p tcp --dport 23 -j ACCEPT
# iptables -A INPUT -p tcp --dport 5222 -j ACCEPT

# iptables -t nat -A OUTPUT -o eth0 -p tcp --dport 23 -j REDIRECT --to-port 5222

# iptables -t nat -A PREROUTING -p tcp -i eth0 -d 127.0.0.1 --dport 23 -j DNAT --to 127.0.0.1:5222

# iptables -A PREROUTING -t nat -p tcp --dport 23 -j REDIRECT --to-port 5222

Before applying iptables rules I can connect to 23 port of the ubuntu server from my windows machine using telnet and get telnet's standard greeting message, but after the port becomes unavailable (neither for the telnet or jabber servers):

# telnet 192.168.0.32 23
Connecting To 192.168.0.32 ... Could not open connection to the host, on port 23:Connect failed

I was wondering is it possible to redirect/forward one port to another within the same machine?

Any help would be greatly appreciated.

PS. Jabber server based purely on PHP and I cannot use another port on the server because of security reasons. (to open a port below 1024 one needs to be root but apache's child processes run as www-data only)

Thanks,

//Drupal developer

---

### Post by syrgak on 2009-08-07
solved.

---

