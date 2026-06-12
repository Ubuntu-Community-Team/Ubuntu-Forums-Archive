---
title: "[SOLVED] how is this possible?"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by nixie21 on 2009-01-01
Kubuntu machine connected to actiontec router (wired)

Ping (ICMP Echo)
Destination:	192.168.1.4
	
Number of pings:	4
Status:	Test Failed
Packets:	4/4 transmitted, 0/4 received, 100% loss
Round Trip Time:	Minimum = 0 ms
Maximum = 0 ms
Average = 0 ms

Pther computers on network can be pinged.... I am on this computer right now.  The fact it can not be pinged I believe is causing some networking problems between computers...

Any ideas?

Thanks

---

### Post by cabbiinc on 2009-01-01
> **nixie21 said:**
> Kubuntu machine connected to actiontec router (wired)

Ping (ICMP Echo)
Destination:	192.168.1.4
	
Number of pings:	4
Status:	Test Failed
Packets:	4/4 transmitted, 0/4 received, 100% loss
Round Trip Time:	Minimum = 0 ms
Maximum = 0 ms
Average = 0 ms

Pther computers on network can be pinged.... I am on this computer right now.  The fact it can not be pinged I believe is causing some networking problems between computers...

Any ideas?

Thanks

Is your connection slow to start, but normal once the connection is made? Make sure that your DNS addresses are correct (I don't have/know about routers, but if I type my modems IP address into Firefox I can get into it to see what everything is). I had the first DNS address wrong and internet connections lagged before connecting. Once I fixed that all was good.

---

### Post by MaindotC on 2009-01-01
[quote=cabbiinc](I don't have/know about routers, but if I type my modems IP address into Firefox I can get into it to see what everything is)[/quote]
A modem doesn't have an IP address...it is a Layer 1 device.  You probably have a modem with built in switching functionality (just like most routers).

If you can ping google.com or any other external domain then you should be fine.  Anything beyond that would require you changing firewall settings on your machine or the router which I'm judging by the OP as highly unlikely.

---

### Post by nixie21 on 2009-01-01
interesting that on my laptop I can ping anything (except for the desktop)  When I ping anything on the desktop I get this

nixie21@Kubuntu:~$ sudo ping 192.168.1.6
PING 192.168.1.6 (192.168.1.6) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 192.168.1.6 ping statistics ---
12 packets transmitted, 0 received, 100% packet loss, time 11009ms

nixie21@Kubuntu:~$ ping google.com
PING google.com (209.85.171.100) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

---

### Post by Iowan on 2009-01-01
I wonder if something in the Zeroconf setup you mentioned in [ your other thread]("http://ubuntuforums.org/showthread.php?t=1026528") may have affected something.  The "sendmsg" part of the "ping" response looks unusual. If you have AppArmor installed, you might try disabling it (**/etc/init.d/apparmor stop**).

---

### Post by MaindotC on 2009-01-01
Is there any chance you have a firewall enabled on your machine like iptables?

---

### Post by superprash2003 on 2009-01-01
could you post output of ifconfig from the terminal

---

### Post by nixie21 on 2009-01-01
I have no firewall, although i played with one once...how can i check if something was left behind?  I will be home tomorrow night so will post the ifconfig then.  thanks so much for the help!  Happy New year to you all by the way!

---

### Post by MaindotC on 2009-01-01
You could open up Synaptic and type "firewall" and see if any of the ones that appear have thier boxes checked (indicating they are installed).  I'm using 8.04 and the packages ufw and iptables are installed by default.  I've been googling this and typically it seems to be a firewall issue.  Let me know if you have any installed and if so learn how to remove their restrictions.  I know one time I had a problem with iptables - I configured it just to see it actually working, and then I couldn't disable it or I didn't disable it properly.  I ended up just re-installing because the time it would have taken me to troubleshoot and figure out the way to do it was more than it would have taken me to reinstall.

---

### Post by nixie21 on 2009-01-02
here is ifconfig

nixie21@Kubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:f1:9a:51:5c
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fe9a:515c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:355 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:137951 (134.7 KB)  TX bytes:3138 (3.0 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5104 (4.9 KB)  TX bytes:5104 (4.9 KB)

---

### Post by nixie21 on 2009-01-02
for firewall UFW is installed...How do I acess this to find what is wrong?

---

### Post by nixie21 on 2009-01-02
OK!!!

I ran sudu ufw disable and it now works.  The problem is, do I need UFW?  I am not good with firewalls, but would use one if it was VERY easy to configure...

THANKS SO MUCH!!!!

---

### Post by superprash2003 on 2009-01-03
you could install gufw .. GUI for ufw.. please mark thread as SOLVED

---

### Post by nixie21 on 2009-01-03
> **superprash2003 said:**
> you could install gufw .. GUI for ufw.. please mark thread as SOLVED

thanks, how to a make it solved?

---

### Post by MaindotC on 2009-01-03
At the top of the page on the right it should say "Thread Tools" in red lettering.  You should be able to click that and on the drop-down menu there should be an option for "Mark Thread as Solved".

---

