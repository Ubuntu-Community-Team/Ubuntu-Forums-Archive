---
title: "SSH with dynamic ip adress; connection times out"
date: 2011-09-20
forum: Networking &amp; Wireless
---

### Post by tjoff on 2011-09-20
My parents live far away from me, but often need assistance with the computer. I therefore want to be able to administer their ubuntu-box remotely with ssh. Since none of us have static ip adresses, my plan is to use DynDNS to keep track of the ip adresses. 
Before I involve my parents, I want to test it all on my own computer, in short: I want to connect to my own computer with ssh, but using DynDNS to resolve the ip adress. In the following xxx.xxx.xxx.xxx stands for an actual public ip adress.
  
The problem arises when i try to log in with DynDNS:

```
myname@mybox:~$ ssh -v myname@myhostname.dyndns.org
OpenSSH_5.3p1 Debian-3ubuntu7, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to mek-403-jakbo-01.dyndns.org [80.63.5.243] port 22.
debug1: connect to address xxx.xxx.xxx.xxx port 22: Connection timed out
ssh: connect to host myhostname.dyndns.org port 22: Connection timed out

```

The problem persists if i substite the actual public ip adress for "myhostname.dyndns.org". Same result if I check port 22 on [http://www.canyouseeme.org](http://www.canyouseeme.org).

Further info:

I think I have the DynDNS part working, since I can resolve my ip with the 'host command' [1] and ddclient is running [2].
As for the ssh part, i have installed the openssh-client and openssh-server packages and succesfully gone through 
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring). 
The ssh daemon is running [3], it listens on port 22 [4], and i can succesfully log in with "shh localhost" [5].
Using firestarter i have set the firewall policy to "service=ssh, port=22, source=all" and allowing all incoming connections. This does not change the result. My computer is on a home network with a Netgear CVG824G wireless cable voice gateway.
 

How can I diagnose the problem further, and am I doing this right at all?
I have read that i need to set up port forwarding on my router. Is this correct? When doing this I can set values for (Name,strt port, end port, protocol,local ip adress) I put in "SSH","22","22","both" but I do not know what to give as local ip adress.
I will be grateful for any help, as this is the first time i am wrestling with networking stuff.



[1]
```
myname@mybox:~$ host myhostname.dyndns.org
myhostname.dyndns.org has address xxx.xxx.xxx.xxx

```
[2]
```
myname@mybox:~$ ps -ef | grep ddclient
root      2027     1  0 19:56 ?        00:00:00 ddclient - sleeping for 90 seconds
myname     4870  5562  0 22:00 pts/0    00:00:00 grep ddclient

```
[3]
```
myname@mybox:~$ ps -ef | grep sshd
root      1150     1  0 19:56 ?        00:00:00 /usr/sbin/sshd -D
myname     7571  5562  0 21:33 pts/0    00:00:00 grep sshd

```
[4]
```
myname@mybox:~$ sudo ss -lnp | grep sshd
0      128                           :::22                           :::*      users:(("sshd",1150,4))
0      128                            *:22                            *:*      users:(("sshd",1150,3))

```
[5]
```
myname@mybox:~$ ssh localhost
myname@localhost's password: 
Linux mybox 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:07:13 UTC 2011 x86_64 GNU/Linux
Ubuntu 10.04.3 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

If you want to download a file from a URL via the console, you can use the
command 'wget http://address/to/file.tar'

Last login: Tue Sep 20 21:41:13 2011 from localhost


```

---

### Post by Dangertux on 2011-09-20
Two things here.

1 - If you have a router you need to be port forwarding port 22 TCP. Additionally if you are behind the router, you will not be able to connect via the host name (due to the way NAT routing works it will fail at the router). The workarounds for this is running your own DNS server, or more easily adding a hosts file entry (/etc/hosts) something like this

```

192.168.1.12      mydns.dyndns.com

```*192.168.1.12 is the ip address of the machine running SSH on the LAN

Of course this won't actually test if the port forward works so  you will have to try to connect to it remotely, or use a portscanner like "canyouseeme" to verify port 22 is open.

2 -- You need to allow traffic to Port 22 TCP via ufw , if you have ufw enabled. Type the following to check if it is enabled

```

sudo ufw status

```If it is enabled, add the following rule to allow SSH traffic

```

sudo ufw allow from any to 192.168.1.12 port 22 proto tcp

```* 192.168.1.12 , is again the ip of the machine on the LAN running ssh server.

Additionally, you can limit this to say only computers on the 192.168.1.0 network by doing something like this

```

sudo ufw allow from 192.168.1.0/24 to 192.168.1.12 port 22 proto tcp

```This allows any machine on the 192.168.1.x network to connect to your SSH server but will deny the traffic from elsewhere.

Hope that is helpful.

---

