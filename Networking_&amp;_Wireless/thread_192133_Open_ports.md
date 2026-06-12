---
title: "Open ports"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by sopo_dan on 2006-06-08
hi

i'd like to know how i can check what apps (daemons) and on what port(s) are listening

TIA

---

### Post by nanotube on 2006-06-08
[QUOTE=sopo_dan]hi

i'd like to know how i can check what apps (daemons) and on what port(s) are listening

TIA[/QUOTE]
```
sudo netstat -plantu
```

---

### Post by sopo_dan on 2006-06-08
thanks
i've read lots of threads on firewalls and was surprised that this wasn't discussed in any, 'cause i think it the easyest way to find out if one really needs/doesn't need a firewall to be enabled

---

### Post by imhdd on 2006-06-08
For a free, quick scan of your ports, go to:

[www.grc.com/](www.grc.com/)

On the opening page, click on "SHIELDS UP!" Then on the second page:
Scroll down to "SHIELDS UP!" and click it; Scroll down to "PROCEED" and click it; On the "Shields Up Services" , click your choice of procedures.

---

### Post by nanotube on 2006-06-08
[QUOTE=imhdd]For a free, quick scan of your ports, go to:

[www.grc.com/](www.grc.com/)

On the opening page, click on "SHIELDS UP!" Then on the second page:
Scroll down to "SHIELDS UP!" and click it; Scroll down to "PROCEED" and click it; On the "Shields Up Services" , click your choice of procedures.[/QUOTE]
note: that would only mean anything if you are not behind a nat/router, though. otherwise it would only be scanning the router, not your computer, so won't tell you anything about the services you are running on the comp.

---

### Post by nanotube on 2006-06-08
[QUOTE=sopo_dan]thanks
i've read lots of threads on firewalls and was surprised that this wasn't discussed in any, 'cause i think it the easyest way to find out if one really needs/doesn't need a firewall to be enabled[/QUOTE]
well, on the default ubuntu install, no services are listening to the world. only way something would be listening is if you specifically installed some server, in which case you would know what it was :)

about interpreting netstat output - note that a few things will be listed, but they /should/ all just be listening to localhost, not to outside. so when you see stuff listed from the nestat command, don't be alarmed that there is stuff, first make sure whether it's localhost only or not.

---

### Post by sopo_dan on 2006-06-08
[quote=nanotube]note: that would only mean anything if you are not behind a nat/router, though. otherwise it would only be scanning the router, not your computer, so won't tell you anything about the services you are running on the comp.[/quote] well that's exactly what i wanted to see - what can be accessed from the outside. i wasn't particularly interested in the actual daemons which are running

[quote=nanotube]well, on the default ubuntu install, no services are listening to the world. only way something would be listening is if you specifically installed some server, in which case you would know what it was :smile:[/quote] yea, i read that too. i only intalled azureus & wanted to make sure it's - as it says - only listening on the port i specified :wink:

---

### Post by pzonik on 2006-07-01
I've a problem with open port. I use apache server, and when I block standard port for http (80) than nobody see my site. When I open it everbody see it but Shields UP!! test ([https://www.grc.com](https://www.grc.com)) give me Failed. Is this normal ?

---

### Post by fragos on 2006-07-01
Port 80 is for http.  If a firewall only has one port open, it will be 80.

---

### Post by nanotube on 2006-07-01
[QUOTE=pzonik]I've a problem with open port. I use apache server, and when I block standard port for http (80) than nobody see my site. When I open it everbody see it but Shields UP!! test ([https://www.grc.com](https://www.grc.com)) give me Failed. Is this normal ?[/QUOTE]
yes, it is normal, because web servers run on port 80. so of course if you close port 80, your website cannot be seen. :) grc gives you failed, because it detects that you have a port open (namely, port 80). so, seems like everything is good.

---

### Post by verbatim210 on 2006-07-01
seems like a default firewall is blocking my ports. is this true?
**netstat -plantu** showed only main ports opened.

how to forward ports using console?
thank you

---

### Post by nanotube on 2006-07-02
[QUOTE=verbatim210]seems like a default firewall is blocking my ports. is this true?
**netstat -plantu** showed only main ports opened.

how to forward ports using console?
thank you[/QUOTE]
well, if you are sitting behind a NAT router, then the router is the one that's blocking stuff for you. to forward the ports, go to the router config page, and set the proper forwards. 

