---
title: "Creating a web site using a dynamic DNS service"
date: 2013-06-01
forum: Networking &amp; Wireless
---

### Post by Colugo on 2013-06-01
I'm trying to set up a webpage using Ubuntu 12.04 and a dynamic DNS service. I'm recounting the process for those that follow and for error checking purposes. I installed apache2 on my would be server and verified that I could access it over the WAN. From my laptop, I can enter in 192.168.254.2 and I get the default page. At this point, the address is still dynamically assigned (the .2 means that the server was turned on second), so I need to make the server a static IP address. I edit the /etc/network/interfaces file to be static (because I'm using an old iMac as a server, it is eth2 rather than eth0) *and* use network manager on the server to change the ip address to 192.148.254.5. I have to use ifdown eth2 then ifup eth2 to get this to work - you can't just restart network services. Next I log into my wireless router (determine your ip address with a search engine, then enter it into the web browser) and change it so that incoming HTTP traffic is directed to port 80 (or 8080) on 192.168.254.5. Next I go to no-ip.biz and create an account. I add a host at myplace.no-ip.biz. I download and install their dynamic update client (noip2).

So, now what? If I enter in the host name I selected (myplace.no-ip.biz) as a url, I get nothing. When I do nslookup on myplace.no-ip.biz I get a different ip address than the one registered at no-ip.com and what I get from whatismyip.com. Thus no-ip.com isn't working?

---

### Post by SASDOE2 on 2013-06-01
Not sure of this, but when I setup my server with dyn dns, I also had to tell my router about it so it would automatically update the ip. Also you should know that visiting yourplace.no-ip.biz from your home network will not work (or it will only point you to your router) as long as you don't setup a loopback.

Another thing you could try is telling your router to assign ip 192.1168.1.2 to the server and try again.

---

### Post by Colugo on 2013-06-01
I changed my dynamic DNS service to freeDNS.afraid.org, and am much happier (go Josh!). I installed ddclient, which more or less works - it will not accept 'protocol=freedns'. [This]("https://freedns.afraid.org/scripts/freedns.clients.php") is the reference page for that. Now nslookup for myplace.crabdance.com returns the same IP address as an IP lookup site. I have also found that network manager takes precedence over the interfaces file. I still can't access a webpage or a SSH connection. I have this on my router:

[TABLE]
[TR]
[TD="class: hd"]Server Name[/TD]
       [TD="class: hd"]External Port Start[/TD]
       [TD="class: hd"]External Port End[/TD]
       [TD="class: hd"]Protocol[/TD]
       [TD="class: hd"]Internal Port Start[/TD]
       [TD="class: hd"]Internal Port End[/TD]
       [TD="class: hd"]Server IP Address[/TD]
       [TD="class: hd"]WAN Interface
[/TD]
       [TD="class: hd"]Remove[/TD]
    [/TR]
    [TR]
       [TD]Web Server (HTTP)[/TD]
       [TD]80[/TD]
       [TD]80[/TD]
       [TD]TCP[/TD]
       [TD]80[/TD]
       [TD]80[/TD]
       [TD]192.168.254.5[/TD]
       [TD]ppp0[/TD]
       [TD="align: center"][/TD]
    [/TR]
    [TR]
       [TD]Secure Shell Server (SSH)[/TD]
       [TD]2121[/TD]
       [TD]2121[/TD]
       [TD]TCP[/TD]
       [TD]22[/TD]
       [TD]22[/TD]
       [TD]192.168.254.5[/TD]
       [TD]ppp0[/TD]
       [TD="align: center"][/TD]
    [/TR]
 [/TABLE]

---

### Post by Colugo on 2013-06-01
I changed my dynamic DNS service to freeDNS.afraid.org, and am much happier (go Josh!). I installed ddclient, which more or less works - it will not accept 'protocol=freedns'. [This]("https://freedns.afraid.org/scripts/freedns.clients.php") is the reference page for that. Now nslookup for myplace.crabdance.com returns the same IP address as an IP lookup site. I have also found that network manager takes precedence over the interfaces file. I still can't access a webpage or a SSH connection. I have this on my router:

[TABLE]
[TR]
[TD="class: hd"]Server Name[/TD]
[TD="class: hd"]External Port Start[/TD]
[TD="class: hd"]External Port End[/TD]
[TD="class: hd"]Protocol[/TD]
[TD="class: hd"]Internal Port Start[/TD]
[TD="class: hd"]Internal Port End[/TD]
[TD="class: hd"]Server IP Address[/TD]
[TD="class: hd"]WAN Interface[/TD]
[TD="class: hd"]Remove[/TD]
[/TR]
[TR]
[TD]Web Server (HTTP)[/TD]
[TD]80[/TD]
[TD]80[/TD]
[TD]TCP[/TD]
[TD]80[/TD]
[TD]80[/TD]
[TD]192.168.254.5[/TD]
[TD]ppp0[/TD]
[TD="align: center"][/TD]
[/TR]
[TR]
[TD]Secure Shell Server (SSH)[/TD]
[TD]2121[/TD]
[TD]2121[/TD]
[TD]TCP[/TD]
[TD]22[/TD]
[TD]22[/TD]
[TD]192.168.254.5[/TD]
[TD]ppp0[/TD]
[TD="align: center"][/TD]
[/TR]
[/TABLE]

Part of the problem is that the iMac/server can't decide if it's using eth1 or eth2. In fact, it seems that whenever I change /etc/network/interfaces, it switches to something else. 


Can someone tell me what this line in the ddclient.conf does:


 #use=if, if=eth0

? ddclient isn't working, but I can manually set the IP at freedns.afraid.org.

Thanks, love y'all

---

### Post by Colugo on 2013-06-04
For those who come after:  the problem is that one cannot access this kind of server from within one's home network. Once I logged into my neighbor's unprotected network, I can see the webpage and access the SSH server fine. The ddclient still doesn't work. In some fashion it must resolve the home IP address, which isn't easy from the terminal. The line with 'use' in it in the ddclient.conf file seem to do this, but I don't know how to control it.

---

### Post by papibe on 2013-06-04
Hi Colugo.

This works for me (using DynDNS):
```
use=web, web=checkip.dyndns.com, web-skip='IP Address'
```
Then you should restart the service:
```
sudo service ddclient restart
```
Let us know how it goes.
Regards.

---

