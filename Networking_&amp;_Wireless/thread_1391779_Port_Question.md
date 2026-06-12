---
title: "Port Question"
date: 2010-01-27
forum: Networking &amp; Wireless
---

### Post by moore.bryan on 2010-01-27
I have an external hd attached to my one computer at home, use DynDNS to give it a static address, and can usually ssh into the machine fine. I ran update a few days ago and now have the much-aligned "connection reset by peer" error. I checked the machine and made sure everything was "normal;" e.g., checked ssh config for the port change (correct), doubled-checked ufw to make sure the port was open (it was), etc. I ran nmap on the machine and it said the port was open.

This morning when I arrived at work, I ran nmap on my machine here where I've been unable to connect and its results were a little surprising: the port I specified at home and was demonstrated as open is not. WTF?

Any ideas where I can start troubleshooting this?

---

### Post by Rob_H on 2010-01-27
Many corporate firewalls restrict outbound ports. allowing only HTTP (80 and 443) and a handful of others, for example. Could that be happening here? One thing you can try is moving the external port of your SSH service to port 80 and see if it makes a difference. Also, double-check to make sure you're going to the correct public IP address. Have someone at home recite the current IP address to you and then try to connect to that machine by IP address rather than name to eliminate any potential DNS problem.

---

### Post by moore.bryan on 2010-01-27
Thanks for the response, Rob_H... I've already changed my port (to 5101) and have checked; it is open on all assorted connections. Except, that is, the one that tells me it's not open although it is. ;-)

---

### Post by Rob_H on 2010-01-27
If your corporate firewall is restricting destination ports, just moving the service to another random port isn't going to help. Try moving it to 80.

---

### Post by moore.bryan on 2010-01-27
Sorry, Rob_H, I think I may have not explained my issue fully. My work *does not* block port 5101 in *any* way. I know this: one, because I asked and, two, because I used sshfs up until *yesterday* just fine. The *only* thing different is the updates on the computer at my house. *That's *what's truly irritating, since all the diagnostics on that machine tell me 5101 is open and good...

---

### Post by Rob_H on 2010-01-27
OK, the next thing I would try then is to run a packet capture program on the server box to see if any of the traffic from outside the LAN is reaching it. You can use [Wireshark]("http://www.wireshark.org/") or [tcpdump]("http://www.tcpdump.org/") for this. This test will enable you to tell whether the traffic is getting rejected at the host or somewhere in the network.

---

### Post by moore.bryan on 2010-01-27
I should set Wireshark to run on the server machine tomorrow morning and attempt to log-in from work when I get here, checking the logs when I get home tomorrow evening?

Or... I could just try and ssh into the machine from home, right.... I'm an idiot.

---

### Post by Rob_H on 2010-01-27
> **moore.bryan said:**
> I should set Wireshark to run on the server machine tomorrow morning and attempt to log-in from work when I get here, checking the logs when I get home tomorrow evening?

Yes, or get a friend to help you. Have them try to log in from outside your network while you're watching Wireshark.

> **moore.bryan said:**
> Or... I could just try and ssh into the machine from home, right.... I'm an idiot.

I thought you said that works fine...?

---

### Post by moore.bryan on 2010-01-27
> **Rob_H said:**
> Yes, or get a friend to help you. Have them try to log in from outside your network while you're watching Wireshark.
That's what I thought...

> I thought you said that works fine...?
At home does work fine; I confused myself, but now I'm all better.

---

### Post by moore.bryan on 2010-01-29
Okay, let's--possibly--complicate matters.

I went to Starbucks yesterday and easily, as well as successfully, ssh'd into my home server. Hmm. When I got into work today, I used by Asus to try and ssh into the server, thinking it may be the laptop at work. Connection refused. I ran nmap and it *insists* 5101 is open and my IT department tells me it's open.

Huh?

---

### Post by Rob_H on 2010-01-29
> **moore.bryan said:**
> Okay, let's--possibly--complicate matters.

I went to Starbucks yesterday and easily, as well as successfully, ssh'd into my home server. Hmm. When I got into work today, I used by Asus to try and ssh into the server, thinking it may be the laptop at work. Connection refused. I ran nmap and it *insists* 5101 is open and my IT department tells me it's open.