if the assumption i made that you are behind a router is incorrect, post back here and we will take a better look. :)

---

### Post by verbatim210 on 2006-07-02
your half correct. 
it is behind a router, but im accessing it via lan.

as i mentioned, i did netstat -plantu and it is **not **listening on telnet.
verbatim

---

### Post by nanotube on 2006-07-02
[QUOTE=verbatim210]your half correct. 
it is behind a router, but im accessing it via lan.

as i mentioned, i did netstat -plantu and it is **not **listening on telnet.
verbatim[/QUOTE]
well, then tell us what exactly you are trying to do. the telnet daemon does not run on ubuntu by default. did you install it? are you sure you want to use telnet, instead of ssh (a much better alternative, with more security and more features)?

but at any rate, to see what the firewall on your machine is allowing or blocking, just run "sudo iptables --list", and it will show all the firewall rules. by default, it allows everything, though.

---

### Post by verbatim210 on 2006-07-02
[I]Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination[/I]

**you're right, nothing is there**

[I]Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State                                                                                                    PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     -                                                                                             
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN     -                                                                                             
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     -                                                                                             
tcp6       0      0 :::80                   :::*                    LISTEN     -                                                                                             
tcp6       0      0 :::22                   :::*                    LISTEN     -                                                                                             
tcp6       0   52 ::ffff:192.168.0.1:22 ::ffff:192.168.0.4:1749 ESTABLISHED-                                                                                             
udp        0      0 0.0.0.0:68              0.0.0.0:*                          -   [/I]

[B]http, ftp and ssh etc... are opened ports.  i want to open 23 so i can telnet into this computer.  hope this makes sense, thanks.

verbatim[/B]

---

### Post by pzonik on 2006-07-02
[QUOTE=nanotube]yes, it is normal, because web servers run on port 80. so of course if you close port 80, your website cannot be seen. :) grc gives you failed, because it detects that you have a port open (namely, port 80). so, seems like everything is good.[/QUOTE]

Ok, thanks for answer. I have a clear conscience now.

---

### Post by nanotube on 2006-07-02
[QUOTE=verbatim210][I]Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination[/I]

**you're right, nothing is there**

[I]Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State                                                                                                    PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     -                                                                                             
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN     -                                                                                             
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     -                                                                                             
tcp6       0      0 :::80                   :::*                    LISTEN     -                                                                                             
tcp6       0      0 :::22                   :::*                    LISTEN     -                                                                                             
tcp6       0   52 ::ffff:192.168.0.1:22 ::ffff:192.168.0.4:1749 ESTABLISHED-                                                                                             
udp        0      0 0.0.0.0:68              0.0.0.0:*                          -   [/I]

[B]http, ftp and ssh etc... are opened ports.  i want to open 23 so i can telnet into this computer.  hope this makes sense, thanks.

verbatim[/B][/QUOTE]

so, like i asked before, why not use ssh? but if you /really/ want telnet, you have to install telnetd, the telnet daemon. to install it, just run
```
sudo aptitude update
sudo aptitude install telnetd
```

---

### Post by verbatim210 on 2006-07-02
hey nanotube,

i cant use ssh because this is for a different application.  
also after updating, it cannot find telnetd.
the closest thing it has is telnet, which is a client.

