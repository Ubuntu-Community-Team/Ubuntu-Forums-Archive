---
title: "Ping problem"
date: 2011-07-27
forum: Networking &amp; Wireless
---

### Post by budgie9 on 2011-07-27
Can someone do some testing for me.

I have a high speed internet connection that drops the Internet for around 4 minutes on most days. Myself and the Internet provider are trying to resolve this issue, but so far have failed to find a cause for the drop out. 
The Router used is a Netgear which has been swapped out with a Dlink and a Linksys and the same drop out happens, with or WITHOUT a router in line. All are wired routers. Using either  Ubuntu or XP the same happens. 
We can not see a drop in connection at the router, nor at the radio transmitter attached to the house. The provider has not found any reason for a drop out at his end either. With a constant ping of the transmitter on my house from his end also proving fruitless.

I use the Network tools in Ubuntu to see if I can Ping the DNS servers and or the equipment used to access the Internet. I also use Ping in Terminal to do the same thing, but not at the same time. Here is the problem that I need resolving.

In both the Network Tools and in Terminal I PING the router, the radio transmitter dish ( used for my connection to the Internet) and the DNS servers such as the OpenDNS 208.67.222.222 or 208.67.220.220 and 156.154.70.1. also Google and other sites where one can ping for testing.

The problem is if I type in to Terminal or the Network tools one of these numbers it pings the site and returns the Ping rate. That is fine. But if one STOPS the Ping and restarts it, in either tools or Terminal, there is no response. Which defeats the testing of course, as I can't prove that the ping is working or not. This is not a one off stop, it happens almost all the time. 
Here is the sequence for clarity of request.

Ping 192.168.10.1 ping returns details as normal.
Hit STOP in Tools or Control C in Terminal 
Start Ping to 192.168.10.1 
No response back.
in Terminal it returns 
PING 192.168.10.1 (192.168.10.1) 56(84) bytes of data.
and stops.
Just a flashing cursor.
Any recall of the command still returns a flashing cursor

Can someone else test this for me, to see if they get the same response. Or tell me if there is something I am doing wrong. Perhaps I have found a bug in the Ping tool, but I doubt it. 

If anyone has any ideas why my Internet connection should drop for these few minutes on must days I would be interested to hear.

---

### Post by thefasterblueone on 2011-07-27
I had a very similar problem recently. I had made some changes in my router configuration. I changed the 'Internet IP Address' from 'Get Dynamically from ISP' to 'Use Static IP Address' and then I was getting a bad connection and eventually could not Ping any addresses. so check if you have a static IP or a Dynamic IP and set your router correctly.

Also set your DNS server in your router to 'Use DNS addreses of your choice'. Google DNS addreses are:
```
8.8.8.8 and 8.8.4.4
``` 
They work very good. You will also want to set your DNS server addreses in resolv.conf file:
```
sudo gedit /etc/resolv.conf
```
so it looks like this if you use Google DNS servers:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```
Rebooting your router can fix problems too and rebooting the computer after the router will help also.

To check where your connection is dropping off try running this command in Terminal, you can change the host to whatever you want:
```
mtr yahoo.com
```

---

### Post by budgie9 on 2011-07-27
Many thanks for your response Thefasterblue one.
I have looked at the router settings and checked these out many times. I had a feeling that the router was to blame, but have disproved it by swapping it out on a few occasions. Including using default settings in the routers.
Google is one of the DNS servers I use, after both the provider and myself thought it maybe a DNS server problem. This has proved to be baseless. I use 8.8.8.8 as my primary DNS server, but don't normally use it for pinging, for some reason.

The mtr command I had not known of and will try that out when the Internet stalls again, probably in the morning, As these stops seem to happen mainly after being shut down for the night and then within the next hour or so of using it again. But it has frequently happened after a full day running fine. Totally unexplainable to us. I should have added, that it happens to all of my computers if they are on.
If you or anyone else has any ideas, I am willing to listen.

---

