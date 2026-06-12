---
title: "Access Ubuntu Server from outside home network"
date: 2013-03-14
forum: Networking &amp; Wireless
---

### Post by heinbu on 2013-03-14
Hey guys,

I know this sounds like a pretty common issue that a lot of people new to Ubuntu Server want to do, but I assure you I have gone through all the easy stuff and I need some assistance about what I am missing.

Here is the setup that I am working with:
Ubuntu Server (newest version)
Subsonic
Netgear WND3700 Router
Putty on my laptop

I've got the Server set up and I can access everything from inside of my own home network (both the server via Putty, and the Subsonic via a web browser), but I can not get access to it from outside of the network.

I have the external IP address that addresses my router from the outside world (and I can successfully ping it from a windows command line), and I have attempted to set up Port forwarding by opening port 654 and it shows the rule as active inside of my router's admin page and it connects to my internal IP address of 192.168.1.8, but when I attempt to access the site from outside my network as XXX.XXX.X.X:654 it just times out.

I eventually tried checking to see if the port was open using the tool [http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/) but it shows as closed.

I'm officially flummoxed.  :confused::confused::confused: I would very much appreciate any help that you can offer and I will provide any further information that you require.

Thank you for your time,
Nick

---

### Post by agillator on 2013-03-15
Do you have a firewall running on your server? Try 'sudo iptables -L -v -n' and see if it gives you anything but three policies. That probably is not your problem, but is easy to check and is the first thing to check.What is the router's rule that forwards port 654? I am suspecting the router is blocking the port for some reason.

---

### Post by heinbu on 2013-03-15
I checked the iptables and it only has the three policies.  The router rule that forwards port 654 looks like this:

External Start Port: 654
External End Point: 654
INternal Start Point 654
Internal End Point: 654
Internal IP Address: 192.168.1.8

I have no idea why it doesn't work. My small experience got me far enough to set it up that far, and I am not sure why it's not working cuz eyeballing it looks right.

I would love any advice!

---

### Post by Doug S on 2013-03-16
O.K. so you have sshd listening on port 654 instead of the default of port 22 on your server at 192.168.1.8. You know it is working O.K. because internally connecting to 192.168.1.8:654 works fine.
I checked [portforwarding.com ]("http://portforward.com/english/routers/port_forwarding/Netgear/WNDR3700/SSH.htm")and your router setup seems right. Seems it should be working.
Just as a sanity check observe the ports being listened to. Example:```
doug@s15:~$ [COLOR=#ff0000]sudo netstat -plnt[/COLOR]
[sudo] password for doug:
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.122.1:53        0.0.0.0:*               LISTEN      1900/dnsmasq
[COLOR=#ff0000]tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1154/sshd   <<< should be port 654 for you[/COLOR]
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1971/master
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      2056/apache2
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      874/smbd
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1676/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      874/smbd
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      2056/apache2
```Then check for actual packets arriving at your server with a packet sniffer. Example:```
doug@s15:~$ [COLOR=#ff0000]sudo tcpdump -n -nn -tttt -i eth0 port 654[/COLOR]
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
2013-03-15 22:44:58.462596 IP 192.168.111.1.46184 > [COLOR=#ff0000]192.168.111.112.654:[/COLOR] Flags [S], seq 48743279, win 14600, options [mss 1460,sackOK,TS val 460457735 ecr 0,nop,wscale 6], length 0
2013-03-15 22:44:58.462729 IP [COLOR=#ff0000]192.168.111.112.654 [/COLOR]> 192.168.111.1.46184: Flags [R.], seq 0, ack 48743280, win 0, length 0
```(I do not actually have anything listening to port 654, hence the "reset" returned packet. I just used telnet to try to make the connection. Interface eth0 is my internal LAN, use whatever interface for your case. Of course you can use wireshark if you prefer. The purpose is to determine if the packets are arriving at your server, and so we should look further at the server itself, or the packets are not getting forwarded by the router and so we should look further there. If packets are arriving at the server, check also for returned packets

---

### Post by heinbu on 2013-03-16
Well you have helped me to make headway! I made the changes that you suggested, and when I ran the packet sniffer Ubuntu basically went a little bit crazy (since I was running it via Putty) and was showing a crap ton of activity between 192.168.1.6 (my laptop) and 192.168.1.8 (my server).

I will have to check and see if I can access the server via something off the network now!

Any other advice? :D :D :D

I will let you know and mark it solved if it works

---

### Post by papibe on 2013-03-16
> **heinbu said:**
> I will have to check and see if I can access the server via something off the network now!
Just make sure you are not on in your network while trying to access your public IP or DDNS name (it usually don't work).

If you are using your phone, make sure it is not connected to your own Wifi.

Just a thought.
Regards.

---

### Post by kevdog on 2013-03-16
What your asking to do shouldn't be all that difficult.

Just for kicks this is how I would test the setup (while you are sitting at home next to the server).
Try connecting through your android phone using connect bot which would mimic the remote connection.
Turn off the firewall on the server (initially). 
Confirm the port if forwareded appropriately at the route.
Make sure your sshd_config file is listening on the correct port. 

connect with ssh -vvv via the client to see error messages.

---

### Post by Doug S on 2013-03-16
> **heinbu said:**
> Well you have helped me to make headway! I made the changes that you suggested, and when I ran the packet sniffer Ubuntu basically went a little bit crazy (since I was running it via Putty) and was showing a crap ton of activity between 192.168.1.6 (my laptop) and 192.168.1.8 (my server).

I will have to check and see if I can access the server via something off the network now!

Any other advice? :D :D :D

I will let you know and mark it solved if it worksSorry, I had assumed you had a local server connection. Yes, the tcpdump command I mentioned will blow up if you are using an SSH session to it. Why? becuase the tcpdump filter gets a hit, which causes output to the terminal, which causes more tcpdump hits, which causes more output to the terminal, ... For further tests using tcpdump and also via your putty session, try redirecting the tcpdump output to a file, then examine the file after your test accesses from the WAN.

Kevdog: From earlier postings, I think there is no firewall on the server. If that is not true and there is a firewall, then I would definately look there.

Edit: Or change the tcpdump command to exclude 192.168.1.6. Example (where my SSH session is from 192.168.111.101):```
doug@s15:~$ [COLOR=#ff0000]sudo tcpdump -n -nn -tttt -i eth0 not host 192.168.111.101[/COLOR]
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
2013-03-16 11:06:35.050705 IP 192.168.111.1 > 192.168.111.112: ICMP echo request, id 28762, seq 1, length 64
2013-03-16 11:06:35.050755 ARP, Request who-has 192.168.111.1 tell 192.168.111.112, length 28
2013-03-16 11:06:35.050837 ARP, Reply 192.168.111.1 is-at 00:19:b9:0d:af:fa, length 46
2013-03-16 11:06:35.050843 IP 192.168.111.112 > 192.168.111.1: ICMP echo reply, id 28762, seq 1, length 64
2013-03-16 11:06:36.049692 IP 192.168.111.1 > 192.168.111.112: ICMP echo request, id 28762, seq 2, length 64
2013-03-16 11:06:36.049718 IP 192.168.111.112 > 192.168.111.1: ICMP echo reply, id 28762, seq 2, length 64
2013-03-16 11:06:37.049441 IP 192.168.111.1 > 192.168.111.112: ICMP echo request, id 28762, seq 3, length 64
2013-03-16 11:06:37.049467 IP 192.168.111.112 > 192.168.111.1: ICMP echo reply, id 28762, seq 3, length 64

```

---