dont think thats what i'm looking for,
i just want to open my port 23 :(

---

### Post by nanotube on 2006-07-02
[QUOTE=verbatim210]hey nanotube,

i cant use ssh because this is for a different application.  
also after updating, it cannot find telnetd.
the closest thing it has is telnet, which is a client.

dont think thats what i'm looking for,
i just want to open my port 23 :([/QUOTE]
have you enabled the universe repository? telnetd is not in the default repositories (for reasons of being insecure). enable that, then try again.

---

### Post by verbatim210 on 2006-07-02
alright, i've installed... telnetd inetutils-telnetd and telnetd-ssl
(all the ones labelled telnet server)

reboot machine
i still can't telnet, port 23 is blocked.

[I]tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     -
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN     -
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     -
tcp6       0      0 :::80                   :::*                    LISTEN     -
tcp6       0      0 :::22                   :::*                    LISTEN     -
tcp6       0  148 ::ffff:192.168.0.1:22 ::ffff:192.168.0.5:2438 ESTABLISHED-
udp        0      0 0.0.0.0:68              0.0.0.0:*  [/I]   

need to get port 23 on this list somehow

---

### Post by nanotube on 2006-07-02
[QUOTE=verbatim210]alright, i've installed... telnetd inetutils-telnetd and telnetd-ssl
(all the ones labelled telnet server)

reboot machine
i still can't telnet, port 23 is blocked.

[I]tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     -
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN     -
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     -
tcp6       0      0 :::80                   :::*                    LISTEN     -
tcp6       0      0 :::22                   :::*                    LISTEN     -
tcp6       0  148 ::ffff:192.168.0.1:22 ::ffff:192.168.0.5:2438 ESTABLISHED-
udp        0      0 0.0.0.0:68              0.0.0.0:*  [/I]   

need to get port 23 on this list somehow[/QUOTE]
well first, i think you only needed one of them. now, second, you have to make sure the daemon is running. try 
```
ps ax |grep telnet
```
and see if a telnetd process is up. i have never configured a telnet server on ubuntu (and neither have most people, since telnet is basically deprecated), so don't really know how easy they make it to put one up. look for some documentation...

---

### Post by verbatim210 on 2006-07-02
verbatim@home:~$ ps ax |grep telnet
 6378 pts/0    S+     0:00 grep telnet

im not sure what this means

---

### Post by nanotube on 2006-07-02
[QUOTE=verbatim210]verbatim@home:~$ ps ax |grep telnet
 6378 pts/0    S+     0:00 grep telnet

im not sure what this means[/QUOTE]
that means that there is no telnet daemon running. the only process that has telnet in it is your "grep telnet". :)

so, that means that you have to actually /start/ you telnet daemon.
try looking around in /etc/init.d/
there should be a start script for telnet (will probably have something with telnet in its name). just run it with 
```
sudo /etc/init.d/nameofthattelnetscript start
```

and then your telnet daemon should be running...

---

### Post by verbatim210 on 2006-07-02
acpid                            loopback           rc.local
alsa-utils                       lvm                rcS
apache2                          makedev            README
atd                              mdadm              reboot
bootclean.sh                     mdadm-raid         rmnologin
bootlogd                         module-init-tools  rsync
bootmisc.sh                      mountall.sh        sendsigs
checkfs.sh                       mountdevsubfs      single
checkroot.sh                     mountvirtfs        skeleton
console-screen.sh                mtab               ssh
cron                             mysql              stop-bootlogd
dns-clean                        mysql-ndb          sysklogd
evms                             mysql-ndb-mgm      udev
glibc.sh                         networking         umountfs
halt                             nvidia-kernel      umountnfs.sh
hdparm                           pcmciautils        umountroot
hostname.sh                      postfix            urandom
hwclock.sh                       ppp                vsftpd
keymap.sh                        pppd-dns           waitnfs.sh
klogd                            procps.sh
linux-restricted-modules-common  rc

nope, no telnet lol.  tried google tried forums, no one seems to know how to open linux ports.  damn.

---

### Post by verbatim210 on 2006-07-02
could not bind telnet socket to address 127.0.0.1:23 TCP (psock_bind: Permission denied)

---

### Post by nanotube on 2006-07-03
[QUOTE=verbatim210]could not bind telnet socket to address 127.0.0.1:23 TCP (psock_bind: Permission denied)[/QUOTE]
what command did you run to get that? did you run it with sudo?

---

### Post by verbatim210 on 2006-07-03
copy and pasted from log file
just wanted to help u see whats happening
i'm guessing i need to do something like this...

iptables -A PREROUTING -t nat -p tcp -i eth1 --dport 80 -j DNAT --to 192.168.0.2:80

anyway i give up, i'll just wait till school starts and ask my teacher.

---

### Post by nanotube on 2006-07-03
[QUOTE=verbatim210]copy and pasted from log file
just wanted to help u see whats happening
i'm guessing i need to do something like this...

iptables -A PREROUTING -t nat -p tcp -i eth1 --dport 80 -j DNAT --to 192.168.0.2:80

anyway i give up, i'll just wait till school starts and ask my teacher.[/QUOTE]
the iptables command is to manipulate your firewall. since your firewall already lets everything through, you don't need to do anything with it. you need to run the telnet daemon. but ok, have fun. :)

---

