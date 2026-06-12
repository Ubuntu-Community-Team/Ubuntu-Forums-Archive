---
title: "Backwards in a ssh tunnel"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by emjay86 on 2009-04-07
Hi all..

I'm wondering how to go backwards in a ssh tunnel.. The case is that I have a little linux server behinds a gprs sender.. But the netprovider for the gprs have all ports closed towards the little server.. Therefore I have to use a client from the little server to establish the connection to my larger server. I can do that from some scripting an stuff, but I was wondering how to "use" the ssh tunnel from the large server to the little server when I use the little server as the client..

Hope you get my point (:

Thx

---

### Post by emjay86 on 2009-04-07
When the connection is established from the little server to the large server, is it then possible to make a normal ssh request from the large to the little, and then use the same tunnel?

---

### Post by doas777 on 2009-04-07
what you are describing is a persistent tunnel. usually you need  a pair of routers to set that up. I'm sure it's possible to do with just pure tunneling, but i think you will prolly have problems setting up dynamic tunnels to work as persistent ones. 
just a hunch. if you prove me wrong, please post back so we all learn a little.

good luck,

---

### Post by doas777 on 2009-04-17
you might be able to acheive this with 2 tunnels. just create a script to map a ssh connection/tunnel from the big server to the little and execute it as soon as you connect from the little to the big. you may be able to automate the process.

---

### Post by ktrnka on 2009-04-19
This is very simple to do:

From your little server:

```
ssh -R 4342:localhost:22 user@bigserver
```

Then on the Big server:

```
ssh -p 4342 user@localhost
```

You can replace 4342 with another port number if you wish, just make sure it's not in use if you choose a different one.

---

### Post by kevdog on 2009-04-19
Um - yeah -- Reverse Tunneling anyone?

---

### Post by ktrnka on 2009-04-19
> **kevdog said:**
> Um - yeah -- Reverse Tunneling anyone?

Hey hey now let's not mock anyone because they may not know/understand what Reverse tunneling is - Hence the original question. Instead of being arrogantly sarcastic, you could have provided links/references to further their knowledge on Reverse Tunnels. Please limit these types of comments as they help no one.

---

