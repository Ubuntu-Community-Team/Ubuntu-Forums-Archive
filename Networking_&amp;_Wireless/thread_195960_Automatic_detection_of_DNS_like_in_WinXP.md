---
title: "Automatic detection of DNS like in WinXP???"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by carlos123 on 2006-06-13
I have been having an extreme problem using the Internet while running Ubuntu in that it has been sooo slow with packet losses routinely running upwards of 20% (sometimes as high as 50%).  

I finally was able to diagnose part of the problem or perhaps the whole problem in that if I eliminate a DNS query and ping an IP address directly there is no packet loss and no problem.  

My /etc/resolv.conf file has one line....

nameserver 192.168.0.1

My question is how can I get Linux Ubuntu to automatically get the DNS nameserver IP address from the DHCP server without specifying the IP explicitly in the /etc/resolv.conf file?  I roam around and use various connection points from two ISP's that I use which means that my DNS server will not always be the same.  I recently travelled out of country and used still another different DNS server.  

Windows picks up the DNS server IP automatically from any existing DHCP server in whatever network I happen to be using.  Is there a way to have Ubuntu Linux do the same?  

Any input or suggestions would be greatly appreciated.  

Thanks.  

Carlos

---

### Post by viper52b on 2006-06-13
If your /etc/resolv.conf file is completely empty, linux will get the DNS server from the DHCP lease...
So your best bet is to just remove that nameserver ip from the file.

Hope it helps :)

---

### Post by carlos123 on 2006-06-13
Thanks for the input viper52b but I don't think that is correct.  If I remove everything from the /etc/resolv.conf file I cannot connect to the internet no matter what I do.   No ping.  No host <site-name>.  No nothing.  

I have to have at least the nameserver designation inside the file to make it work at all.  

Carlos

---

### Post by dbarron on 2006-06-13
Actually Viper is correct...assuming STD DHCP lease and configuration.  I would agree that the best course is to let the automation handle it (since your params vary).  If you insist, you can populate two files, and set up something to copy the proper nameserver info to /etc/resolv.conf.

---

### Post by carlos123 on 2006-06-14
Not sure what you are saying dbaron about having two files and copying the info from one to the other or something to that effect.  I will play with it some more.  If not having any info in the /etc/resolv.conf file is supposed to allow Linux to get the nameserver IP's automatically from DHCP I am not sure what is going on with my setup where it does not appear to be doing that.  I'll report back in this thread when I get things working.  

Thanks again to both of you for your input.  

Carlos

---

### Post by viper52b on 2006-06-14
Have you tried requesting a new DHCP lease after making the /etc/resolv.conf file empty?

```
# dhclient
```

This should work. Except (like dbarron said) if there is something wrong with the DHCP server configuration or if there's something totally different wrong ;) .

Greetz

---

### Post by ape on 2006-06-14
You may also want to validate that your dhclient.conf file is properly configured to ask for the domain-name-servers from the dhcp server.  This file can be found under /etc/dhcp or /etc/dhcp3 depending on the client.

---

### Post by carlos123 on 2006-06-14
Thanks for the added tip viper52b.  

I deleted whatever was inside the /etc/resolv.conf file first.  Then I executed dhclient.  Here are the results....

```

carlos@laptop:/etc$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:0f:b0:dd:f2:81
Sending on   LPF/eth0/00:0f:b0:dd:f2:81
Listening on LPF/eth1/00:16:6f:11:43:2c
Sending on   LPF/eth1/00:16:6f:11:43:2c
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPNAK from 192.168.0.1
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.3 -- renewal in 252267 seconds.
carlos@laptop:/etc$ cat resolv.conf
nameserver 192.168.0.1

```

Running dhclient put the 192.168.0.1 line right back into /etc/resolv.conf.   I then did a ping through DNS to [www.google.com](www.google.com) with the following result....

```

carlos@laptop:/etc$ ping www.google.com
PING www.l.google.com (72.14.203.99) 56(84) bytes of data.
64 bytes from 72.14.203.99: icmp_seq=1 ttl=245 time=57.6 ms
64 bytes from 72.14.203.99: icmp_seq=2 ttl=244 time=53.4 ms
64 bytes from 72.14.203.99: icmp_seq=3 ttl=245 time=59.8 ms
64 bytes from 72.14.203.99: icmp_seq=4 ttl=245 time=54.5 ms
64 bytes from 72.14.203.99: icmp_seq=5 ttl=245 time=57.6 ms

--- www.l.google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 31252ms
rtt min/avg/max/mdev = 53.420/56.642/59.893/2.350 ms

```

