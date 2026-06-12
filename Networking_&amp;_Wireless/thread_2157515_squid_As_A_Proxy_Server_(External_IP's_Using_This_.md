---
title: "squid As A Proxy Server (External IP's Using This Server)"
date: 2013-06-25
forum: Networking &amp; Wireless
---

### Post by CaseyC on 2013-06-25
I am curious, I have tried to set this up before: I have a VPS on a server that I rent, I installed squid to use as a proxy server, however my home PC (not on the same subnet as the squid) and I could not get my PC to connect and navigate the internet. 

Does anyone know or have a guide on how to setup squid on an external network, that will allow a PC on another network to connect it and use it as a proxy server?

---

### Post by SeijiSensei on 2013-06-25
Did you configure your browser to use the proxy's IP and port?

Is the port open on the remote server, or at least open to connections from your IP address?

What do you see when you type "telnet ip.of.proxy.server 3128" on your client?

Is there any reason to think the ISP is intercepting port 3128?  What if you set an arbitrary port like 33128?  (Use the http_port directive in squid.conf to do this.)

If you tried to set up a transparent proxy, that isn't going to work if squid is running on a machine outside your network.  You need remove the transparent directive, restart squid, then tell the browser to use the proxy by IP and port specifically.

---

### Post by CaseyC on 2013-06-25
Right now I have this in my Firefox windows: The proxy server is refusing connections. Firefox is configured to use a proxy server that is refusing connections. 

Obiviously I have something setup wrong. Here were my steps: 

1. sudo apt-get install squid3. 
2. Edited /etc/squid3/squid.conf -> http_port 33128 (not commented out). 
3. Edited /etc/squid3/squid.conf -> http_access allow all (I added this line). 

Here is some more of my acl's that were pre-set when I installed squid. 


```
# Only allow cachemgr access from localhost
http_access allow manager localhost
http_access allow all
http_access deny manager

# Deny requests to certain unsafe ports
http_access deny !Safe_ports

# Deny CONNECT to other than secure SSL ports
http_access deny CONNECT !SSL_ports
```

---

### Post by CaseyC on 2013-06-25
Attached is my squid.conf file zipped.

---

### Post by SeijiSensei on 2013-06-25
Here's a hint for the future.  You can strip out all the comments by running this command

```
grep -v '^#' squid.conf | grep -v '^$' > squid.stripped.conf
```

The first "grep" command removes ("-v") anything beginning with a hash mark ("#").  It passes the result to another grep which removes blank lines.  The result is stored in the file squid.stripped.conf in the current directory.

Applying that to your squid.conf results in 

```

acl manager proto cache_object
acl localhost src 127.0.0.1/32 ::1
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32 ::1
acl SSL_ports port 443
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl CONNECT method CONNECT
http_access allow manager localhost
http_access allow all
http_access deny manager
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access deny all
http_port 33128
coredump_dir /var/spool/squid3
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern -i (/cgi-bin/|\?) 0     0%      0
refresh_pattern (Release|Packages(.gz)*)$      0       20%     2880
refresh_pattern .               0       20%     4320

```

Now the "allow all" should enable connections from any address, so I'm guessing there is some type of firewalling in the way.  Since you changed the port to 33128, please try running the "telnet" command I gave you above.  You should get a response like this:

```

$ telnet 10.1.1.5 33128
Trying 10.1.1.5...
Connected to 10.1.1.5.
Escape character is '^]'.

```

Use Ctrl-] to exit the session.  If you don't get this response, log into the VPS and try the same command from a prompt there using 127.0.0.1 as the address.  Does that work?

---

### Post by CaseyC on 2013-06-26
When I telnet from a Windows PC, and here is the output

```
Microsoft Telnet> open 11.22.33.44 33128
Connecting To 11.22.33.44...Could not open connection to the host, on port 33
128: Connect failed
Microsoft Telnet>
```

And thank you for the regex grep snippet :) I use regex's at work every day and completely forgot about them. Here is the output currently that I have configured in my squid.conf file. Note: I have removed the http_access deny all line that appeared below the http_access allow all 

```
acl manager proto cache_object
acl localhost src 127.0.0.1/32 ::1
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32 ::1
acl SSL_ports port 443
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl CONNECT method CONNECT
http_access allow manager localhost
http_access allow all
http_access deny manager
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_port 33128
coredump_dir /var/spool/squid3
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern -i (/cgi-bin/|\?) 0     0%      0
refresh_pattern (Release|Packages(.gz)*)$      0       20%     2880
refresh_pattern .               0       20%     4320
```


I have started / stopped / started the service, rebooted the server as well...

---

### Post by SeijiSensei on 2013-06-26
Have you tried "telnet localhost 33128" on the server itself?  How about "telnet ip.of.external.interface 33128"?

---

### Post by CaseyC on 2013-06-26
I was able to connect using telnet localhost 33128. So this appears to be something on my end? 

I enabled outbound and inbound connections on my local PC to accept connections ranging from 33000 and 34000, restarted my firewall, and I was unable to telnet to the vpn server I have. Next I disabled my firewall all together. (Note: I am using this PC at work so there might be network restrictions on my corp network?)

---

### Post by Cheesemill on 2013-06-27
> **CaseyC said:**
> Note: I am using this PC at work so there might be network restrictions on my corp network?

I think this is your problem.

Wherever I have set up corporate networks the ***only*** connections allowed to the internet are through the companies own proxy server. This is to stop people doing exactly what you are attempting.

Have a word with IT support and see if you can agree on a solution with them (they may well just say no, you can't do it).

---

### Post by CaseyC on 2013-06-27
Thanks I believe you are correct as well! The only time I have to work on it is between Nessus scans during the day, where RHEL and SLES scans can take awhile, I started my little project :). 

I will attempt this at another location and see if it works!

---

### Post by SeijiSensei on 2013-06-27
Originally you said this was a problem with your "home PC" so I've been working from that assumption all along.

If you are behind a corporate firewall, that is a very different story.  The firewalls I build for clients would not let you connect to a high port either.  In fact we block all traffic originating on high ports behind the firewall destined for high ports on remote servers.  There is no reason ordinary users need that kind of access since they should be connecting to servers listening on ports below 1024 like 80, 443, etc.

Letting people send random traffic from high ports behind the firewall to high ports on remote machines is just an invitation for them to run torrents, play games, or engage in other non-work-related activities that oftentimes consume bandwidth unnecessarily.

---

### Post by tony_j87 on 2013-12-04
hi there,

I am new to the squid proxy and have followed these steps from this website -->[http://www.danscourses.com/Linux-Fundamentals/install-a-configure-squid-in-ubuntu.html](http://www.danscourses.com/Linux-Fundamentals/install-a-configure-squid-in-ubuntu.html)

Once i put my ip address in firefox and finish the steps upto here
 --> To re-enable web access uncomment line 676
[FONT=Courier] #http_access allow localnet
[/FONT]to
[FONT=Courier] http_access allow localnet[/FONT] To verify the Web is now working, save your changes to the squid.conf file and restart your Squid server.
[FONT=Courier] service squid restart (or "sudo service squid restart" if you are no longer root)[/FONT]

I get a mseesage "The proxy server is refusing connections'.

I ran this test setup in vmware to test it. both guest and host networks show the same thing in the browser.

I have DHCP enabled on my router. Could this conflict with the proxy settings? Do I have to turn DHCP off to get rid of that message that displays on the browser?

Thanks.

---

