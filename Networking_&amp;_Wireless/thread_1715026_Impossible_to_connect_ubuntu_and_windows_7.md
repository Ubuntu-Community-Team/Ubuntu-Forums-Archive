---
title: "Impossible to connect ubuntu and windows 7"
date: 2011-03-26
forum: Networking &amp; Wireless
---

### Post by semsaudade on 2011-03-26
Hello and thank you in advance for the help. And please, forgive my bad english! I have a desktop PC with Windows 7 and a netbook with Ubuntu 10.04 netbook edition. The two computers are connected in a network with a Belkin modem router (the desktop PC is connected via cable and the netbook is connected wireless).  I simply want to have access to some folders on Windows 7 from Ubuntu (I do not need the opposite), but I can not do it in any way. I tried following various guides on the net, I set the permissions of shared folders on Windows 7 (giving permission to everyone: everyone, guests and so on and so forth !)... but to no result. When I look for windows in Ubuntu's network folder, I see absolutely nothing. I also tried directly with nautilus smb://192.168.2.3 (the network address of my computer-desktop), but every trial was useless. I always get a frustrating message: &quot;Retrieving the list of shares from the server failed. &quot;  Someone can suggest a solution or which tests can I do to understand where the problem lies? Keep in mind that I'm not a linux expert, so please be patient with me.  Thanks again. Giancarlo

---

### Post by mkhurram92 on 2011-03-26
hello
first make sure that u r able to ping the Windows Machine from ubuntu and from here to windows 

from Windows to Ubuntu Share access please read this
[http://www.7tutorials.com/how-access-ubuntu-shared-folders-windows-7](http://www.7tutorials.com/how-access-ubuntu-shared-folders-windows-7)

and from ubuntu to windows share access please read this
[http://www.liberiangeek.net/2010/03/how-to-quickly-access-windows-shares-from-ubuntu/](http://www.liberiangeek.net/2010/03/how-to-quickly-access-windows-shares-from-ubuntu/)

Or u can also use WinSCP for easy access from Ubuntu to Windows !!!!

---

### Post by semsaudade on 2011-03-27
Thank a lot for your answer-

This is the result of ping executed on Ubuntu machine towards Windows machine:

```
giancarlo@giancarlo-laptop:~$ ping 192.168.2.3
PING 192.168.2.3 (192.168.2.3) 56(84) bytes of data.
64 bytes from 192.168.2.3: icmp_seq=1 ttl=128 time=8.20 ms
64 bytes from 192.168.2.3: icmp_seq=2 ttl=128 time=2.40 ms
64 bytes from 192.168.2.3: icmp_seq=3 ttl=128 time=1.82 ms
64 bytes from 192.168.2.3: icmp_seq=4 ttl=128 time=1.85 ms
64 bytes from 192.168.2.3: icmp_seq=5 ttl=128 time=2.91 ms
64 bytes from 192.168.2.3: icmp_seq=6 ttl=128 time=1.96 ms
64 bytes from 192.168.2.3: icmp_seq=7 ttl=128 time=13.4 ms
64 bytes from 192.168.2.3: icmp_seq=8 ttl=128 time=2.15 ms
64 bytes from 192.168.2.3: icmp_seq=9 ttl=128 time=18.7 ms
64 bytes from 192.168.2.3: icmp_seq=10 ttl=128 time=8.97 ms
64 bytes from 192.168.2.3: icmp_seq=11 ttl=128 time=1.69 ms
^C
--- 192.168.2.3 ping statistics ---
11 packets transmitted, 11 received, 0% packet loss, time 10014ms
rtt min/avg/max/mdev = 1.696/5.839/18.753/5.551 ms
giancarlo@giancarlo-laptop:~$ 
```

I guess that network is OK... isn't it?

So which is the next step? I try to read the guides you suggested. but I can understand which is the purpose of changing computer name and workgroup name in windows. Can't I keep the standard names (es. workgroup named WORKGROUP)? Could this be related in any way with my problem in establishing a connection?

Thank you very much once more!

---

### Post by mkhurram92 on 2011-03-27
> 
So which is the next step? I try to read the guides you suggested. but I can understand which is the purpose of changing computer name and workgroup name in windows. Can't I keep the standard names (es. workgroup named WORKGROUP)? Could this be related in any way with my problem in establishing a connection?


Make Sure that Domain name is same on both side nothing more than this.
There is no problem now u can just follow my links to access shares

---

### Post by semsaudade on 2011-03-28
> Make Sure that Domain name is same on both side nothing more than this.
There is no problem now u can just follow my links to access sharesSorry but I am not able to do it. What do you mean for "Domain name".

I tried following your links:
1) went to Places &#8211;> Connect to Server&#8230;
2) choose Windows shares as Service type, and entered the Server IP address Hostname

After doing it, I am very puzzled about what to do. Now I should enter Share, Folder, User and Domain name.... I tried every possible combination of inputs with no results at all. It is not very clear for me if it is necessary to fill each item in the previous list, or if these informations are optional (as suggested by ubuntu).

If can help u, I give here the results of some other tests I made. Thanks again!

> 
Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2011-03-27 10:57 CEST
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 3.19 seconds
giancarlo@giancarlo-laptop:~$ smbclient -L //192.168.2.3
Enter giancarlo's password: 
Connection to 192.168.2.3 failed (Error NT_STATUS_UNSUCCESSFUL)

giancarlo@giancarlo-laptop:~$ nmap 192.168.2.3 -PN

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2011-03-28 19:11 CEST
Interesting ports on 192.168.2.3:
Not shown: 996 filtered ports
PORT      STATE SERVICE
135/tcp   open  msrpc
49153/tcp open  unknown
49154/tcp open  unknown
49158/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 12.45 seconds

---

