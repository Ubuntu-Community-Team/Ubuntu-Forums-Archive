---
title: "Firefox/Opera incredibly slow"
date: 2006-01-02
forum: Networking &amp; Wireless
---

### Post by Traxis on 2006-01-02
Hi. I'm new to Ubuntu, I just installed 5.10, (I installed 5.04 and upgraded to 5.10 through Synaptic), and web pages are taking forever to load in Firefox 1.5 and Opera. My download speeds are normal, (~190k/sec), but it takes forever to initially connect to the server. For example, in Firefox when trying to load Google, it takes about 10 seconds to connect, but once it's connected it loads like normal. I've disabled IPv6, but that didn't help.

I'm using the onboard GigaLAN ethernet, (VIA K8T800 Pro chipset MB) and am connecting to my DSL through an Actiontec DSL gateway, (its a combo DSL modem and wireless router, I'm connected via ethernet cable, though). Everything works fine in XP, so I don't think it is a hardware problem.

---

### Post by jetpeach on 2006-01-03
There are a few possibilities, first I would suggest disabling ipv6.  hopefully the developers will not enable ipv6 by default in Dapper, and I've heard disabling it can improve your performance greatly.  In firefox, enter " about:config " in the address bar then search for ipv6 and change it to true for disabling it.
EDIT: it seems sometimes disabling in FIrefox isn't enugh, see this thread. [http://www.ubuntuforums.org/showthread.php?t=111676&highlight=ipv6](http://www.ubuntuforums.org/showthread.php?t=111676&highlight=ipv6)

---

### Post by handy on 2006-01-03
I've had this problem.

In Ubuntu
 
Menu:System/Administration/Networking

Double left click on the ethernet connection that you use to conect to the internet.  Usually "eth0"

Make sure that the "Configuration:" drop down is set to "DHCP" & OK out of there.

If it is set to "Static IP Address"  it will take a long time to load any page coming from a "New" server.  Once on that server the pages should load normally.

I do hope that this has helped you.

handy

---

### Post by HappySegfault on 2006-01-03
[QUOTE=handy]
[...] 

If it is set to "Static IP Address"  it will take a long time to load any page coming from a "New" server.  Once on that server the pages should load normally.

I do hope that this has helped you.

handy[/QUOTE]

Can you explain why would that make any difference?  From what I understand, all DHCP does is assign an IP address, gateway address, etc.  Once they're assigned, there shouldn't be any difference in the way things work as long as the static IP address setup is OK.  

I have similar problems as the original poster is having---good download throughputs but slow initial connections.  It looks to me like a network latency problem somewhere.  

HappySegfault

---

### Post by mips on 2006-01-04
Initial slow connections might be DNS/IPv6 related.

Look at *Reaching the Internet by name* & *Common Application Problems* in the thread below. 
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

---

### Post by stream303 on 2006-01-25
[QUOTE=HappySegfault]
I have similar problems as the original poster is having---good download throughputs but slow initial connections.  It looks to me like a network latency problem somewhere.[/QUOTE]

Most likely a DNS problem that has to time-out.  I'd look at your **/etc/resolv.conf**
and see if the nameservers are pointing to your isp's nameserver(s), and not those of the router.

If they are pointing to the dns inside the router, there is an easy fix to bypass it by editing /etc/dhcp3/dhclient.conf, but we can go from here...

---

### Post by JeffBlouin on 2006-02-05
Hi

           
I looked at my /etc/resolv.conf and it says :

nameserver 192.168.123.254

This is my router adress

Here is my  /etc/dhcp3/dhclient.conf: 

# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

And now what i do with that...

Thanks
As you see Im pretty new to all this!
Jeffblouin

---

### Post by darkpark on 2006-02-05
look at the line 
#prepend domain-name-servers 127.0.0.1;
of your dhclient.conf.

uncomment that line and insert the ip addresses of your ISP's dns servers (be sure to delete the local loopback 127.0.0.1).

---

### Post by JeffBlouin on 2006-02-05
Hi

Where do I get my ISP nameserver

Hope to find the problem soon...!

Thanks

---

### Post by mips on 2006-02-05
You can get your DNS/Nameserver IP addresses from your ISP.

Who is your ISP, weblink please ?

---

### Post by JeffBlouin on 2006-02-05
Hi,

I called my ISP and got the dns naserver: 192.168.2.1 
I uncommented the line :
 #prepend domain-name-servers 127.0.0.1;and insert this ip addresses

I restarded Ubuntu but nothing is going faster than before. It take alot of time to start loading the page but once it start the speed look normal.

My Speedstream modem is connected to a USR 5850 router|wireless but im not using the wireless feature.

Anything else to do... because i cannot use ubuntu with this kind of speed!

Thanks

---

### Post by mips on 2006-02-06
I might be wrong but that address does not seem right. That address is a private address and ISP DNS servers usually use public IP addresses.

Who is your ISP, weblink ?

---

### Post by JeffBlouin on 2006-02-06
The ISP is sympatico

[www.sympatico.ca](www.sympatico.ca)

How should a public adress look like? 

Thanks alot for your help!

Jeffblouin

---

### Post by mips on 2006-02-07
What Brand&Model router are you using ???

That website probably has the crappiest support I have ever seen but in the process I learned something new. I figured out how to get DNS server addresses from the internet via the command line.
> 
reon@obelix:~$ **dig ns sympatico.ca**

; <<>> DiG 9.3.1 <<>> ns sympatico.ca
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 53205
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 4

;; QUESTION SECTION:
;sympatico.ca.                  IN      NS

;; ANSWER SECTION:
sympatico.ca.           320     IN      NS      dns1.sympatico.ca.
sympatico.ca.           320     IN      NS      dns2.sympatico.ca.
sympatico.ca.           320     IN      NS      ns5.bellnexxia.net.
sympatico.ca.           320     IN      NS      ns6.bellnexxia.net.

;; ADDITIONAL SECTION:
ns5.bellnexxia.net.     455     IN      A       [COLOR="Red"]**209.226.175.236**[/COLOR]
ns6.bellnexxia.net.     62858   IN      A       [COLOR="Red"]**209.226.175.237**[/COLOR]
dns1.sympatico.ca.      320     IN      A       [COLOR="Red"]**204.101.251.1**[/COLOR]
dns2.sympatico.ca.      1242    IN      A       [COLOR="Red"]**204.101.251.2**[/COLOR]

;; Query time: 47 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Tue Feb  7 11:09:15 2006
;; MSG SIZE  rcvd: 182

reon@obelix:~$

From a terminal **sudo gedit /etc/resolv.conf**
```
nameserver 209.226.175.236
nameserver 209.226.175.237
nameserver 204.101.251.1
nameserver 204.101.251.2
nameserver 192.168.123.254
```  

Are you 100% certain this is your routers IP ???

> How should a public adress look like?
If an IP address falls within one of the following ranges then it is a Private address:
10.0.0.0 to 10.255.255.255
172.16.0.0 to 172.31.255.255
192.168.0.0 to 192.168.255.255

Another type of Private address is link-local addresses 169.254.1.0 to 169.254.254.0

These addresses are not routable over the internet. All other address are Public addresses with the exception of a few reserved for other purposes like loopback, multicast etc.

---