Huh?

Interesting. But again, the Wireshark test is crucial to see if the traffic from work is hitting the server at home. If it is, then some setting on the server is refusing the connection (iptables/netfilter, hosts.allow, hosts.deny, etc.) But if the traffic isn't reaching it, it is something in the network.

---

### Post by CharlesA on 2010-01-29
Stupid question, but have you tried connected using the IP address from yer work machine?

---

### Post by moore.bryan on 2010-01-29
> **Rob_H said:**
> Interesting. But again, the Wireshark test is crucial to see if the traffic from work is hitting the server at home. If it is, then some setting on the server is refusing the connection (iptables/netfilter, hosts.allow, hosts.deny, etc.) But if the traffic isn't reaching it, it is something in the network.
Wireshark gave me *so* much information; how should I sort it out to even know what's relevant?

> **CharlesA said:**
> Stupid question, but have you tried connected using the IP address from yer work machine?
Yup.

---

### Post by Rob_H on 2010-01-29
> **moore.bryan said:**
> Wireshark gave me *so* much information; how should I sort it out to even know what's relevant?


You can restrict the capture to just your SSH traffic by going to Capture > Options. Pick your network interface from the dropdown (e.g. "eth0"). Uncheck "Capture packets in promiscuous mode". Then, in the edit box next to the capture filter button, type in "port 22" (or whatever local port the router is forwarding SSH packets to). Then click "Start".

You should now be capturing ONLY the SSH traffic going to/from the box. You won't be able to read it because it's encrypted, of course. But the point is just to see if traffic from work is getting that far. If it is, you should see some packets show up where the source column matches the public IP address of your work machine (or corporate firewall).

Test it first by connecting from within the LAN. Good luck!

---

### Post by moore.bryan on 2010-01-29
Once, again, perhaps this confuses the issue...

Running nmap on my localhost (127.0.0.1) returns only port 631 open; running it on the ip address given to me by my work connection (172.31.8.44) tells me no ports are open; running it on the ip address of my proxy server at work tells me a number of ports are open, including 5101.

---

### Post by moore.bryan on 2010-01-29
> **Rob_H said:**
> You can restrict the capture to just your SSH traffic by going to Capture > Options. Pick your network interface from the dropdown (e.g. "eth0"). Uncheck "Capture packets in promiscuous mode". Then, in the edit box next to the capture filter button, type in "port 22" (or whatever local port the router is forwarding SSH packets to). Then click "Start".

You should now be capturing ONLY the SSH traffic going to/from the box. You won't be able to read it because it's encrypted, of course. But the point is just to see if traffic from work is getting that far. If it is, you should see some packets show up where the source column matches the public IP address of your work machine (or corporate firewall).

Test it first by connecting from within the LAN. Good luck!
Thanks, Rob_H, for *all* your help. I'll try this on the weekend and post back.

---

### Post by moore.bryan on 2010-02-01
Well, it would seem my troubles are multiple. It turns-out, I've got several layers of "protection," each with their own ports open. The ip my ap gives me (172.16.254.183), my proxy (172.16.0.9), and the isp ip for the building (209.114.152.12) all have different ports open, now. So, basically, my IT department "doesn't know" which ports are open and which aren't.

So much for easy sshfs from work...

---

### Post by moore.bryan on 2010-02-12
> **Rob_H said:**
> You can restrict the capture to just your SSH traffic by going to Capture > Options. Pick your network interface from the dropdown (e.g. "eth0"). Uncheck "Capture packets in promiscuous mode". Then, in the edit box next to the capture filter button, type in "port 22" (or whatever local port the router is forwarding SSH packets to). Then click "Start".

You should now be capturing ONLY the SSH traffic going to/from the box. You won't be able to read it because it's encrypted, of course. But the point is just to see if traffic from work is getting that far. If it is, you should see some packets show up where the source column matches the public IP address of your work machine (or corporate firewall).

Test it first by connecting from within the LAN. Good luck!
Wireshark tells me "port 22" is an "invalid filter." Huh?