### Post by bab1 on 2011-09-20
> **tjoff said:**
> I want to test it all on my own computer, in short: I want to connect to my own computer with ssh, but using DynDNS to resolve the ip adress. In the following xxx.xxx.xxx.xxx stands for an actual public ip adress.
  
The problem arises when i try to log in with DynDNS:

```
myname@mybox:~$ ssh -v myname@myhostname.dyndns.org
OpenSSH_5.3p1 Debian-3ubuntu7, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to mek-403-jakbo-01.dyndns.org [80.63.5.243] port 22.
debug1: connect to address xxx.xxx.xxx.xxx port 22: Connection timed out
ssh: connect to host myhostname.dyndns.org port 22: Connection timed out

```

The problem persists if i substite the actual public ip adress for "myhostname.dyndns.org". Same result if I check port 22 on [http://www.canyouseeme.org](http://www.canyouseeme.org).

Further info:

I think I have the DynDNS part working, since I can resolve my ip with the 'host command' [1] and ddclient is running [2].
As for the ssh part, i have installed the openssh-client and openssh-server packages and succesfully gone through 
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring). 
The ssh daemon is running [3], it listens on port 22 [4], and i can succesfully log in with "shh localhost" [5].
Using firestarter i have set the firewall policy to "service=ssh, port=22, source=all" and allowing all incoming connections. This does not change the result. My computer is on a home network with a Netgear CVG824G wireless cable voice gateway.
 

How can I diagnose the problem further, and am I doing this right at all?


Not 100% sure on this, but I believe your router will not let you connect to the WAN IP address from your local net.  This would be a security breach.  No non-routable (private IP) addresses should ever appear at a Public facing IP address.  In other words you can't make a u-turn and come back *to your local* network *from your local* network.

I would have a friend from outside test your network, or, better yet,  you test it from the local coffee shop.  :-)

---

### Post by papibe on 2011-09-21
The ability to connect to a machine from your local network using its public name, or IP, is called NAT loopback (read about it [here]("http://www.dyndns.com/support/kb/loopback_connections.html")). Unfortunately most routers don't support it.

The easiest way to test your setup is to go to a Internet cafe, public library, or even better, a friend's house. Another alternative is to use your pnone/tablet 3G connection (not WiFi).

Regards.

---

### Post by bab1 on 2011-09-21
> **papibe said:**
> The ability to connect to a machine from your local network using its public name, or IP, is called NAT loopback (read about it [here]("http://www.dyndns.com/support/kb/loopback_connections.html")). Unfortunately most routers don't support it.

The easiest way to test your setup is to go to a Internet cafe, public library, or even better, a friend's house. Another alternative is to use your pnone/tablet 3G connection (not WiFi).

Regards.

Yeah, that's it.  I can see why you would not want to provide NAT loopback for security reasons, but I can also see why it could be useful in testing.  I wonder if it can be switched on an off easily?

Edit:  Now that I think about it: NAT loopback would violate the non-routable private network address idea.  Wouldn't it be routing the packets from the private net to the public side?  It's only 1 hop, but it is a hop!  :D

---

### Post by Dangertux on 2011-09-21
> **bab1 said:**
> Yeah, that's it.  I can see why you would not want to provide NAT loopback for security reasons, but I can also see why it could be useful in testing.  I wonder if it can be switched on an off easily?

Edit:  Now that I think about it: NAT loopback would violate the non-routable private network address idea.  Wouldn't it be routing the packets from the private net to the public side?  It's only 1 hop, but it is a hop!  :D

Yeah it's a hop with pretty big implications :-P

---

### Post by agillator on 2011-09-21
People are correct when they say your computers ip address is not the address you want. However, if you will log into your router you should find that you can set a dynamic dns function. If you will set that up, then the router (not your computer) will update your dynamic dns server (dyndns in this case) when your INTERNET ip address changes. Then set your router to give your computer a static address on the LAN and forward port 22 (or any port to port 22 on that address). Then you will be in business. Note you may have to do the same for your parents depending on their setup.

---

### Post by tjoff on 2011-09-21
First, thanks for all the answers guys!
I clearly have a lot to learn about networking, as i struggle to understand some what you are writing, but I appreciate it nonetheless.

@Dangertux:
Have I understood it correctly that the ip adress in the /etc/hosts file has to be the same ip that I get from running ifconfig?
I run
```
myname@mybox:~$ sudo ufw status
[sudo] password for myname: 
Status: inactive
```
Does this mean that i can rule out any firewall interference (from the computers firewall, that is)?

@bab1,papipe:
Even though I do not really understand the details, I understand so much that what I wanted to do is not that simple nor secure.
About having a friend test for me. I have remote access (ssh) to a university computer. Can I test the setup by logging onto this computer and then ssh back to my own machine, or will that give the same problem?

