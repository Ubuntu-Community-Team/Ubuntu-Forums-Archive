---
title: "SSH over SSH: port forwarding"
date: 2011-02-06
forum: Networking &amp; Wireless
---

### Post by newbie_toy on 2011-02-06
I have 3 computers; XP, Mac and Ubuntu. I wanted to use Mac connect to Ubuntu by using SSH and also wanted to port forwarding 5999 to Ubuntu's ssh as well. But I got connection refused all the time. Please Help

This is my command on my Mac: 
[HTML]ssh -L 5999:ubuntu:22 username@ubuntu -N[/HTML]

it's connected successfully. 

But when I used XP to connect to Mac via ssh port 5999: ssh winxp -p 5999. I got connected refused. What I was expecting is, I could connect to ubuntu from winxp via mac on port 5999

Am I missing something here?

Thank you so much.

---

### Post by gmargo on 2011-02-06
The full format of -L is "[bind_address:]port:host:hostport", and the bind_address defaults to localhost only.  To listen on all network interfaces, change your command to
```

ssh -L "*:5999:ubuntu:22" username@ubuntu -N

```

---

