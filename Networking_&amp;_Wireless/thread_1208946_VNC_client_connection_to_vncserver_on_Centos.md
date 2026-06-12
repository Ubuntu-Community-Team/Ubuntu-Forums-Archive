---
title: "VNC client connection to vncserver on Centos"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by daniel_93 on 2009-07-09
Hi everyone, 

I&#7743; trying to connect to a sever running Centos 5, using VNC but I keep getting the same error:

VNC Viewer Free Edition 4.1.2 for X - built Mar 24 2009 19:52:30
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
vncviewer: unable to open display ""

I configuered the server and everything looks okay, a friend of mine is using OpenSuse and he was able to connect to the server, and I used his machine to test my user account and configuration, and it worked, so I think the problem is on my client in ubuntu.

I tried using Vinagre but as soon as I click "connect" a dialog comes out saying "connection closed".

I am running Ubuntu 9.04, it would be great if someone could help me with this.

Thanks

---

### Post by superprash2003 on 2009-07-10
try opening vnc from the terminal by typing **vncviewer x.x.x.x** where x.x.x.x is the ip of the machine you want to remote control

---

### Post by daniel_93 on 2009-07-10
Hi super,

I run vncviewer from the terminal and got this:

daniel@daniel-laptop:~$ vncviewer 158.97.88.6
vncviewer: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or director

I tryed looking for this lib in the package manager but I couln't find it, I found libstdc++6 and libstdc++6-4.1-dev, but I still get the same error when running vncviewer :(

regards.

---

### Post by superprash2003 on 2009-07-11
your trying to connect to a server without GUI right? in that case VNC will not work , you shold try using ssh

---

### Post by daniel_93 on 2009-07-13
no, actually I&#7743; trying to connect with GUI, the SSH works fine, but I just can't get the graphical part to work.

the server is working okay, a friend of mine managed to connect with GUI, he is using OpenSUSE, I used his computer to connect to the server using my account and it worked, so the problem is on the client.

---

### Post by kallek on 2009-09-12
I too have problems connecting with vncviewer/vinagre to a Centos machine.

Port forwarding w. ssh:
```
ssh -L 5900:localhost:5900 me@xxx.xxx.xxx.xxx
```
sets up the tunnel, but trying to connect w. vncviewer fails:
```
vncviewer localhost:5900
Connected to RFB server, using protocol version 3.7
vncviewer: VNC server closed connection
```

Vinagre works as bad:
```
vinagre localhost:5900
```
A little box pops up telling me that "Connection closed, Connection to host localhost:5900 was closed."

Not using a ssh tunnel doesn't work either:
```
vinagre me@xxx.xxx.xxx.xxx:0
```
or
```
vinagre xxx.xxx.xxx.xxx:0
```
also results in the little "connection closed" box.

The result is similar with vncviewer:
```
vncviewer xxx.xxx.xxx.xxx:0
vncviewer: ConnectToTcpAddr: connect: No route to host
Unable to connect to VNC server
```

I have configured the Centos machine to "Allow users to view you desktop".
Further, I used to be able to connect to the Centos machine (a half year ago or so).

---

### Post by kallek on 2009-09-16
Reply to myself:
I just failed starting the vnc server on the Centos machine. A bit silly.

---