@agillator:
It seems that the netgear cvg824g v2 router does not have an option to use dynamic dns. There is no documentation for this model on Netgear.com, and i read in some forum that this model is made specific to my ISP and crippled by design, dont know it is true. Does it make sense to follow the rest of your advice without this step?


If I forget the whole dynamic dns thing for know, and just want to open port 22, I have checked that ufw is inactive, i have enabled port forwarding on port 22 in the router (to the local ip i get from 'ifconfig', is this right?), i have nothing in /etc/hosts.deny.
Still canyouseeme.org tells me that the connnection to port 22 times out.
What other things should i check?

---

### Post by agillator on 2011-09-22
OK, I can see this is not going to be an easy solution; may the fleas of a thousand camels infest your isp's armpits! I assume you have done nothing special to your router and it will still have its default address - could we be so lucky? Go to 192.168.0.1 in your browser. That should be, hopefully is, the default address of your cable modem/router/etc/etc. If it is, take a few minutes and prowl the menus it will offer. Find out what is there and what it will do, even if you don't understand everything. If that is not its address let us know and we'll try to find it using nmap or something. The other thing to do is check your firewall to make sure your problem is at the router, not your machine. Open a terminal and enter 'sudo iptables -L -v -n --line-numbers' (without the quotes, of course). If you want to and are in a directory you have write permissions to you can use 'sudo iptables -L -v -n --line-numbers > rules' and then open the resulting file named rules. Hopefully there won't be much there. If there is, look for two things in the chain named INPUT. See what the default policy is, it should be either ACCEPT or DROP. Also see if there is any rule in there, if there are any rules containing something like 'dport 22' or 'destport 22' or anything else referring to port 22. Answer these questions and we will know how to proceed. Of course there is always the bigger hammer approach - if at first you don't succeed, get a bigger hammer!

---

### Post by tjoff on 2011-09-24
Hi agillator.

Thanks for taking your time to answer me.

I wrote the support of my ISP and they confirmed that it is not possible to set up DDNS on my type of modem. Without me even having to ask, they wrote that a new modem with DDNS-capability is underway in the mail, at no extra charge.
So please recall the camel fleas!

The 'Chain INPUT' section of the output of 'sudo iptables -L -v -n --line-numbers' is listed below. So there is _something_ in there, but nothing related directly to port 22.

```
myname@mybox:~$ sudo iptables -L -v -n --line-numbers
Chain INPUT (policy DROP 0 packets, 0 bytes)
num   pkts bytes target     prot opt in     out     source               destination         
1        0     0 ACCEPT     tcp  --  *      *       193.162.153.164      0.0.0.0/0           tcp flags:!0x17/0x02 
2     1233  369K ACCEPT     udp  --  *      *       193.162.153.164      0.0.0.0/0           
3        0     0 ACCEPT     tcp  --  *      *       194.239.134.83       0.0.0.0/0           tcp flags:!0x17/0x02 
4        1   247 ACCEPT     udp  --  *      *       194.239.134.83       0.0.0.0/0           
5       60  2520 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
6        0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
7        0     0 DROP       all  --  wlan0  *       0.0.0.0/0            255.255.255.255     
8       52 11172 DROP       all  --  *      *       0.0.0.0/0            192.168.0.255       
9        0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
10       0     0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
11       0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
12       0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
13      10   436 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
14       0     0 LSI        all  -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
15    118K  154M INBOUND    all  --  wlan0  *       0.0.0.0/0            0.0.0.0/0           
16       0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
17       0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 
```

I am not sure how to interpret this, but rule number 7 looks to me as if it could be the culprit. Am I on the right track?

---

### Post by agillator on 2011-09-25
OK, fleas recalled. Actually, I am shocked! An ISP who knows something and is willing to do something about it! Wow.

Rule 7 is simply dropping broadcast stuff - the 255.255.255.255 address is a general address like 'Occupant', one address to use so many machines will pick it up except we all block it. It looks like port 22 is open with no problem. So, install the new modem/router when it arrives, set up DDNS on it and see what happens. Hopefully that will fix the problem because then your modem/router will notify your DNS people anytime your internet ip changes. Of course you will have to forward port 22 to your machine, but I think you already know that. 

Let us know how it goes. Nothing is ever simple - Murphy is alive and well.

---

### Post by tjoff on 2011-09-25
I too was surprised to put it mildly. After having filled out an online support form, I had prepared myself for some weeks of waiting, a standardized answer not adressing my question, being rerouted to various corners of the support, and finally being told "sorry, we cant help you".
I was so happy to be proved a cynic this time :-)

I will watch my mailbox and follow your instructions when the modem arrives, and give a followup here if I think there is a chance that others can learn from it.  Thanks a lot for your help so far!

---

