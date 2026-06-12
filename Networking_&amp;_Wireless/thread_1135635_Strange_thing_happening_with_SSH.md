---
title: "Strange thing happening with SSH"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by hempyelmo on 2009-04-24
Hi,

Here's the situation. I want to access with SSH from everywhere to a cluster that I built. The frontend computer is connected to a router (Trendnet TEW-633GR) which is configured to forward port 22 as described in the page: [http://portforward.com/english/routers/port_forwarding/Trendnet/TEW-633GR/SSH.htm]("http://portforward.com/english/routers/port_forwarding/Trendnet/TEW-633GR/SSH.htm"). It has also a routable static IP, let's say 1.2.3.4.

On the frontend, sshd is up and running. The router has a wireless network configured. I can connect to its wireless network and access the frontend with SSH with the static IP 1.2.3.4. However, I can't do the same when I'm not on the wireless network and using the network at my office, i.e.:

```

me@office# ssh -vvv me@1.2.3.4
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config   
debug1: Applying options for *                           
debug2: ssh_connect: needpriv 0                          
debug1: Connecting to 1.2.3.4 [1.2.3.4] port 22.
debug1: connect to address 1.2.3.4 port 22: Connection timed out
ssh: connect to host 1.2.3.4 port 22: Connection timed out

```

Now, the strange thing is that I can connect from my home with ssh:
```

me@home# ssh me@1.2.3.4
me@1.2.3.4's password:

```

It works! (I did not put the -vvv option here obviously to encourage you reading further...)

I haven't put any filter on the router (mac or IP) and I can ping it.

What could it be? How can I connect to the cluster from where I work most of the time?

Thanks

---

### Post by hempyelmo on 2009-04-24
Development:
In fact, I'm not able to ping **everytimes**... Sometimes it work, other times not. Looks like a router issue to me... But I would like to know what you folks are thinking.

---

### Post by hempyelmo on 2009-04-28
I agree this forum is not well suited for that type of question. My apologies :/.

---

