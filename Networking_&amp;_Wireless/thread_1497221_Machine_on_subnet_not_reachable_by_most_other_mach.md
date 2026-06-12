---
title: "Machine on subnet not reachable by most other machines"
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by pdxrlk on 2010-05-30
Hi - 

I have a problem where one of my Ubuntu machines is no longer reachable by all other machines on my subnet except for one machine, my backup server.

Machines:

[LIST]
[*]A: Ubuntu.   Can ping all machines including B.  Backups run on this machine and it does an rsync to all other machines on a daily basis.
[*]B: Ubuntu.   Can ping all machines
[*]C: Ubuntu.   Can ping all machines except B.
[*]D. Mac.       Can ping all machines except B.
[*]E.  etc. can ping all machines except B.
[/LIST]

All machines are on a wireless subnet with static IPs.   

So - B is not pingable by IP address, nor by name, except from machine A.  I cannot ssh to B either, except from A.   However, this is the strange part  , if I log in to B and ping C, then voila, I can now ping B from C.  Now I have a happy interconnected network, however after a period of time B will 'go dark' again and not be visible from any machines except A.

I seem to have two clues here:


[LIST]
[*]A runs backups and perhaps this activity is keeping its connection to B alive in some way.
[*]All the other machines connect to B sporadically (once every few days) but when they try, B is not reachable.
[/LIST]
Thanks for any pointers on how to debug this one.

---

### Post by Iowan on 2010-05-30
Some of the symptoms have me confused.  :confused:
> # All the other machines connect to B sporadically (once every few days) but when they try, B is not reachable.
The difference between *connect* and *reach*.

I don't understand why one machine would be successful - otherwise, I'd wonder if a power-save option is disabling the interface.I can't remember if **acpi** or **apic** (or something similar-sounding) might be responsible.

---

### Post by pdxrlk on 2010-05-31
Sorry, let me try again.  Thanks for replying.

B is a server which I generally don't need to log in to.   It gets backed up by A on a daily basis (rsync via cron job).   From A I can ping and ssh to B at any time - it always works.

All the other machines on my network are laptops/desktops.  From these laptops/desktops I try to log in to B occasionally to write code, check on workloads, etc.   This is where the problem is - usually I cannot ping nor ssh B from any laptop/desktop.  I need to ssh to A first, and then ssh to B.     From this ssh xterm, if I ping back to the laptop I'm using (let's call it C), then voila, I can ssh/ping from C to B without problem (and I can continue doing so until the next morning when I have to do this little dance again).

Bizarre, eh?  

All machines have an identical copy of /etc/hosts.

---

### Post by Iowan on 2010-05-31
> **pdxrlk said:**
> Bizarre, eh?  
Yeah, that pretty much describes it...
I could envision a machine that flushes it's logs periodically, and refuses to acknowledge any (incoming) machine not in it's logs. "A" server makes frequent contact and stays in the log. Outgoing connections are permitted - and the target gets added to logs, thus target can then make direct contact.

This is all speculation - and I've no idea which log or which program. Does "B" run a firewall?

---

### Post by pdxrlk on 2010-05-31
> **Iowan said:**
> . Does "B" run a firewall?

This is pretty vanilla Ubuntu, and I'm AFAIK I am only using iptables as it popped out of the womb:

```

% iptables -L -v
Chain INPUT (policy ACCEPT 371K packets, 258M bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     udp  --  virbr0 any     anywhere             anywhere            udp dpt:domain 
    0     0 ACCEPT     tcp  --  virbr0 any     anywhere             anywhere            tcp dpt:domain 
    0     0 ACCEPT     udp  --  virbr0 any     anywhere             anywhere            udp dpt:bootps 
    0     0 ACCEPT     tcp  --  virbr0 any     anywhere             anywhere            tcp dpt:bootps 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  any    virbr0  anywhere             192.168.122.0/24    state RELATED,ESTABLISHED 
    0     0 ACCEPT     all  --  virbr0 any     192.168.122.0/24     anywhere            
    0     0 ACCEPT     all  --  virbr0 virbr0  anywhere             anywhere            
    0     0 REJECT     all  --  any    virbr0  anywhere             anywhere            reject-with icmp-port-unreachable 
    0     0 REJECT     all  --  virbr0 any     anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTPUT (policy ACCEPT 333K packets, 267M bytes)
 pkts bytes target     prot opt in     out     source               destination
```

---

