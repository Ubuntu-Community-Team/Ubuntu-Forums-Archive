---
title: "ssh tunnel service ports made openly available to local network?"
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by burgundy on 2009-12-24
I'm trying to SSH tunnel two ports from a remote server onto a local server and then allow other computers to connect to the local server's ports.

The local server has no problems connecting to its own localhost ports with VNC/DAAP clients.

But as soon as I try to using the local server's IP 192.168.x.x or a domain name, nothing works because Ubuntu 9.10 and other linux distros are too smart to late strangers in their house.

How do I open up these ports on the local machine that aren't a service running on the local machine?  A Port Scan shows 22 as open with the IP and domain name, but that is only because the magic of apt-get setup SSH for me.

I tried firestarter, ufw, gfw, and changing my iptables, but nothing worked...

These are the results of a $ netstat -an | grep "LISTEN "

user@server:~$ netstat -an | grep "LISTEN "
tcp        0      0 127.0.0.1:3689          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:5900          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp6       0      0 ::1:3689                :::*                    LISTEN     
tcp6       0      0 ::1:5900                :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN    

Thanks for your time.  If this is the wrong place to ask, pleas re-direct me.

---

### Post by puppywhacker on 2009-12-24
your netstat shows that VNC is listening to port 5900 only on the local interface.

So I think you want to port forwarding using SSH. You can open let your remote client listen to port 5123 that ssh will forward to the local server side localhost:5900 (localhost is relative to the ssh server). Once you connected the SSH tunnel, you can VNC from the remote client to localhost:5123

```
ssh user@server -L 5123:localhost:5900

```

I used port 5123, but also 5900 would have been fine, but I decided to deviate a bit to avoid confusion.

Alternative to VNC, with X forwarding you can run applications remotely. If you ssh into a server just run for instance xclock to see run the application on the server displayed on the client (which is also running an Xserver)

---

