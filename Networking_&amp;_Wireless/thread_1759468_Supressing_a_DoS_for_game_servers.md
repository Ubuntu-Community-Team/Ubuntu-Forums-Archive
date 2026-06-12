---
title: "Supressing a DoS for game servers?"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by Kreative1 on 2011-05-15
Hello, I have a rather intriguing issue. I've been playing with Firewalls for the past four days, and I can't seem to even supress a DoS/DDoS attack. I've been using pure IPTables, UFW, APF, and DDoS Deflate, but nothing seems to be working. I've done research, and the only solution I got is using hardware infront of the actual box, but I can't do that, for I don't have the necessary financial needs. So, my question is...

How can I just have an attack numbed down so that:
1: The server is still playable, and not affected greatly
2: It doesn't use up all the bandwidth.

I really need to just block and drop bad UDF packets so they're not processed, and not even all of them, just so it doesn't doesn't interfere with the server in the ways stated above. 

Also, I'm hosting a Gmod server with srcds, if that helps in anyway. And I really need this done as soon as possible. If you need more information, just ask for it, I'll give you whatever is needed. 

I'll also let you come on my TeamViewer or give ssh access.

My MSN: [email]kylesandlin1@hotmail.com[/email]
Email: [email]Bc.Kreative1@gmail.com[/email]

I really appreciate it! <3

Edit: And my bandwidth limit is 1.5 TBs a month ( 30 days ). So even if I can't block out all the attack

---

### Post by Kreative1 on 2011-05-20
Bump =/ Anyone? I really need this server up >.<

Again, all help is appreciated!

---

### Post by psusi on 2011-05-20
You can't.

---

### Post by Kreative1 on 2011-05-20
Not even a little? =/

Remember, I just need it to block even a bit of an attack, just so a server is still playable, and I don't go over the bandwidth limit

---

### Post by psusi on 2011-05-23
You may be able to make sure that you are ignoring the incoming packets and not responding, causing your upstream to bog down as well, but there is nothing you can do about the downstream being saturated.

---

