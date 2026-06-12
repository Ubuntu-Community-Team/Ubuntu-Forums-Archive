---
title: "&quot;no route to host&quot; with ping and ssh from laptop"
date: 2013-02-17
forum: Networking &amp; Wireless
---

### Post by arm-c on 2013-02-17
All,

I cannot connect via SSH to my media center.  This is perplexing, as I was doing this previously.  Something has changed and I am not sure what.  Key things not working:
>  SSH from Laptop to Media Center (also on wifi).
  NOTE:  I can SSH from laptop to my server (wired)... and subsequently SSH from server to media center.
  NOTE:  I can also SSH from Media Center to laptop with both on wifi.

>  browser access to media server (XBMC) webUI fails.
>  Ping exhits same error.

Ping and SSH both report "no route to host"

I run iptables -L and it yields the following (which also matches the server and the media centers iptables).

```

sudo iptables --list -n -v
[sudo] password for xxxxx: 
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 

```

I have also noticed that once I run "sudo iptables -F", SSH, PING, and webUI all work from laptop.  I don't know how to fix this or find the problem that is causing it, as the problem returns following reboot.

Some help would be appreciated greatly.

v/r
ARM-C

---

### Post by Doug S on 2013-02-17
I think you posted your iptables after you flushed them, as they are empty.
I guess it doesn't matter, unless they give us a clue as to the source. i.e. just by looking at them, sometimes we can tell from if they were made by ufw or firestarter or other. The task is to find where or how they are being auto loaded during start up and to disable that. The problem is that there are many many ways it can be done. Have a look in /etc/interfaces for any pre-up iptables-restore command. Have a look in /etc/rc.local. Is ufw running after re-boot?

---

### Post by arm-c on 2013-02-17
i will take a look at what you are recommending.  as far as i can tell... i am not running ufw or other fire wall.  i suspect that this problem began after i upgraded to 12.10.  i just did that in january... so could be some problem with the upgrade process removing something or adding something back in that was disabled previously.

i have looked and as far as i can see... nothing is different from before or after i flush the tables.  both listings look the same.

i will post an update once i get back later tonight and have had a chance to look at what you recommended.

---

### Post by arm-c on 2013-02-18
Doug,

I have looked.  Can't find any reference to iptables.

Again,  there is no visible diference between iptables -L before or after a iptables -F

I believe this began as an issue once I upgraded from 12.04 to 12.10.

---

### Post by Doug S on 2013-02-18
Well, I'm stumped. Clinging to the one clue about before and after iptables flush, maybe looking at loaded modules and route differences before and after might give another clue. Example (from a fresh boot):```
doug@test-smy:~$ doug@test-smy:~$ lsmod >mod_before_flush
doug@test-smy:~$ route >route_before_flush
doug@test-smy:~$ sudo iptables -F
[sudo] password for doug:
doug@test-smy:~$ lsmod >mod_after_flush
doug@test-smy:~$ route >route_after_flush
doug@test-smy:~$ diff mod_before_flush mod_after_flush
1a2,4
> iptable_filter         12706  0
> ip_tables              17791  1 iptable_filter
> x_tables               21974  2 ip_tables,iptable_filter
doug@test-smy:~$ diff route_before_flush route_after_flush
doug@test-smy:~$

```Note: the iptables related modules got loaded because of the flush command, whereas I didn't even have any tables prior.

---

### Post by arm-c on 2013-02-20
Doug,

I am stumpped... and I greatly appreciate your attempt.

My results are nearly identical to yours (returns a little different order):
```

arick@arick-Studio-XPS-1340:~$ diff mod_before_flush mod_after_flush
1a2,4
> iptable_filter         12707  0 
> ip_tables              17792  1 iptable_filter
> x_tables               21936  2 iptable_filter,ip_tables

arick@arick-Studio-XPS-1340:~$ diff route_before_flush route_after_flush 
arick@arick-Studio-XPS-1340:~$

```

So, perhaps it is how one of the filters are listed...

Can you tell me how to check that?  Perhaps it has to do with how the x_tables are ordered as mine returned iptable_filter first then ip_tables....

---

### Post by Doug S on 2013-02-20
I am pretty sure the order does not matter, as it is just a list of what x_tables is used by. The computer I used for my example was actually a 13.04 test computer. On two of my 12.04 computers, the order is listed the other way around.
 
For now, I'm out of ideas. If there is any other clue or log entry or whatever, please let us know.

---

### Post by arm-c on 2013-02-23
Doug / Anyone,

I am still having this issue.  Today, I sat down to try a few things out and check logs.

One thing I noticed is that the route command shows I have a metric of 9 and the other machines have a metric of 2.

I don't know if this is changed behavior between versions or if this is a sign of a problem that I am having.

Ubuntu 12.10 / computer with issue.
```

route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth3
link-local      *               255.255.0.0     U     1000   0        0 eth3
192.168.2.0     *               255.255.255.0   U     9      0        0 eth3

```

Ubuntu 12.04 Computers (two of them only iface name changed)
```

route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
192.168.1.0     *               255.255.255.0   U     2      0        0 eth1

```

NOTE:  the gateways are different, but routers forward packets between both networks.  For example, I have no problem hitting the server at 192.168.1.100 (wired) even though I am on the 192.168.2.1 network.  The problem persist even when I connect to the 192.168.1.X network.

Any new ideas?

Does the Metric appears odd...?  if change needed... how?

Thanks,
Arick

---

