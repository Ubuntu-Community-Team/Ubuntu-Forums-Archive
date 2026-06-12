---
title: "IP Masquerading issue"
date: 2011-04-15
forum: Networking &amp; Wireless
---

### Post by drewbob on 2011-04-15
Hi all, I've got a laptop connecting wirelessly to a router/cable modem, and I want to use a crossover cable to connect my desktop computer to the internet through the laptop.  Both are running Ubuntu 10.10.

I've followed various IP Masquerading HOWTOs and I still can't get this to work.  The ones I've looked at are: 

1) [http://linux.about.com/od/ipm_howto/a/hwtipm19t00_5.htm](http://linux.about.com/od/ipm_howto/a/hwtipm19t00_5.htm)
2) [http://linux.about.com/od/ubusrv_doc/a/ubusg18t03.htm](http://linux.about.com/od/ubusrv_doc/a/ubusg18t03.htm)
3) [http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

In 3) there is a lot of stuff about setting up a DHCP server on the laptop, but I figure I can leave this if I just configure the ip/subnet/gateway on each card individually (maybe this would need doing every time but I'm happy to do it while just trying to get the masquerading working).  Am I right about this or is it absolutely necessary?

Then I've basically customised the IP masquerading script in 1).  The only bits I have edited are: 

 EXTIF="wlan0"
 INTIF="eth0"
 echo " External Interface: $EXTIF"
 echo " Internal Interface: $INTIF"
I've commented out the bit about dynamic IP addresses because mine is static.  And then the commands the script seems to send are:

$IPTABLES -P INPUT ACCEPT
 $IPTABLES -F INPUT 
 $IPTABLES -P OUTPUT ACCEPT
 $IPTABLES -F OUTPUT 
 $IPTABLES -P FORWARD DROP
 $IPTABLES -F FORWARD 
 $IPTABLES -t nat -F
to clear the IPTABLES
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT
 $IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
 $IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE

and this is the actual masquerading

Here is my ifconfig for wlan0 and eth0 on the laptop (host):

eth0      Link encap:Ethernet  HWaddr 00:26:22:ee:71:ad  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::226:22ff:feee:71ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1400 (1.4 KB)  TX bytes:20326 (20.3 KB)
          Interrupt:42 Base address:0xa000 

wlan0     Link encap:Ethernet  HWaddr 70:1a:04:81:07:74  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::721a:4ff:fe81:774/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25367 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25939 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17595241 (17.5 MB)  TX bytes:5321799 (5.3 MB)
          Interrupt:18 Memory:ffffc90003df8000-ffffc90003df8100 


[FONT=Verdana]On the desktop I have eth0 configured as having inet_addr: 192.168.2.2, Bcast: 192.168.2.255
Mask 255.255.255.0

and the default gateway is 192.168.2.1

(Does eth0 on the laptop need the gateway to be the inet_addr of wlan0?)

The two machines can ping each other fine, but the desktop still has no network connection... Anyone able to help?  
Sorry if this isn't laid out too well, there's a lot of information and I'm not entirely sure what's relevant; if anything needs clarifying or adding let me know...
Thanks a lot for the help in advance,

Andrew
[/FONT]

---

### Post by drewbob on 2011-04-15
I've got it sorted and I'm pretty sure I know why, but I'm updating right now and daren't fiddle with anything until it's finished.  I didn't set the DNS address in /etc/resolv.conf so just added the line:

nameserver 192.168.1.1 

and it seems to have worked fine.  

This was also having cleared the iptables manually using commands similar to those mentioned in the opening thread, and typing in the following commands manually: 

sudo iptables -A FORWARD -d 192.168.1.0/16 -m state --state ESTABLISHED,RELATED -i wlan0 -j ACCEPT
sudo iptables -A FORWARD -s 192.168.1.0/16 -o wlan0 -j ACCEPT
sudo iptables -t nat -A POSTROUTING -s 192.168.1.0/16 -o wlan0 -j MASQUERADE

Don't know if this will help anyone but it's there incase it might.

---

