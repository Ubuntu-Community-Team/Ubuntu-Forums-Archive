---
title: "SSH Dynamic Forwarding as SOCKS"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by napalm97 on 2010-03-14
I'm trying to set up a tunnel to dynamically forward all HHTP requests  to remote host.
I do  this test on my localhsot (same result if I try from another PC)
```
ssh -vvv -D1080 localhost
```My Firefox is configured to use SOCKS 5 at 1080.

When I try accessing any web page in client's Firefox, I get this in my ssh session:

```
debug1: Connection to port 1080 forwarding to socks port 0 requested.
debug2: fd 9 setting TCP_NODELAY
debug2: fd 9 setting O_NONBLOCK
debug3: fd 9 is O_NONBLOCK
debug1: channel 3: new [dynamic-tcpip]
debug2: channel 3: pre_dynamic: have 0
debug2: channel 3: pre_dynamic: have 3
debug2: channel 3: decode socks5
debug2: channel 3: socks5 auth done
debug2: channel 3: pre_dynamic: need more
debug2: channel 3: pre_dynamic: have 0
debug2: channel 3: pre_dynamic: have 10
debug2: channel 3: decode socks5
debug2: channel 3: socks5 post auth
debug2: channel 3: dynamic request: socks5 host 66.249.91.104 port 80 command 1
channel 3: open failed: administratively prohibited: open failed
debug1: channel 3: free: direct-tcpip: listening port 1080 for 66.249.91.104 port 80, connect from 127.0.0.1 port 37499, nchannels 4
debug3: channel 3: status: The following connections are open:
  #2 client-session (t4 r0 i0/0 o0/0 fd 6/7 cfd -1)
  #3 direct-tcpip: listening port 1080 for 66.249.91.104 port 80, connect from 127.0.0.1 port 37499 (t3 r-1 i0/0 o0/10 fd 9/9 cfd -1)
debug3: channel 3: close_fds r 9 w 9 e -1 c -1
```I cannot figure out what is administratively prohibited.

My sshd alows these:
AllowTcpForwarding yes
PermitTunnel yes

My ssh config allows these:
   Tunnel yes
   TunnelDevice any:any

I'm using OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
on Ubuntu 9.04

I have read so many postings already but nothing helps... :-(
Please let me know if you have any suggestions.

Thanks!

---

### Post by efflandt on 2010-03-14
Maybe this from man ssh about -D is a clue: "Only root can forward privileged ports."  Does that apply to the port you configure (1080) or the dynamic port 80?

The only thing I know about SOCKS is that the unix ISP that I used for dial up years ago got mighty upset when someone ran an open SOCKS proxy there.  Because that could have allowed anyone from the internet to do anything that would have appeared to come from our ISP (worse than an open smtp relay).  So whatever you do, do not leave your SOCKS proxy open to the internet without any security, or you could get blamed for whatever happens.

Have you ever though of using "squid" (or that may be just a cache)?  Apache can proxy web sites even on private IPs as virtual hosts.

---

### Post by napalm97 on 2010-03-15
Thanks for the reply, efflandt!

I do not intend to leave SOCKS proxy open to the internet without any security, it's tunneled through ssh from my one PC to another, through firewall. Nobody else will be able to use it, unless someone gets my private ssh key [-X

According to the SSH manual pages, 
**-D** [*bind_address*:]*port*
Specifies a local ``dynamic'' application-level port forwarding.
This works by allocating a socket to listen to *port* on the local
side, optionally bound to the specified *bind_address*.  Whenever a
connection is made to this port, the connection is forwarded over
the secure channel, and the application protocol is then used to
determine where to connect to from the remote machine.  Currently
the SOCKS4 and SOCKS5 protocols are supported, and **ssh** will act
as a SOCKS server.

Since I already have ssh encrypted connection, with -D1080 
I create a dynamic application-level port forwarding.

Port 80 should be dynamically forwarded, as if it was originating from the browser on the remorte machine,
and I doubt I will need root access for that. Otherwise we would need root access just to browse the internet.

Just like in this example:
[http://thinkhole.org/wp/2006/05/10/howto-secure-firefox-and-im-with-putty/](http://thinkhole.org/wp/2006/05/10/howto-secure-firefox-and-im-with-putty/)
but there's no need for Putty.

It works for many people, so why am I getting "open failed: administratively prohibited: open failed"?
It must be something obvious that I'm missing.](*,)

---

### Post by napalm97 on 2010-03-19
Is there anybody who can help?

---

### Post by joaquintopiso on 2010-06-25
> **napalm97 said:**
> Is there anybody who can help?

I found these very useful:
[http://ubuntuforums.org/showthread.php?t=1377914](http://ubuntuforums.org/showthread.php?t=1377914)
[http://ubuntuforums.org/showthread.php?t=723025&highlight=socks](http://ubuntuforums.org/showthread.php?t=723025&highlight=socks)

---

