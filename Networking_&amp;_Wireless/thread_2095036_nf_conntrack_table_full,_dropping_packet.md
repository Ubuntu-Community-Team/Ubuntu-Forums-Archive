---
title: "nf_conntrack: table full, dropping packet"
date: 2012-12-15
forum: Networking &amp; Wireless
---

### Post by koenc86 on 2012-12-15
Hello all,

A while back my linux box became unreachable for the first time. In syslog, I noticed error messages "nf_conntrack: table full, dropping packet.".

I then Googled for a solution, and changed a setting in sysctl.conf:
net.netfilter.nf_conntrack_max=131072. This resolved the issue at that moment.

Today, however, the same issue appeared again. All network traffic locked. net.netfilter.nf_conntrack_count exceeded 131072.

Now, I do not understand why this happens and how I can solve and prevent this from happening.
My box is runnning Ubuntu 12.10, used mostly as a home server for basic stuff such as storage, streaming media and running a few small websites with very low usage.

I appreciate any help from you solving this problem. Thanks in advance!

---

### Post by Doug S on 2012-12-15
I guess the first step is to try to figure out why you are having so many connections. I think the default is 65536, so you doubled it. The first thing that comes to mind is some sort of attack, such as a SYN flood or something creating connections. Is your server on a LAN or on internet? Does it have a good iptables rule set (firewall)?
 
Do you see one dominant IP address or group of IP addresses in the conntrack table when it is excessively large? Do:```
 sudo cat /proc/net/ip_conntrack
```Since your table gets huge, you might want to redirect output to a file to look at with an editor:```
 sudo cat /proc/net/ip_conntrack >temp_file.txt
```You may or may not find other helpful information in the /var/log directory, perhaps in syslog or kern.log or the apache2 sub-directory.

---

### Post by koenc86 on 2012-12-15
Thanks for your reply.

There is no such file "ip_conntrack" in /proc/net/.
I cannot find such file aywhere. 

I do have iptables setup using the default chains, just accepting a few ports and default policy drop. Nothing really special.

I checked /var/log but I did not find anything useful in the files there.

---

### Post by Doug S on 2012-12-15
I do not know how to try to help without being able to extract some hints, to get us started, from the actual connection tracking table. I also have no clue as to why the table is not available for display on your system. I assume that you tried the command I gave, and got some error. (?) If you try to find a file "ip_conntrack" or show it via "ls -l /proc/net", then no it will not show up.

---

### Post by koenc86 on 2012-12-15
> cat: /proc/net/ip_conntrack: No such file or directory

Is there any other place this file could be stored or named?

I wish I could give you more hints but currently I have no other clues.

---

### Post by Doug S on 2012-12-15
I guess on your system the ip_conntrack module is not loaded into the kernel. One of my other computers doesn't have it either.```
sudo modprobe ip_conntrack
```After you load that module then you should be to display the connection tracking table.
Without loading the module you might be able to gain some insight via the netstat command. Example:```
netstat --tcp
netstat --udp
```Also I found this [link]("http://antmeetspenguin.blogspot.ca/2011/01/high-performance-linux-router.html#!/2011/01/high-performance-linux-router.html") useful.
Hope this helps.

---

### Post by koenc86 on 2012-12-16
The link you provided is the guide I used the first time this problem occurred to increase the nf_conntrack_max numbers.

I used the command 'sudo modprobe ip_conntrack'. This does not respond nor error anything. It hasn't created the file /proc/net/ip_conntrack either. File still not exists.

When doing "modprobe -l | grep conntrack" I see a bunch of "nf_conntrack*.so" modules listed. I assume these are the ip_conntrack module.

** EDIT ***:

I have rebooted the box to reset it. I installed package 'conntrack' and can now list connections with 'conntrack -L'.
Currently there is not much in the list, but I will often look for odd entries. Any specific, suspected things I could watch out for?

---

### Post by Doug S on 2012-12-16
> **koenc86 said:**
> The link you provided is the guide I used the first time this problem occurred to increase the nf_conntrack_max numbers.
 
I used the command 'sudo modprobe ip_conntrack'. This does not respond nor error anything. It hasn't created the file /proc/net/ip_conntrack either. File still not exists.
 
When doing "modprobe -l | grep conntrack" I see a bunch of "nf_conntrack*.so" modules listed. I assume these are the ip_conntrack module.
 
** EDIT ***:
 
I have rebooted the box to reset it. I installed package 'conntrack' and can now list connections with 'conntrack -L'.
Currently there is not much in the list, but I will often look for odd entries. Any specific, suspected things I could watch out for?Yes, there is no print out from the "modprobe ip_conntrack" command, it just loads the kernel module. Anyway, it doesn't matter, as you are now using the conntrack package (myself, I avoid extra packages if there are other ways to get the information). I am not sure what to look for. Perhaps a flood of connections from some attack. Perhaps abandonded established connections, with their so very very long timeout (typically 5 days). We will have to wait and see what is in the conntrack table after time.
 
Just for completeness, here is session from one of my computers from before and after loading the kernel ip_conntrack module:```
doug@s15:~$ sudo cat /proc/net/ip_conntrack
cat: /proc/net/ip_conntrack: No such file or directory
doug@s15:~$ sysctl net.ipv4.netfilter.ip_conntrack_max
error: "net.ipv4.netfilter.ip_conntrack_max" is an unknown key
doug@s15:~$ sudo modprobe ip_conntrack
doug@s15:~$ sudo cat /proc/net/ip_conntrack
tcp      6 299 ESTABLISHED src=192.168.111.112 dst=192.168.111.100 sport=22 dport=16959 src=192.168.111.100 dst=192.168.111.112 sport=16959 dport=22 [ASSURED] mark=0 use=2
doug@s15:~$ sysctl net.ipv4.netfilter.ip_conntrack_max
net.ipv4.netfilter.ip_conntrack_max = 65536

```Edit 1: Just to clarify (for other readers) the default max connections is not simply 65536, but rather a function of how much memory one has (until 65536 is reached). For example, on another of my computers, with only 256 megabytes, the default is 15540.
Edit 2: I do not understand how the OP is getting the error, but didn't have the ip_conntrack (or nf_conntrack) module loaded at first. I wonder if I am missing something or confused about something.

---

