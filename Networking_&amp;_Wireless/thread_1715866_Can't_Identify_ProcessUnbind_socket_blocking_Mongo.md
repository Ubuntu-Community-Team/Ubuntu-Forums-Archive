---
title: "Can't Identify Process/Unbind socket blocking MongoDB.."
date: 2011-03-27
forum: Networking &amp; Wireless
---

### Post by Ropes on 2011-03-27
Hey guys, I've been a long time lurker but this is my first post! I'm running Ubuntu 10.10 64bit, and I'm a newbie when it comes to networking.

My issue is that there seems to be a socket bound to a port blocking MongoDB from accessing it's usual port 27017.  The strange thing that it was working just fine until recently and I can't figure out what I did to screw things up... I can make it use a different port but the reason why it can't bind to the default port and why I can't fix it is really bothering me.  I've tried rebooting the machine even with nothing else running when I try to run Mongo is still blocked giving the following message:
```
ropes@ropes:~/mongodb-linux-x86_64-1.8.0/bin$ ./mongod
./mongod --help for help and startup options
Sun Mar 27 14:08:14 [initandlisten] MongoDB starting : pid=2718 port=27017 dbpath=/data/db/ 64-bit 
Sun Mar 27 14:08:14 [initandlisten] db version v1.8.0, pdfile version 4.5
Sun Mar 27 14:08:14 [initandlisten] git version: 9c28b1d608df0ed6ebe791f63682370082da41c0
Sun Mar 27 14:08:14 [initandlisten] build sys info: Linux bs-linux64.10gen.cc 2.6.21.7-2.ec2.v1.2.fc8xen #1 SMP Fri Nov 20 17:48:28 EST 2009 x86_64 BOOST_LIB_VERSION=1_41
Sun Mar 27 14:08:14 [initandlisten] waiting for connections on port 27017
Sun Mar 27 14:08:14 [initandlisten] listen(): bind() failed errno:98 Address already in use for socket: 0.0.0.0:27017
Sun Mar 27 14:08:14 [websvr] web admin interface listening on port 28017
Sun Mar 27 14:08:14 [initandlisten]   addr already in use
Sun Mar 27 14:08:14 [initandlisten] now exiting
Sun Mar 27 14:08:14 dbexit: 
Sun Mar 27 14:08:14 [initandlisten] shutdown: going to close listening sockets...
Sun Mar 27 14:08:14 [websvr] listen(): bind() failed errno:98 Address already in use for socket: 0.0.0.0:28017
Sun Mar 27 14:08:14 [initandlisten] shutdown: going to flush diaglog...
Sun Mar 27 14:08:14 [websvr]   addr already in use
Sun Mar 27 14:08:14 [initandlisten] shutdown: going to close sockets...
Sun Mar 27 14:08:14 [initandlisten] shutdown: waiting for fs preallocator...
Sun Mar 27 14:08:14 [initandlisten] shutdown: closing all files...
Sun Mar 27 14:08:14 closeAllFiles() finished
Sun Mar 27 14:08:14 [initandlisten] shutdown: removing fs lock...
Sun Mar 27 14:08:14 dbexit: really exiting now
```So I tried running netstat to check the port process to kill...
```
ropes@ropes:~$ netstat -lnptu
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address State PID/Program name
tcp        0      0 127.0.0.1:28017         0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:631           0.0.0.0:*                LISTEN      -               
tcp        0      0 127.0.0.1:27017         0.0.0.0:*               LISTEN      -               
tcp6       0      0 ::1:631                 :::*                          LISTEN      -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                                  -               
udp        0      0 0.0.0.0:41548           0.0.0.0:*                                -               
udp        0      0 0.0.0.0:5353            0.0.0.0:*                                 -               
udp6       0      0 :::36250                :::*                                         -               
udp6       0      0 :::5353                 :::*                                          -               

```Do I have some weird setting that's blocking the association of port bindings to the PID?
so sockstat..
```
ropes@ropes:~$ sockstat -p 27017
USER     PROCESS              PID      PROTO  SOURCE ADDRESS            FOREIGN ADDRESS           STATE
```I'm really confused, it seems like the socket isn't bound at all but Mongo still can't bind to the port, so there's some type of ghost binding?

I've pretty much been following this blog about tracking down port issues:
_[http://www.techrepublic.com/blog/security/list-open-ports-and-listening-services/443](http://www.techrepublic.com/blog/security/list-open-ports-and-listening-services/443)_

but whatever is causing this issue is beyond my knowledge base.
Thanks for any help you guys can give!

---

### Post by michaelshumway on 2011-03-28
i'm having this exact same problem... any ideas anyone?

---

### Post by Ropes on 2011-03-28
> **michaelshumway said:**
> i'm having this exact same problem... any ideas anyone?
I actually found out what the problem was for me at least.  If you installed MongoDB the 'sudo apt-get...' way then Ubuntu seems to boot a mongo DB on startup.  How to turn the damn thing off so I can control in the usual way I'm still trying to figure out....:(

I can connect and use it like a normal database just fine though..

---

### Post by michaelshumway on 2011-03-28
> **Ropes said:**
> I actually found out what the problem was for me at least.  If you installed MongoDB the 'sudo apt-get...' way then Ubuntu seems to boot a mongo DB on startup.  How to turn the damn thing off so I can control in the usual way I'm still trying to figure out....:(

I can connect and use it like a normal database just fine though..

yeah, mongodb runs at startup.  i installed using sudo apt-get as well.  not sure how to clear that port though so that mongo can use it

---

### Post by Ropes on 2011-03-30
Hey you probably found a solution already, but in case anyone else wants a quick fix here's a solution to find and kill the Mongo server.

Get the process list:
```
ps -eF | grep 'mongo\|PID'
```This will return the PIDs which can then be used to kill the process and hopefully close the sockets as well.
```
UID        PID  PPID  C    SZ   RSS PSR STIME TTY          TIME CMD
mongodb   1260     1  0 26316  4316   4 Mar29 ?        00:00:00 /usr/lib/mongodb/mongod --config /etc/mongodb.conf
ropes    19931 18808  0  2239   864   1 03:16 pts/2    00:00:00 grep --color=auto mongo\|PID
```Problem solved..

---

### Post by michaelshumway on 2011-04-05
> **Ropes said:**
> Hey you probably found a solution already, but in case anyone else wants a quick fix here's a solution to find and kill the Mongo server.

Get the process list:
```
ps -eF | grep 'mongo\|PID'
```This will return the PIDs which can then be used to kill the process and hopefully close the sockets as well.
```
UID        PID  PPID  C    SZ   RSS PSR STIME TTY          TIME CMD
mongodb   1260     1  0 26316  4316   4 Mar29 ?        00:00:00 /usr/lib/mongodb/mongod --config /etc/mongodb.conf
ropes    19931 18808  0  2239   864   1 03:16 pts/2    00:00:00 grep --color=auto mongo\|PID
```Problem solved..

awesome, thanks!  i'm able to launch it now.  you rock!

---

