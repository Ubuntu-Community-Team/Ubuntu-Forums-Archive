---
title: "SSH help"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by stretch427 on 2009-05-02
I have just created a Homes server with Ubuntu 9.04 and I'm running 8.10 on my desktop. 
from terminal how to I access my server? Command?

---

### Post by blackened on 2009-05-02
Do you have openssh set up on the server? If so, you should be able to

```
ssh <server's ip>
```

If you've not yet set it up, then [let me google that for you]("http://lmgtfy.com/?q=set+up+ssh+jaunty").

---

### Post by stretch427 on 2009-05-02
When I type that I get 

The authenticity of host 'ip(ip))' can't be established.
RSA key fingerprint is big long number
Are you sure you want to continue connecting (yes/no)?

---

### Post by hotstovejer on 2009-05-02
You want to type yes in there. What is asking is "Should this connection be trusted?"

As soon as you type yes and it generates the RSA key, you will be on your server.

Hope this helps!

Jeremy

---

### Post by stretch427 on 2009-05-02
Thanks my friend!

Now being that I'm new to ssh I want to try and secure my stuff and I read their Openssh-server how to, but it didn't make sense. 

How am I supposed to secure it? 

That's the Public Key Authentication, but how to?

---

