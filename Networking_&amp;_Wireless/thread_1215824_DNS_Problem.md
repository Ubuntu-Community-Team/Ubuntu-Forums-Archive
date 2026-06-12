---
title: "DNS Problem??"
date: 2009-07-17
forum: Networking &amp; Wireless
---

### Post by MrMacHead on 2009-07-17
I'm troubleshooting my daughter's  Intrepid Ibex install due to a problem with getting access to the internet. She can access her home network and fileshare as well as print to her network printer. The PC is now at my house and the symptoms have not changed.

Firefox, ThunderBird and Update Manager cannot get access to the internet. FrostWire works just fine. After some research here and via Google, it looks like the problem involves DNS.

Here are the commands I ran in Terminal...

[B]missy@Ubuntu:~$ sudo mii-tool eth0
[sudo] password for missy: 
eth0: negotiated 100baseTx-FD flow-control, link ok

missy@Ubuntu:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:50:8d:61:ab:95  
          inet addr:10.0.1.8  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe61:ab95/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13154 (13.1 KB)  TX bytes:8214 (8.2 KB)
          Interrupt:23 Base address:0xa000 

missy@Ubuntu:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: Stale NFS file handle
missy@Ubuntu:~$ 

missy@Ubuntu:~$ ping 208.67.222.222
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
TRUNCATED
64 bytes from 208.67.222.222: icmp_seq=41 ttl=55 time=26.4 ms
64 bytes from 208.67.222.222: icmp_seq=42 ttl=55 time=28.3 ms
64 bytes from 208.67.222.222: icmp_seq=43 ttl=55 time=28.4 ms
^C
--- 208.67.222.222 ping statistics ---
43 packets transmitted, 43 received, 0% packet loss, time 42147ms
rtt min/avg/max/mdev = 25.955/29.111/45.365/3.220 ms
missy@Ubuntu:~$ 

missy@Ubuntu:~$ ping google.com
ping: unknown host google.com
missy@Ubuntu:~$ [/B]


The /etc/resolv.conf: Stale NFS file handle stands out, of course. When I went into the etc directory to check the file, I see that the file itself is resolv.conf.tmp for some reason. There is no resolv.conf that I can see, however the ls command does show it. It is not a hidden file either.

Can anyone give me some help on how to sort out this glitch??

John

---

### Post by dlmarti on 2009-07-17
How is the network setup?  DHCP or Static?

The NFS comment is something I haven't seen, thats a weird one.

---

### Post by shredkingj on 2009-07-17
Are you mounting /etc to a NFS server?  Maybe this was accidentally done.  Try running the mount command without arguments and posting it here for us to get a better sense of that.

---

### Post by MrMacHead on 2009-07-17
> **dlmarti said:**
> How is the network setup?  DHCP or Static?

The NFS comment is something I haven't seen, thats a weird one.

It is DHCP

---

### Post by MrMacHead on 2009-07-17
> **shredkingj said:**
> Are you mounting /etc to a NFS server?  Maybe this was accidentally done.  Try running the mount command without arguments and posting it here for us to get a better sense of that.

This is strictly a vanilla install for use at home...nothing fancy like a server. I am not that advanced so there is no mounting other than what the OS does for drives.....

The machine just suddenly lost the ability to get FF and TB onto the internet the other day.

---

### Post by capscrew on 2009-07-17
> **MrMacHead said:**
> ...
```
missy@Ubuntu:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: Stale NFS file handle
missy@Ubuntu:~$ 
```


The /etc/resolv.conf: Stale NFS file handle stands out, of course. When I went into the etc directory to check the file, I see that the file itself is resolv.conf.tmp for some reason. There is no resolv.conf that I can see, however the ls command does show it. It is not a hidden file either.

This does come from a request to view a file mounted on a NFs server.  See [_[COLOR="DarkSlateGray"]here[/COLOR]_]("http://sysunconfig.net/unixtips/stale_nfs.txt").> 

Can anyone give me some help on how to sort out this glitch??

What is the contents of *"resolv.conf.tmp"? *Regardless of how a stale file handle was left in place of the file, the cure is simple.  Create a new /etc/resov.conf file.  Use any text editor e.g gedit for GUI or nano from the CLI and add the needed dns server.  Below is the format and what is in my /etc/resov.conf file.  Note: I have DNS services on my router (192.168.1.1)  ```
nameserver 192.168.1.1
```

---

### Post by MrMacHead on 2009-07-18
> **capscrew said:**
> This does come from a request to view a file mounted on a NFs server.  See [_[COLOR="DarkSlateGray"]here[/COLOR]_]("http://sysunconfig.net/unixtips/stale_nfs.txt").What is the contents of *"resolv.conf.tmp"? *Regardless of how a stale file handle was left in place of the file, the cure is simple.  Create a new /etc/resov.conf file.  Use any text editor e.g gedit for GUI or nano from the CLI and add the needed dns server.  Below is the format and what is in my /etc/resov.conf file.  Note: I have DNS services on my router (192.168.1.1)  ```
nameserver 192.168.1.1
```

```
missy@Ubuntu:~$ sudo cat /etc/resolv.conf
[sudo] password for missy: 
cat: /etc/resolv.conf: Stale NFS file handle
missy@Ubuntu:~$ cat /etc/resolv.conf.tmp
# Generated by NetworkManager
domain cgocable.net
search cgocable.net
nameserver 10.0.1.1
```

When I try to create a new /etc/resolv.conf file, it is always blocked by the "stale" state. I have tried to use the rm --force command to delete the /etc/resolv.conf file, with the same result. That was one of the ideas I had before I posted...to rename the tmp file or overwrite the /etc/resolv.conf file. All efforts are blocked.

I read that running an fsck check at bootup should cure the stale state of that file. Does that make sense??

As for the server...this PC is in a small home network with an iMac. There is absolutely no server, as such, involved.

Thanks for the help

John

---

### Post by MrMacHead on 2009-07-18
OK..situation is resolved. I discovered the "force fsck" tip on this page and it did the trick! Thanks to all who posted.

[http://onlyubuntu.blogspot.com/2009/03/how-to-repair-corrupted-filesystem-in.html]("http://onlyubuntu.blogspot.com/2009/03/how-to-repair-corrupted-filesystem-in.html")

---

