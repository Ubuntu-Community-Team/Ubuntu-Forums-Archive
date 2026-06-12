---
title: "my netcat doesn't listen..."
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by Mohammad-Hossein on 2011-07-14
Hello,

My necat (nc) doesn't listen!

It means when I write  "nc -l 3333", I can't communicate data with "nc 127.0.0.1 3333" in another terminal!

Also after writing "nc -l 333", I don't see port 333 between the ports which are listening, by "netstat -ln | grep 3333".

What should I do?

Thank you!

---

### Post by matt_symes on 2011-07-14
Hi

What problem are you having ? Take a look at this.

On one terminal that is sending 

```
matthew@matthew-laptop:~/my_documents$ netcat 127.0.0.1 3333
testing testing one two three

```

On the second terminal that is listening (notice the switch).

```
matthew@matthew-laptop:~$ netcat -l 127.0.0.1 3333
testing testing one two three

```

Are you trying to do that. **You must start the listening terminal first.**

Kind regards

---

