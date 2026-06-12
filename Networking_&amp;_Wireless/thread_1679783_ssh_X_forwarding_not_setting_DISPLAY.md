---
title: "ssh X forwarding not setting DISPLAY"
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by Howard Cheng on 2011-02-01
I have recently encountered the following problem.  I am not sure exactly when it started to happen, but I know I have been using X forwarding over ssh for years without problems.

  At home, I am running Ubuntu 10.04.1 LTS with openssh server  OpenSSH_5.3p1 Debian-3ubuntu5

  In my office, we are using CentOS 5.5 with openssh OpenSSH_4.3p2, OpenSSL 0.9.8e-fips-rhel5

Both my /etc/ssh/sshd_config at home and my ~/.ssh/config has X forwarding enabled.

  When I log in to my home machine from my office with ssh -X -vv host, I got the following:

```
debug2: x11_get_proto: /usr/bin/xauth  list :0.0 2>/dev/null
debug1: Requesting X11 forwarding with authentication spoofing.
debug2: channel 0: request x11-req confirm 0
```But once I log in, I get:

```
home:~>echo $DISPLAY
DISPLAY: Undefined variable.
```I tried setting DISPLAY to localhost:xx.0 (xx from 0 to 10) but none of that works.

I have also tried ssh -Y but the result is the same.

Does anyone know why?

---

### Post by Howard Cheng on 2011-02-02
Actually, I have tried logging in from another machine at home which also runs Ubuntu 10.04.1 LTS and it also doesn't work.

---

### Post by pegranka on 2011-02-07
Check that xauth is installed on the machine you are trying to log in to. ssh uses xauth to authorise the X connection.

---

### Post by Howard Cheng on 2011-02-07
Yes, xauth is installed on the machine.

---

### Post by andrewtappert on 2011-02-23
You may want to adjust the LogLevel in /etc/ssh/sshd_config to see what's happening on the other end of the connection.

If you by chance recently disabled IPv6 on your home system, you may be affected by this issue:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=422327](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=422327)

---

