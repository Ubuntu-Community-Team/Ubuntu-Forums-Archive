---
title: "Waiting for headers..."
date: 2011-07-31
forum: Networking &amp; Wireless
---

### Post by Drezard on 2011-07-31
My machine here won't update or wget anything. It just sits "Waiting for headers" on both commands for a few minutes, before I get bored and ^c it. 

The network is setup in a bit of a weird way. The devices having issues are going through a Debian box. So like:

home [Box having issues] > gateway [Debian box] > Router [Cisco 1801] 

```

home:~# apt-get update
Hit http://mirror.internode.on.net lenny Release.gpg
Ign http://mirror.internode.on.net lenny/main Translation-en_AU
Ign http://mirror.internode.on.net lenny/non-free Translation-en_AU
Ign http://mirror.internode.on.net lenny/contrib Translation-en_AU
Hit http://mirror.internode.on.net lenny Release
Ign http://mirror.internode.on.net lenny/main Packages/DiffIndex
Ign http://mirror.internode.on.net lenny/non-free Packages/DiffIndex
Ign http://mirror.internode.on.net lenny/contrib Packages/DiffIndex
Hit http://mirror.internode.on.net lenny/main Packages
Hit http://mirror.internode.on.net lenny/non-free Packages
Hit http://mirror.internode.on.net lenny/contrib Packages
Get:1 http://security.debian.org lenny/updates Release.gpg [836B]
Ign http://security.debian.org lenny/updates/main Translation-en_AU
Hit http://volatile.debian.org lenny/volatile Release.gpg
Ign http://volatile.debian.org lenny/volatile/main Translation-en_AU
Hit http://volatile.debian.org lenny/volatile Release
Ign http://volatile.debian.org lenny/volatile/main Packages/DiffIndex
Ign http://volatile.debian.org lenny/volatile/main Sources/DiffIndex
Hit http://volatile.debian.org lenny/volatile/main Packages
Hit http://volatile.debian.org lenny/volatile/main Sources
99% [Waiting for headers]

```

Can ping out to internet and connect to webservers on port 80. 
```

home:~# telnet www.google.com.au 80
Trying 74.125.224.148...
Connected to www.l.google.com.
Escape character is '^]'.
^]
telnet> quit
Connection closed.
home:~# ping 4.2.2.2
PING 4.2.2.2 (4.2.2.2) 56(84) bytes of data.
64 bytes from 4.2.2.2: icmp_seq=1 ttl=57 time=185 ms
^C
--- 4.2.2.2 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 185.337/185.337/185.337/0.000 ms
home:~# ping www.google.com.au
PING www.l.google.com (74.125.224.144) 56(84) bytes of data.
64 bytes from 74.125.224.144: icmp_seq=1 ttl=51 time=235 ms
64 bytes from 74.125.224.144: icmp_seq=2 ttl=51 time=236 ms
^C
--- www.l.google.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1004ms
rtt min/avg/max/mdev = 235.942/236.275/236.608/0.333 ms
home:~#


```

---

### Post by carverj on 2011-08-01
When did you first notice the problem?
Due to introduction of deb. gw?
Tried bypassing the gw to see if it works connected directly to modem?
Also, you may find helpful: -
[http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-8-04-server-not-updating-at-all-stuck-at-waiting-for-headers-645680/](http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-8-04-server-not-updating-at-all-stuck-at-waiting-for-headers-645680/)

---

