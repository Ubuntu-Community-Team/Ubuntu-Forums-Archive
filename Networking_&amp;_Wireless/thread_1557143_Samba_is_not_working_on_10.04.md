---
title: "Samba is not working on 10.04"
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by franciskus on 2010-08-20
I dont know what happened but samba stopped working and now I cant get it up again.

I dont know what to do, when I try to start it says:
```
$ sudo /etc/init.d/samba restart
sudo: /etc/init.d/samba: command not found
```

---

### Post by walter_j on 2010-08-20
> **franciskus said:**
> I dont know what happened but samba stopped working and now I cant get it up again.

I dont know what to do, when I try to start it says:
```
$ sudo /etc/init.d/samba restart
sudo: /etc/init.d/samba: command not found
```

I had that for awhile too. I installed latest updates which included samba and haven't had the problem again.

---

### Post by CharlesA on 2010-08-20
samba is still in the /etc/init.d/ directory, but it's listed as smbd and nmbd.

To restart samba, you would use this:

```
sudo service smbd restart; sudo service nmbd restart
```

To check the status you can use this:

```
sudo service smbd status
```

To see if it's running.

---

### Post by franciskus on 2010-08-20
Thanks a lot, now I can 'see' it from machines with windows.

Question: how/were do I set it to do this on boot?

---

### Post by CharlesA on 2010-08-20
It should start automatically after bootup.

Reboot and run that status command to see if it's running. :)

---

### Post by franciskus on 2010-08-20
Ok, thanks, but what status command would be that? (I am kind a newbie on this)

---

### Post by arubislander on 2010-08-20
> **CharlesA said:**
> 
To check the status you can use this:

```
sudo service smbd status
```

To see if it's running.

^^

---

### Post by Thomas Garman on 2010-08-20
deleted

---

### Post by Morbius1 on 2010-08-20
> **Thomas Garman said:**
> you have to be sure to install libapache2.2 and libapache2.2-dns-mod or something like that to get it to work too.  Google it.  Without those installed you will "see" the other computers but you will never get them to mount.

Look, I don't know how many people have to tell you this but what you are talking about is "Personal File Sharing." 

[COLOR=Blue]**Personal File Sharing has nothing to do with Samba.**[/COLOR] 

And BTW those two packages are incorrect for Personal File Sharing. So if you going to give bad information at least get the required dependencies correct. Go into synaptic , search for gnome-user-share, and read the description, and dependencies - no mention of Samba.

---

### Post by CharlesA on 2010-08-20
> **Thomas Garman said:**
> you have to be sure to install libapache2.2 and libapache2.2-dns-mod or something like that to get it to work too.  Google it.  Without those installed you will "see" the other computers but you will never get them to mount.

Huh? All the dependencies for Samba are installed when you install it.

EDIT: Thanks Morbius1.

---

### Post by franciskus on 2010-08-20
Ok, I restarted and now it is worse, I can't see windows machines neither windows machines can see Ubuntu shared folders.

Checking status:```
francisco@francisco-desktop:~$ sudo service smbd status
[sudo] password for francisco: 
smbd start/running, process 926

```When I go to Networking folder I just see an icon with 'Windows network' if I click on it says 'was not possible to mount localization' (something like, I am translating)

---

### Post by CharlesA on 2010-08-20
Make sure nmbd is also running.

```
sudo service nmbd status
```

---

### Post by franciskus on 2010-08-20
Ok, there we go:```
~$ sudo service nmbd status
nmbd start/running, process 3166

```

---

### Post by sikander3786 on 2010-08-20
Hi.

Just thinking everyone has been concentrating on to see if "smbd" and "nmbd" are running. My opinion, did you have another look at your configuration file? Post it to get it rechecked. Also, can you ping from Windows box to Ubuntu and vice versa?

---

### Post by Morbius1 on 2010-08-20
It almost sounds like a firewall is in the way, doesn't it?

You might want to use the following command to see if the required ports are open:
```
sudo nmap -sS -sU -T4 192.168.0.100
```Run it a couple of times changing 192.168.0.100 to the ip address of one of the machines you're trying to access and again on the machine you're trying to access it from.

---