---

### Post by Rob_H on 2010-02-12
> **moore.bryan said:**
> Wireshark tells me "port 22" is an "invalid filter." Huh?

Make sure your caption options screen looks something like this. (Your network interface name may vary.)
[ATTACH]146867[/ATTACH]

---

### Post by moore.bryan on 2010-02-14
Now it works, for some *mysterious* reason... just to get back into work and test it!

---

### Post by moore.bryan on 2010-02-17
So, there's *no* traffic hitting my home computer. The results of nmap on several ip's at work confuse me:
nmap for ip address WhatIsMyIPAddress.com reports:
```

Starting Nmap 5.00 ( http://nmap.org ) at 2010-02-09 13:35 EST
Interesting ports on 216.162.89.14:
Not shown: 846 closed ports, 153 filtered ports
PORT   STATE SERVICE
53/tcp open  domain
Device type: proxy server|storage-misc
Running (JUST GUESSING) : Blue Coat SGOS 5.X (86%), FreeBSD 6.X (85%)
Aggressive OS guesses: Blue Coat SG210 proxy server (SGOS 5.2.3.3 - 5.2.3.9) (86%), FreeNAS 0.69RC2 (FreeBSD 6.4-RELEASE) (85%)
No exact OS matches for host (test conditions non-ideal).

OS detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 6.56 seconds

```
nmap on proxy:
```

Starting Nmap 5.00 ( http://nmap.org ) at 2010-02-09 13:36 EST
Interesting ports on bluecoat.artemis-fowl.org (172.16.0.9):
Not shown: 989 closed ports
PORT     STATE SERVICE
20/tcp   open  ftp-data
21/tcp   open  ftp
22/tcp   open  ssh
53/tcp   open  domain
80/tcp   open  http
5050/tcp open  mmcc
5101/tcp open  admdog
5190/tcp open  aol
8080/tcp open  http-proxy
8082/tcp open  blackice-alerts
8100/tcp open  unknown
Device type: proxy server
Running: Blue Coat SGOS 5.X
OS details: Blue Coat SG810 web proxy (SGOS 5.3.1.9)
Network Distance: 2 hops

OS detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 8.94 seconds

```
nmap on ip address given to me by the network:
```

Starting Nmap 5.00 ( http://nmap.org ) at 2010-02-09 13:37 EST
All 1000 scanned ports on hs-bmoorez61.admin.artemis-fowl.org (172.31.8.44) are closed
Too many fingerprints match this host to give specific OS details
Network Distance: 0 hops

OS detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 1.91 seconds

```
nmap on my localhost:
```

Starting Nmap 5.00 ( http://nmap.org ) at 2010-02-09 13:37 EST
Interesting ports on localhost (127.0.0.1):
Not shown: 999 closed ports
PORT    STATE SERVICE
631/tcp open  ipp
No exact OS matches for host (If you know what OS is running on it, see http://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=5.00%D=2/9%OT=631%CT=1%CU=31840%PV=N%DS=0%G=Y%TM=4B71AB70%P=i686-
OS:pc-linux-gnu)SEQ(SP=C9%GCD=1%ISR=D3%TI=Z%CI=Z%II=I%TS=8)SEQ(SP=C8%GCD=1%
OS:ISR=D3%TI=Z%CI=Z%II=I%TS=8)OPS(O1=M400CST11NW6%O2=M400CST11NW6%O3=M400CN
OS:NT11NW6%O4=M400CST11NW6%O5=M400CST11NW6%O6=M400CST11)WIN(W1=8000%W2=8000
OS:%W3=8000%W4=8000%W5=8000%W6=8000)ECN(R=Y%DF=Y%T=40%W=8018%O=M400CNNSNW6%
OS:CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=Y%DF=Y%T=40%W
OS:=8000%S=O%A=S+%F=AS%O=M400CST11NW6%RD=0%Q=)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%
OS:F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y
OS:%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%R
OS:D=0%Q=)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)I
OS:E(R=Y%DFI=N%T=40%CD=S)

Network Distance: 0 hops

OS detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 13.79 seconds

```

---

