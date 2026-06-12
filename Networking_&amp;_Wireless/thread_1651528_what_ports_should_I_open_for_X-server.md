---
title: "what ports should I open for X-server"
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by Jorge.ar on 2010-12-23
Hi!!!
 
 
I have a reports server on unix that needs an X-server for running. I've installed a ubuntu on an old pc to run the x-server.
 
I set the display variable on the server pointing to the ubuntu box, but cant make the display work. (i use xclock for testing).
 
I can ping from the server to the ubuntu machine, but I have a firewall between the two machines. I need to know what ports should I open for X-server.
 
I opened ports 6000 and 6001 but still doesnt work. I also executed the command "xhost +" on ubuntu.
 
Should I do something in the ubuntu machine for opening the ports, or configure something else??
 
thanks,
Jorge.
 
PS: sorry about my english :p

---

### Post by puppywhacker on 2010-12-23
I prefer to use X-Forwarding using SSH, you ssh into the reports server and run the applicaton, I use "xclock" as my favority X testing application.

If you insist on using TCP/6000, set the DisallowTCP to false in /etc/gdm/gdm.conf
"DisallowTCP=false"

You should also then configure your firewall to allow TCP/6000 as destination port from your reports server to your ubuntu. Meaning Ubuntu should run the port 6000. On the reportingserver you should export the display to your ubuntu's ip-address "export DISPLAY=ubuntu-ip:0.0"

Be very careful when putting firewall rules in, verify them, if you say "allow 6000", it can just as well mean "allow UDP port 6000 from ubuntu to report server"

---

### Post by Jorge.ar on 2010-12-27
Hi!! thanks for your reply. I have some questions:
 
> **puppywhacker said:**
> I prefer to use X-Forwarding using SSH, you ssh into the reports server and run the applicaton, I use "xclock" as my favority X testing application. I dont know how to do that, but I will do a google search.
 
> **puppywhacker said:**
> Be very careful when putting firewall rules in, verify them, if you say "allow 6000", it can just as well mean "allow UDP port 6000 from ubuntu to report server"
Do I have to allow UDP on port 6000 from ubuntu to rep. server?? 
 
I have the rules allow TCP 6000 and 6001 from rep. server to ubuntu.
 
thanks!

---

### Post by Jorge.ar on 2010-12-27
Uhmmmm
this look suspicius..
 
on the ubuntu box: 
 
```

[FONT=Consolas][SIZE=3]root@SUS-Xserver:~# echo $DISPLAY[/SIZE][/FONT]
[FONT=Consolas][SIZE=3]:0.0[/SIZE][/FONT]
[FONT=Consolas][SIZE=3]root@SUS-Xserver:~# ifconfig eth0[/SIZE][/FONT]
[SIZE=3][FONT=Consolas]eth0      Link encap:Ethernet  HWaddr 00:11:25:8a:4a:d4  [/FONT][/SIZE]
[SIZE=3][FONT=Consolas]        inet addr:10.245.80.224  Bcast:10.245.87.255  Mask:255.255.248.0[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]        inet6 addr: fe80::211:25ff:fe8a:4ad4/64 Scope:Link[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]        UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]        RX packets:4192 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]        TX packets:44 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]        collisions:0 txqueuelen:1000 [/FONT][/SIZE]
[SIZE=3][FONT=Consolas]        RX bytes:449628 (449.6 KB)  TX bytes:6537 (6.5 KB)[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]        Interrupt:16 [/FONT][/SIZE]
 
[FONT=Consolas][SIZE=3]Xserver:~# export DISPLAY=10.245.80.224:0.0 [/SIZE][/FONT]
[FONT=Consolas][SIZE=3]root@SUS-Xserver:~# xclock[/SIZE][/FONT]
[FONT=Consolas][SIZE=3]Error: Can't open display: 10.245.80.224:0.0 [/SIZE][/FONT]
[FONT=Consolas][SIZE=3]root@SUS-Xserver:~# [/SIZE][/FONT]

```

---

### Post by Jorge.ar on 2010-12-27
Solved!!!
 
in /etc/gdm I added the file custom.conf to enable XDMCP.
 
[http://projects.gnome.org/gdm/docs/2.14/configuration.html#xdmcpsection](http://projects.gnome.org/gdm/docs/2.14/configuration.html#xdmcpsection)
 
thanks

---

