---
title: "Failed to registered hostname in DNS"
date: 2006-01-17
forum: Networking &amp; Wireless
---

### Post by mlsalcedo on 2006-01-17
I just recently installed ubuntu, everything was smooth but my I cannot resolve my computers name, it looks like, it's failing to get a lease or something. I'm getting back my address and in the network dialog I can see the gateway and DNS servers, But I don't know why is not registering on them. 

There's a lot of people that need to access my computer for testing, a quick reposonse will be greatly appreciate.

---

### Post by ape on 2006-01-17
Can you verify if you've gotten an IP address?  `ifconfig -a` and then look for your network adapter.  Does it have an IP address listed?  

If not, check your /var/log/syslog file for any dhclient: entries to see what error message you are getting back from your DHCP server.

If you are assigned an address, can you ping your DHCP server's IP address?

What are you seeing in your /etc/resolv.conf file?


If this is simply an issue of your machine's hostname not getting registered in DNS, the first questions are:  is your DNS set up to handle dynamic host registration and is your client set up to send the hostname to the DNS server?

---

### Post by mlsalcedo on 2006-01-17
Does it have an IP address listed?  Here is the output
eth0      Link encap:Ethernet  HWaddr 00:14:22:BF:18:97
          inet addr:132.197.112.180  Bcast:132.197.112.255  Mask:255.255.255.0

THis is what i found in syslog:
Jan 17 17:39:59 localhost kernel: [4317723.432000] tg3: eth0: Link is up at 100 Mbps, full duplex.
Jan 17 17:39:59 localhost kernel: [4317723.432000] tg3: eth0: Flow control is on for TX and on for RX.
Jan 17 17:40:00 localhost dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Jan 17 17:40:00 localhost dhclient: DHCPACK from 132.197.112.90
Jan 17 17:40:00 localhost dhclient: bound to 132.197.112.166 -- renewal in 116859 seconds.
Jan 17 17:40:07 localhost kernel: [4317732.314000] eth0: no IPv6 routers present

which looks good to me

My resolve is also good
search **********
nameserver 132.197.8.9
nameserver 132.197.70.9

I'm new to ubuntu, I was using gentoo before and everything was fine, so I'm used to gentoo's way, which is hard for me to find what is wrong with ubuntu.

I keep getting this problem, I'm planning to switch back Gentoo.


About your last question, Probably the client needs to send the host, but I don't know how to do it in ubuntu.

---

### Post by ape on 2006-01-17
This is what I have in my /etc/dhcp3/dhclient.conf file (in regards to sending the hostname data back):

send fqdn.fqdn "<your.hostname.>";  # don't forget the trailing dot
send fqdn.encoded on;
send fqdn.server-update on;

---

### Post by mlsalcedo on 2006-01-17
Should send fqdn.fqdn "<your.hostname.>"; command include the domain or just the hostname. in the /etc/dhcp3/dhclient.conf, they are sending everything hostname+domain, ex. :

send fqdn.fqdn "<mattpc.>"; or send fqdn.fqdn "<mattpc.loss.com.>";

---

### Post by ape on 2006-01-19
It should be the fully qualified hostname as far as I know (mattpc.loss.com.).

---

