---
title: "help Guru's my port 8181 is closed need it opened"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by Amonsaga on 2009-07-29
ok I need some help I'm trying to play a simple browser based game that uses flash 10.
now I have done the step to make firefox adobe flash only.. that works and its great..
but I play diablo2 and use a site called D2jsp.org.. for forum trolling and what not. but they have a build in game called Ladder Slasher. a simple flash RPG game.
now the tech stuff. I having a had time connecting from ubuntu 9.04 /gnome firefox 3.0.

here the website if people wanna test it on there systems:   [http://ladderslasher.d2jsp.org/ls640.html](http://ladderslasher.d2jsp.org/ls640.html)

I have guarddog as my firewall and have all the ports opened and listed in that.
user defined ladder slasher 8181udp and 8181tcp as well.

ufw - GUI also has the ports in the allow as well.
8181/tcp Allow anywhere
8181/udp Allow anywhere


now the command lines..

**NMAP:**
Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2009-07-29 19:02 MST
Interesting ports on 192.168.0.74:
PORT     STATE  SERVICE
8181/tcp closed unknown

Nmap done: 1 IP address (1 host up) scanned in 13.15 seconds
[B]
sudo lsof -i -n -P[/B]:
COMMAND    PID  USER   FD   TYPE   DEVICE    SIZE NODE NAME
hddtemp         3152  root    0u     IPv4     6903         TCP 127.0.0.1:7634 (LISTEN)
avahi-dae       3432 avahi   14u   IPv4     7898         UDP *:5353 
avahi-dae       3432 avahi   15u   IPv4     7899         UDP *:5712 
cupsd             3461  root    2u      IPv6    7993         TCP [::1]:631 (LISTEN)
cupsd             3461  root    3u      IPv4    7994         TCP 127.0.0.1:631 (LISTEN)
dhclient           3754  root    5u     IPv4     8349         UDP *:68 
[B]
netstat -atlpvn[/B]
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:7634    0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:631      0.0.0.0:*               LISTEN      -               
tcp6      0      0 ::1:631                 :::*                        LISTEN      -               

**sudo lsof |grep -i listen**:
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/photon/.gvfs
      Output information may be incomplete.
hddtemp  3152       root    0u     IPv4       6903                 TCP localhost:7634 (LISTEN)
cupsd      3461       root    2u     IPv6       7993                 TCP localhost:ipp (LISTEN)
cupsd      3461       root    3u     IPv4       7994                 TCP localhost:ipp (LISTEN)


I've tryed everything that i can think of to get around this and I need help been working on the for like 2days with the idea of other flash games might do this to me as well. so I'm trying to learn at the same time.

any help at this point would be awesome.

---

### Post by kerry_s on 2009-07-29
do you have a router? did you check that?

---

### Post by Amonsaga on 2009-07-29
router was something I was thing about too, but after i realized that my windows7 laptop can access the same site just fine and play LS all I want.. I cryed cause it wasn't my ubuntu system.

but for the sake of that argument. yes i tryed port forwarding on my router.

---

### Post by Amonsaga on 2009-07-30
no ideas?

---

### Post by Malac on 2009-07-30
Just joined and played, not quite sure what was going on but all seemed to work okay.
This is with a default Ubuntu 9.04 install. Firestarter set to allow SMB local network traffic only. Have you tried disabling the firewall completely for a short while to see if it works then. If it doesn't then it could be a browser blocking something. Not much help I'm afraid.

---

### Post by Amonsaga on 2009-07-30
Well whats good about you responce is that with ubuntu and on a different machine it doe work, so that means I have some kind if issue on my side.. the other thing you said about SMB i think I forgot to enable that in guarddog. so that might be a possible the problem. I'm check that out really fast.. i'm pretty sure I didn't forget to enable that but I nvr know I make mistakes all the time =D

---

### Post by Amonsaga on 2009-07-31
I fixed it =D I just reinstalled -.- terriable way to do it but it worked. somewhere when installing apts something just didn't take i'll guess is a 9.04 bug I wont know about.. /sigh

---

