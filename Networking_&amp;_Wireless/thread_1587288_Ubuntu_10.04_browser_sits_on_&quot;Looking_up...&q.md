---
title: "Ubuntu 10.04 browser sits on &quot;Looking up...&quot;"
date: 2010-10-03
forum: Networking &amp; Wireless
---

### Post by venator260 on 2010-10-03
The issue I'm having is that browsers in Ubuntu 10.04 stall at the part of the process for loading web pages that is noted by the "Looking Up (website address)...". The page eventually continues to load, but it takes a long time. This problem effects all browsers on the machine (tried Firefox and Chromium). It is not a problem with the connection, because a Windows 7 laptop and even the Windows XP partition on the Ubuntu machine function as they should. 

Ideas?

---

### Post by venator260 on 2010-10-04
bump

---

### Post by endotherm on 2010-10-04
"Looking up ..." means that your pc is querying a DNS server, to ask what IP address goes with the host specified in your URL.

in your network manager, add this dns server address for your connection.
[SIZE=2]```
208.67.222.222
```(OpenDNS.org)

replacing the one already there (if there is one).

then save, reboot and see if your page load time is much improved.
[/SIZE]

---

### Post by Sergius14 on 2010-10-04
Hi,

How do you connect to Internet. DHCP or PPPoE/DSL?

Have you already tested your DNS?

ping [www.google.com](www.google.com) or ping [www.yahoo.com](www.yahoo.com) resolve to an IP address?

If it being resolved, can you browse to that sites directly with the IP address and still have the same issue?

Also you may try to disable IPv6 in Firefox.

about:config

network.dns.disableIPv6 -> true



Regards,

---

### Post by Pick73 on 2010-10-05
I have the same problem. Dual boot to Win XP works normal. Have tried the disable IPv6 and it does not help at all. Chrome does the same thing. It has got to be an OS networking DNS problem of some kind. IP addresses work fast, just not resolving DNS very fast at all. Maybe some kind of virus?

I am using a Linksys router to a direct internet connection.

---

### Post by bkratz on 2010-10-05
> **Pick73 said:**
> I have the same problem. Dual boot to Win XP works normal. Have tried the disable IPv6 and it does not help at all. Chrome does the same thing. It has got to be an OS networking DNS problem of some kind. IP addresses work fast, just not resolving DNS very fast at all. Maybe some kind of virus?

I am using a Linksys router to a direct internet connection.

I used to have the same problem disabling IPv6 did not seem to help. I saw a marked improvement when I went to these DNS servers
(like previously mentioned by endotherm) but I think these were google (don't remember now for sure).

---

### Post by maclenin on 2010-10-05
Almost IDENTICAL (wireless) problem [_here_]("http://ubuntuforums.org/showthread.php?t=1579095") - broadcom 4312 / SLOW to load / non-existant connection / network services of any kind at a snail's pace - or simply die: skype / ftp / browsing....

I have a MacBook Pro that has ZERO (wireless) issues....

---

### Post by endotherm on 2010-10-05
> **maclenin said:**
> Almost IDENTICAL (wireless) problem [_here_]("http://ubuntuforums.org/showthread.php?t=1579095") - broadcom 4312 / SLOW to load / non-existant connection / network services of any kind at a snail's pace - or simply die: skype / ftp / browsing....

I have a MacBook Pro that has ZERO (wireless) issues....
check your dns server address on the mac-side and see if it is using the same server as the ubuntu side of things. if it is, then it has to be a software side issue.

---

### Post by maclenin on 2010-10-05
[Don't want to hijack this person's thread - just wanted to call attention to the fact that many others are struggling similarly - however, to answer your question, endotherm, YES - both mac-side and ubuntu-side are using same dns server....]

---

### Post by venator260 on 2010-10-05
I'm glad to see that I'm not the only one. 

As for the requests for more information: 

The computer has a hard wired connection to a Belkin router which connects to a cable connection. I had the same problem with my Ubuntu laptop, suggesting to me that it was something common to 10.04 that doesn't play well with the connection. The very same laptop works fine with other connections. 

And, just to be clear, it eventually does resolve the DNS connection, it just takes a ridiculously long amount of time. The rest of the loading process occurs at the speed one would expect from the connection.

Also, this computer is at my parents house. I'll email them some instructions and give them a call and see what happens.

---

### Post by venator260 on 2010-10-05
Got right through to the parents: 

Turning off IPv6 through Firefox had a small positive affect on the speed. 

Changing the DNS server saw a more marked improvement. Judging by my sister's reaction over the phone, I'd say it's as fast or nearly as fast as those Windows machines connecting to the same network. 

Thanks for the help everyone!

---

### Post by Sergius14 on 2010-10-05
I'm glad to hear that.

Remember to change the subject of this threat including Solved.

---

### Post by randumnumber on 2010-10-05
I hope everything works out for your fam. I had a similar problem and none of the normal stuff worked...I had to actually edit some file within the system. I really wish i could remember what it is...and if i do find it i will edit and post it for you.

---

### Post by SeijiSensei on 2010-10-06
The file you're looking for is /etc/resolv.conf.  You enter the IP addresses of the nameservers you wish to query like this:

```

nameserver 4.4.4.4
nameserver 8.8.8.8

```

This example uses Google's nameservers.

---

### Post by camorri on 2010-10-06
The above IP address 4.4.4.4 is incorrect. It should be 8.8.4.4

See this link for more information.

[http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)

---

