---
title: "Testing port forwarding with gobby"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by sanderd17 on 2010-01-25
Hi, is there someone out there who wants to help me testing gobby?

I need to know if gobby can be reached from outside my network.

What I have done:
[LIST]
[*]I've installed Gobby 0.4.9 (the gobby package in synaptic)
[*]I went to my router and configured this line:
```

No.   LAN-IP-Addr.  Protocol-Type  LAN-Port Public-port  enable
1.    192.168.1.3   TCP            6522     6522         yes

```
[*]I openend Gobby and started a session without password
[/LIST]

My ip address is 81.241.88.207

What you should do to help me test it:
[LIST]
[*]install the same gobby version
[*]start gobby and choose to participate in a session
[*]fill in my ip address (81.241.88.207), the port should be ok and then click connect
[*]you should see some files I tried (for now a test and a test.tex file) and be able to edit them.
[/LIST]

If anyone would help, it would be great. hope it works from the first time.

---

### Post by sanderd17 on 2010-01-25
oh yeah, i also openend the port with the command
```

iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 6522 -j ACCEPT

```

It could be that you'll have to do the same, I don't know

EDIT: found that command here:[http://www.linuxquestions.org/questions/linux-security-4/how-to-open-ports-in-ubuntu-451282/]("http://www.linuxquestions.org/questions/linux-security-4/how-to-open-ports-in-ubuntu-451282/")

---

### Post by sanderd17 on 2010-01-26
I found someone who wanted to test it and it didn't work. I even tried to forward port 80 to my computer but only computers inside my network could see my /var/www directory. has anyone got an idea?

---

### Post by altonbr on 2010-09-24
Try using 'gobby-0.5' instead of 'gobby' and if you're setting up a dedicated server, check out 'infinoted' instead of 'sobby'. They are the new development focus and have more features but are beta instead of stable.

You should probably set up a dedicated server. I'm not sure if a client session can work as a server over the web.

---

