---
title: "I can ping but noy browse.  All suggestions very much appreciated"
date: 2011-07-16
forum: Networking &amp; Wireless
---

### Post by jalfaro on 2011-07-16
Fellow ubuntu users,
I throw my hands up in the air.  I&#8217;ve done all the research I could.  You are my last hope.  My internet connection is not working.

I have a Dell Inspiron 1525 running Ubuntu 8.10 Intrepid.  My laptop use to wirelessly connect to my network  and online without any problems.  I am sure I accidentally reconfigured something that is not allowing my to go online anymore.  My laptop is able to connect to my local network without any problem.  I am able to share resources with my network.  The other computers can connect and go online without any problems.  However my laptop is not able to browse the web.  I can ping any website but I cannot browse online.

My network settings are set to automatic DHCP.  (Used Gedit to change my DNS to Google or OpenDNS. I tried both).

Here are some of the things that I have tried:
Used Network Tools and this is what I get-
1. Ping- Pings IP addresses (Google, Yahoo, and my own router)without any problems.
2. Netstat-
3. Traceroute-I tracerouted Google (8.8.8.8) and the last device at the end was not 8.8.8.8.  It routed 7 sequences before it went to a no reply state.
4. Portscan-35305 on the laptop
5. Lookup-
6. Finger-
7. Whois-

I&#8217;ve changed DNS address using gnome first to Google server and then OpenDNS. Neither allowed me to surf the web.

I also tried changing DNS server IP address using Gedit with the following command:
sudo gedit /etc/dhcp3/dclient.config

I disable ipv6 in Mozilla.  This also did not make a difference. 

Any suggestions?
Thanks for your inout.

---

### Post by jmoorse on 2011-07-16
Please post the output of:

cat /etc/resolv.conf
dig [www.google.com](www.google.com)
dig [www.google.com](www.google.com) @208.67.222.222
dig [www.google.com](www.google.com) @8.8.8.8

---

### Post by jalfaro on 2011-07-17
jmoorse, thanx so much for taking the time to look at this.  Hopefully you can find something.  Could not dig with google name.   Needed to dig with IP addresses.

> **jmoorse said:**
> Please post the output of:

> cat /etc/resolv.conf
jalfaro@dell-desktop:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: Stale NFS file handle
jalfaro@dell-desktop:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: Stale NFS file handle



> dig [www.google.com](www.google.com)
jalfaro@dell-desktop:~$ dig [www.google.com](www.google.com)
dig
; <<>> DiG 9.5.0-P2.1 <<>> [www.google.com](www.google.com)
;; global options: printcmd
;; connection timed out; no servers could be reached


> dig [www.google.com](www.google.com) @208.67.222.222
jalfaro@dell-desktop:~$ dig [www.google.com](www.google.com) @208.67.222.222
; <<>> DiG 9.5.0-P2.1 <<>> [www.google.com](www.google.com) @208.67.222.222
;; global options: printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 17259
;; flags: qr rd ra; QUERY: 1, ANSWER: 6, AUTHORITY: 0, ADDITIONAL: 0
;; QUESTION SECTION:
;[www.google.com](www.google.com). IN A
;; ANSWER SECTION:
[www.google.com](www.google.com). 600771 IN CNAME [www.l.google.com](www.l.google.com).
[www.l.google.com](www.l.google.com). 183 IN A 74.125.224.84
[www.l.google.com](www.l.google.com). 183 IN A 74.125.224.80
[www.l.google.com](www.l.google.com). 183 IN A 74.125.224.82
[www.l.google.com](www.l.google.com). 183 IN A 74.125.224.83
[www.l.google.com](www.l.google.com). 183 IN A 74.125.224.81
;; Query time: 670 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Sat Jul 16 20:56:35 2011
;; MSG SIZE rcvd: 132


> dig [www.google.com](www.google.com) @8.8.8.8
jalfaro@dell-desktop:~$ dig [www.google.com](www.google.com) @8.8.8.8
; <<>> DiG 9.5.0-P2.1 <<>> [www.google.com](www.google.com) @8.8.8.8
;; global options: printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 34421
;; flags: qr rd ra; QUERY: 1, ANSWER: 6, AUTHORITY: 0, ADDITIONAL: 0
;; QUESTION SECTION:
;[www.google.com](www.google.com). IN A
;; ANSWER SECTION:
[www.google.com](www.google.com). 86390 IN CNAME [www.l.google.com](www.l.google.com).
[www.l.google.com](www.l.google.com). 290 IN A 74.125.224.116
[www.l.google.com](www.l.google.com). 290 IN A 74.125.224.114
[www.l.google.com](www.l.google.com). 290 IN A 74.125.224.115
[www.l.google.com](www.l.google.com). 290 IN A 74.125.224.112
[www.l.google.com](www.l.google.com). 290 IN A 74.125.224.113
;; Query time: 45 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Sat Jul 16 20:57:02 2011
;; MSG SIZE rcvd: 132

---

### Post by jmoorse on 2011-07-17
The output is your problem. 

jalfaro@dell-desktop:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: Stale NFS file handle
jalfaro@dell-desktop:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: Stale NFS file handle

You have no valid nameserver config.  For some reason this file lives on NFS?  Please post output of the command 'mount'.

Perhaps you have some filesystem issues, you may want to perform a fs check as covered here [https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)

Please make sure you have backups of any critical data before doing this, just in the unlikely event there are problems..

Also 'sudo shutdown -rF' should check the filesystem upon reboot

---

### Post by jalfaro on 2011-07-18
Jmoorse. I tried your suggestion and my Internet is still not working. Do you have any other suggestions? 
Thank you.

> **jmoorse said:**
> The output is your problem. 

jalfaro@dell-desktop:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: Stale NFS file handle
jalfaro@dell-desktop:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: Stale NFS file handle

You have no valid nameserver config.  For some reason this file lives on NFS?  Please post output of the command 'mount'.

Perhaps you have some filesystem issues, you may want to perform a fs check as covered here [https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)

Please make sure you have backups of any critical data before doing this, just in the unlikely event there are problems..

Also 'sudo shutdown -rF' should check the filesystem upon reboot

---

### Post by jmoorse on 2011-07-18
Did you fun a fs check?  What is the output of 'mount'?

---

### Post by jalfaro on 2011-08-07
Jeff,
Thank you so much for your time and effort.  I finally decided to restore my ubuntu that came on the hard drive with my dell computer.   I am typing this on my computer.  (I'm online!)  Thank you so much for your time.   It is incredibly helpful for us newbees.  You can file this with the under cases RESOlVED!

---

### Post by jmoorse on 2011-08-12
Glad to hear it, enjoy Ubuntu!

---

