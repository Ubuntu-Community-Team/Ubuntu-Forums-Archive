---
title: "SSH from restricted network"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by fataki on 2009-10-02
I want to be able to ssh into my server from wherever I might be.
For example my school blocks ports 22 and 2222.

I found few solutions, but nothing nice and clean.

[LIST=1]
[*]Set ssh server to use port 443.
Easy and fast. I don't even use https on my server, so right now it wouldn't be inconvenient.


[*]Web ssh like [consoleFISH]("http://www.serfish.com/console").
I wouldn't want to rely on other services and it's also a security issue.


[*]Install my on web ssh (ajaxterm, anyterm).
These also seems kinda easy.


[*][Tunneling SSH over HTTP(S)]("http://dag.wieers.com/howto/ssh-http-tunneling"))
This seems overkill, but would porbably otherwise be the best solution.
[/LIST]

What do you think? Do you have any other ideas?

---

### Post by kevdog on 2009-10-02
You could also do reverse tunneling since I'm betting your school doesn't except outbound ports but only inbound ports.

---

### Post by fataki on 2009-10-02
My school actually seems to block outgoing port 22. At least I haven't been able to connect to my server from the schools network, even though it works from elsewhere.

My server is on a public ip restricted only by NAT controlled by me.

---

### Post by fataki on 2009-10-02
Oops. They were only blocking 2222, not 22. So now it works after i set the router to forward port 22 (not 2222) to my server.

---

