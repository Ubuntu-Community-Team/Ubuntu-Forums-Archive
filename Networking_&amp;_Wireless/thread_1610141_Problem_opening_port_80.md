---
title: "Problem opening port 80"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by Hibernate[SWE] on 2010-10-31
Hi!

I've i server written in Java, and when it tries to open a TCP server
on port 80, »BindException: Premission denied» is thrown.
On a previous Ubuntu version this was fixed by something like

```

sudo iptables -A INPUT -i + -p tcp --dport 80 -m state --state ESTABLISHED -j ACCEPT

sudo iptables -A OUTPUT -i + -p tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT

```

but that does seem to help now.

I've tried --sport instead of --dport, as well as excluding -m state --state ESTABLISHED, and I've tested FORWARD.

Any suggestions?

---

### Post by SeijiSensei on 2010-10-31
Try

```

iptables -A INPUT -p tcp --dport 80 -j ACCEPT

```

The "RELATED,ESTABLISHED" options apply to packets sent in response to a request by the local computer.  For instance, rules like these enable remote web servers to send pages to you in reply to a request.

---

### Post by Hibernate[SWE] on 2010-10-31
I've already tried that, and I retried it now; can't say it helped.

---

### Post by SeijiSensei on 2010-10-31
Let's see all the rules then.  "sudo iptables -L -nv"

I presume nothing else is already listening on port 80?  Try "sudo netstat -vnl | grep :80"? Any listeners there?

---

### Post by Hibernate[SWE] on 2010-10-31
Output:

```

netstat: no support for `AF IPX' on this system.
netstat: no support for `AF AX25' on this system.
netstat: no support for `AF X25' on this system.
netstat: no support for `AF NETROM' on this system.

```


I use a rather clean installation of Ubuntu, with only some IDE:s, p7zip-full, Web browsers (Epiphany, Opera and Konqueror), Skype, games (Epiphany), drivers, VLC, GIMP, Inkscape, Java and Compiz.

After the problem was detected I've also installed nmap and nmaspsi4.

---

