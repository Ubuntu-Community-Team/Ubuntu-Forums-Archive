---
title: "Can't ssh into my computer--says no route to host"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by BetterSense on 2010-04-11
I have 3 computers on a local home network. Computer 1 is not receiving incoming anything from other computers on the network, and I don't know why. The regular internet works fine.

Computer 1 can ping and ssh into either 2 or 3. 2 can ping and ssh into 3 and vice versa. But nothing can ping OR ssh into 1. Trying to do so says "no route to host".

All computers are running Ubuntu Karmic. I don't even know where to start figuring out what's causing this, but it's probably something simple. I'm using the IPs I found listed in my wireless router's web-based control panel.

---

### Post by stilling on 2010-04-11
you installed the openssh server and client ?
if yes see if no firewall bloks your port 
/etc/init.d/sshd status see if is running
iptables -L see if firewall bloks


hope this helps

---

### Post by BetterSense on 2010-04-11
> see if no firewall bloks your port 
How can I do that? *is noob*

```
sudo iptables -L
[sudo] password for chaz: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
chaz@c1:~$ 
```

What does that mean?

---

### Post by souki on 2010-04-11
please, show us the output from these commands (all hosts) :

```
ifconfig -a 
route -n
```

---

### Post by Iowan on 2010-04-11
Hmmm... I've seen one-direction ping problem thread(s) before, but don't remember where - or how/if the problem got solved.

---

### Post by BetterSense on 2010-04-11
Here is the output from the computer that is having the problem:



```
chaz@brutus:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:30:8d:1e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:32 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:191 errors:0 dropped:0 overruns:0 frame:0
          TX packets:191 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23130 (23.1 KB)  TX bytes:23130 (23.1 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:fa:3c:91  
          inet addr:192.168.1.73  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:3fff:fefa:3c91/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:162407 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135062 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:141475254 (141.4 MB)  TX bytes:22445461 (22.4 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-17-3F-FA-3C-91-00-00-00-00-00-00-00-00-00
-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

chaz@brutus:~$ 
```
```

chaz@brutus:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
chaz@brutus:~$
```

---

### Post by stilling on 2010-04-12
sorry for my answer but i just try to play safe is your computer on risc
hope that don`t mind for that

and see this post [HERE]("http://www.linuxquestions.org/questions/linux-networking-3/ssh-no-route-to-host-also-ping-problem-645496/") maybe it will help you a little more

---

### Post by souki on 2010-04-12
> **BetterSense said:**
> Here is the output from the computer that is having the problem:


please, repeat this on all three hosts.

---

### Post by BetterSense on 2010-04-12
Have to work so no time to boot the other one, but but here it is from one of the other computers:
```

chaz@singularity:~/documents/nanowires$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:68:f2:96:c1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:23:4d:64:bd:51  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4dff:fe64:bd51/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5889 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6617932 (6.6 MB)  TX bytes:872427 (872.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-23-4D-64-BD-51-36-34-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

chaz@singularity:~/documents/nanowires$
```

```
chaz@singularity:~/documents/nanowires$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
chaz@singularity:~/documents/nanowires$
```

---

### Post by 98cwitr on 2010-04-12
are you trying to ping via hostname or IP?

---

### Post by BetterSense on 2010-04-12
I tried both, but mostly IP. Tried ssh <ip>, ssh chaz@<ip>, tried ssh <hostname>, tried ssh chaz@<hostname>

---

### Post by _0R10N on 2010-04-12
What does /etc/init.d/ssh status (in that computer) tells you??

---

### Post by 98cwitr on 2010-04-12
do a traceroute...does it hit the router at all?

---

### Post by BetterSense on 2010-04-12
> What does /etc/init.d/ssh status (in that computer) tells you??

I'm at work now but I'll do it when I get home. I could ssh in but...yeah.

---

### Post by BetterSense on 2010-04-12
For absolutely no apparently reason, now it works. I can now ssh into the problematic computer using either hostname or IP.

---

### Post by Iowan on 2010-04-12
You might want to give it a couple of days (and/or reboots) before you mark the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")... ;)

---

### Post by souki on 2010-04-13
compare the ip addr you get from your router control panel, and the one you get from the ifconfig command.
are you sure it is correct ?

singularity:192.168.1.67
brutus: 192.168.1.73

---

### Post by BetterSense on 2010-04-14
It worked for a couple days, but it's doing it again. Same deal. 

> ssh: connect to host brutus port 22: No route to host

This time, I can ssh into brutus from my home-theater PC, but not from my laptop. I can ssh from my laptop into my HTPC and then ssh into brutus that way, but that's hardly fixing the problem. Although I could probably write a script to do that....

Now, in the meantime, since it worked for a day or so, I set up a NFS share so that the ~/video folder of the problematic computer gets mounted to my home-theater computer upon boot. Although my home theater computer hasn't been rebooted, I can still play videos and modify files with mv and so on on the mounted network share. For what that's worth, since ssh works fine on that system now. Just not from the laptop.

Does anyone have even the slightest idea why this is happening? Is it a bug? Most posts have been like "show us the output of _" but then crickets. I take that to mean everybody else is going "wtf" too.


> chaz@singularity:~$ ssh brutus
ssh: connect to host brutus port 22: No route to host
chaz@singularity:~$ ping brutus
PING brutus (192.168.1.72) 56(84) bytes of data.
From singularity (192.168.1.67) icmp_seq=1 Destination Host Unreachable
From singularity (192.168.1.67) icmp_seq=2 Destination Host Unreachable
From singularity (192.168.1.67) icmp_seq=3 Destination Host Unreachable
^C
--- brutus ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3013ms
, pipe 3
chaz@singularity:~$ ssh argus
chaz@argus's password: 
Linux argus 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)

Last login: Wed Apr 14 00:21:52 2010 from singularity
chaz@argus:~$ ssh brutus
chaz@brutus's password: 
Permission denied, please try again.
chaz@brutus's password: 
Linux brutus 2.6.31-20-server #58-Ubuntu SMP Fri Mar 12 05:40:05 UTC 2010 x86_64

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)

Last login: Wed Apr 14 00:26:28 2010 from argus
chaz@brutus:~$ wtf?
No command 'wtf?' found, did you mean:
 Command 'wtf' from package 'bsdgames' (universe)
wtf?: command not found

...

chaz@singularity:~$ traceroute brutus
traceroute to brutus (192.168.1.72), 30 hops max, 60 byte packets
 1  singularity (192.168.1.67)  3001.242 ms !H  3001.233 ms !H  3001.229 ms !H
chaz@singularity:~$ ssh brutus
ssh: connect to host brutus port 22: No route to host
chaz@singularity:~$ 



By the way, pay no attention to the earlier IP address values I posted in the terminal output or otherwise. The directly above values are the current and longstanding values. I was concerned about security so I flipped some digits when I made the earlier posts. My friend assures me there is no problem posting my IPs.

---

### Post by Iowan on 2010-04-14
> **BetterSense said:**
>  My friend assures me there is no problem posting my IPs.The following ranges are considered "private", so you should be safe using them on your network and revealing them:> The main class groups are
Class A: IP Range - 10.0.0.0 to 10.255.255.255
Class B: IP Range - 172.16.0.0 to 172.31.255.255
Class C: IP Range - 192.168.0.0 to 192.168.255.255

**singularity** has a **route -n** similar to **argus**?

---