While my packet losses seem to have disappeared notice the long time value.  It was slow....

One thing I don't understand is why the time value is so high when compared to the individual 
time values that show up after each ping.  If you add up the time values of each ping they 
don't come anywhere near equaling the time value of the report spit out at the end. 

I then did a ping to the IP of [www.google.com](www.google.com) which generated what seems to be 
normal results....at least in so far as the time value was not so high and the ping went along 
smoothly.  The bottom line of the report seems almost identical to the slow ping through DNS 
though.

```

carlos@laptop:/etc$ ping 72.14.203.99
PING 72.14.203.99 (72.14.203.99) 56(84) bytes of data.
64 bytes from 72.14.203.99: icmp_seq=1 ttl=245 time=54.9 ms
64 bytes from 72.14.203.99: icmp_seq=2 ttl=245 time=58.8 ms
64 bytes from 72.14.203.99: icmp_seq=3 ttl=245 time=59.6 ms
64 bytes from 72.14.203.99: icmp_seq=4 ttl=245 time=54.1 ms

--- 72.14.203.99 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3052ms
rtt min/avg/max/mdev = 54.120/56.898/59.688/2.401 ms

```

The difference in the pings between pinging through DNS to a domain name and pinging to the IP (bypassing DNS) is what led me to believe that the problem was with DNS.  Originally I had major packet losses too along with a super slow ping result when going through DNS.  

Ethereal (the network analyzer program) shows what seems to be an excessive amount of packets having to be retransmitted when I go a web page like google.
I believe my router is working correctly and is set up correctly since I can access the Internet just fine from this same laptop when I boot into Windows XP.  Likewise I can access the internet more than fine when I go through my desktop which is hooked up through an Ethernet cable to my router.  

It's possible that the Linux driver for my wireless card in the laptop is faulty or less than good enough. Not sure.  

Any further suggestions as to how I can track this problem down would be appreciated.  

Carlos

---

### Post by carlos123 on 2006-06-14
My dhclient config file which I believe is /etc/dhcp3/dhclient.conf has the following lines in it that seem relevant (I left out all other lines from this reply but they were all commented out anyway)....  

```

# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;

```

Perhaps I could uncomment the "require" line?  Don't know. 

Carlos

---

### Post by mips on 2006-06-14
Manually configure your ISP's DNS servers and don't use the ones obtained from dhcp lease.

---

### Post by carlos123 on 2006-06-14
Thanks mips but that is precisely what I am trying to avoid.  Namely setting up the nameservers to use in a manual way.  I don't want to sit there and have to remember to first off find out what those DNS namervers IP addresses are, edit the /etc/resolv.conf file, put them in through a text editor, and then restart the network to have them used.   I change ISP's quite often due to my work and travel circumstances.  

I can't believe that there is not in Linux and Ubuntu more specifically some way of imitating the way it is done in Windows XP where I simply connect and it does it all for me.  Gets the DHCP lease for internet access, determines my IP, determines and uses the proper DNS server IP's, and so forth without my having to manually do anything at all.  I just go and use whatever ISP I am using at the time and presto, as long as they provide internet access through a DHCP server, it's done for me!  Under Windows XP that is.  

I mean I love Linux but having spent a great deal of time in the past having to configure this or that manually under Gentoo Linux I am hoping that under Ubuntu I can get away from so much manual configuring and get to more actual use of my computer to do things - under Linux if at all possible.  

Carlos

---

### Post by upiph on 2006-06-20
I had the same problem. My solution allows to retrieve the DNS-IP from the DHCP-server and to set a preferred DNS and you have to edit the config-file only once:

In the file the file /etc/dhcp3/dhclient.conf I added the following line above the existing cofigurations:

```

prepend domain-name-servers <my-dns-ip>;
```

After invoking dhclient my resolv.conf looks like this:

```

$ cat /etc/resolv.conf 
nameserver <my-dns-ip>
nameserver 192.168.1.1
```

You could add as much of the "prepend"-lines as you wish to do. 

Greez upiph

---

### Post by tturrisi on 2006-06-20
at prompt type: network-admin & then Configure button > DNS tab and verify that the liseted dns servers are the same ones listed in your access point or router status page.  Also, since this is an issue which appears to only occur in your wifi then it is likely that there is something misconfig'd or askew in the access point-router settings OR there is some device or object(s) in vicinity of wifi comp that interferes w/ the wifi signal (flourecent lights, wires, cables, etc)  thus causing packet loss.

---

### Post by mips on 2006-06-22
Carlos,

Ok I see your point. Could I suggest possibly trying to disable IPv6 system wide and see if it improves matters at all ???

---