### Post by franciskus on 2010-08-20
To the machine I am (ubuntu):```
~$ sudo nmap -sS -sU -T4 192.168.1.100

Starting Nmap 5.00 ( http://nmap.org ) at 2010-08-20 15:26 BRT
Interesting ports on 192.168.1.100:
Not shown: 1987 closed ports
PORT     STATE         SERVICE
25/tcp   open          smtp
80/tcp   open          http
111/tcp  open          rpcbind
139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
901/tcp  open          samba-swat
2049/tcp open          nfs
68/udp   open|filtered dhcpc
111/udp  open|filtered rpcbind
137/udp  open|filtered netbios-ns
138/udp  open|filtered netbios-dgm
2049/udp open|filtered nfs
5353/udp open|filtered zeroconf

Nmap done: 1 IP address (1 host up) scanned in 1.56 seconds

```To the machine with windows:```
~$ sudo nmap -sS -sU -T4 192.168.1.106

Starting Nmap 5.00 ( http://nmap.org ) at 2010-08-20 15:28 BRT
Interesting ports on 192.168.1.106:
Not shown: 1000 open|filtered ports, 991 filtered ports
PORT     STATE  SERVICE
135/tcp  open   msrpc
139/tcp  open   netbios-ssn
445/tcp  open   microsoft-ds
1036/tcp open   unknown
1801/tcp open   unknown
2103/tcp open   zephyr-clt
2105/tcp open   eklogin
2107/tcp open   unknown
2869/tcp closed unknown
MAC Address: 00:13:E8:72:AA:A3 (Intel Corporate)

Nmap done: 1 IP address (1 host up) scanned in 9.43 seconds

```

---

### Post by CharlesA on 2010-08-20
Did you scan the ubuntu box from the windows one?

---

### Post by franciskus on 2010-08-20
> **sikander3786 said:**
> Hi.

Just thinking everyone has been concentrating on to see if "smbd" and "nmbd" are running. My opinion, did you have another look at your configuration file? Post it to get it rechecked. Also, can you ping from Windows box to Ubuntu and vice versa?Yes, I can ping from each other to each other.

---

### Post by Morbius1 on 2010-08-20
I'm fairly certain ports 137 and 138 - UDP need to be open on all the machines. It's used by nmbd. Has there been a change in the firewall settings on the windows boxes?

You could try disabling the Windows firewall temporarily just to see if it brings back the connection.

---

### Post by franciskus on 2010-08-20
> **CharlesA said:**
> Did you scan the ubuntu box from the windows one?
Right at this moment YES, but somehow it just stops working or when I start the machine it is not working.

---

### Post by CharlesA on 2010-08-20
> **franciskus said:**
> Right at this moment YES, but somehow it just stops working or when I start the machine it is not working.

Strange. It sounds like a firewall thing.

---

### Post by Thomas Garman on 2010-08-20
deleted

---

### Post by franciskus on 2010-08-20
> **CharlesA said:**
> Strange. It sounds like a firewall thing.I am pretty sure this happened after a linux updating (today linux-headers or something like that).
Strange is that I can ping them.

---

### Post by CharlesA on 2010-08-20
> **Thomas Garman said:**
> Well, you might think all of the dependencies are downloaded and installed but in fact I was never able to get mount the other file systems and share anything until I did:
 
sudo aptitude install apache2.2-bin apache2.2-common libapache2-mod-dnssd
 
with SAMBA and I couldn't care less if you think that Lucid allows Personal File sharing between Ubuntu systems without SAMBA because it simply never worked AT ALL for me until I installed SAMBA and installed:
 
sudo aptitude install apache2.2-bin apache2.2-common libapache2-mod-dnssd
 
Good lord you could just google how to file share with Ubuntu anyway so why would you post onto a forum for it.  Sheesh.
 
What a waste of time.

Those packages install the Apache HTTP server. You don't need those if you use Samba. We ***aren't*** talking about "Personal File Sharing" either.

@franciskus: Can you post the output of this:

```
sudo iptables -L
```

---

### Post by franciskus on 2010-08-20
here it is:```
~$ sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootps 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootpc 
ufw-skip-to-policy-input  all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            state INVALID limit: avg 3/min burst 10 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state NEW 
ACCEPT     udp  --  anywhere             anywhere            state NEW 

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:51413 
ACCEPT     tcp  --  anywhere             anywhere            multiport dports loc-srv,netbios-ssn,microsoft-ds 
ACCEPT     udp  --  anywhere             anywhere            multiport dports netbios-ns,netbios-dgm 

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination         
francisco@francisco-desktop:~$ 

```

---

### Post by CharlesA on 2010-08-20
OK, try this:

```
sudo ufw disable
```

Then scan it with nmap and see if you can connect.

---

