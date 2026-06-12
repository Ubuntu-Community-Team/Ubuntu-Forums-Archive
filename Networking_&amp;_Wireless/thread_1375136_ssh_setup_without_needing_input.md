---
title: "ssh setup without needing input"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by wbrady4927 on 2010-01-07
I am writing an installation script that sets up ssh keys and then sets up ssh tunnels. I want the ssh connections to be setup by the install script so that the first time you make the connections you don't need to type in yes when it asks if you confirm the brand new host. How can I get around that? All ideas are welcomed!

---

### Post by Lars Noodén on 2010-01-07
One way to do that is to pre-load the known_hosts file, either for the user or at the host level, ~/.ssh/known_hosts or  /etc/ssh/ssh_known_hosts respectively.  

Ignoring the host keys can be done, but then that sets you up to be vulnerable to MIM attacks.

---

### Post by teward on 2010-01-07
> **Lars Noodén said:**
> Ignoring the host keys can be done, but then that sets you up to be vulnerable to MIM attacks.

I agree.  I run an SSH server on my desktop and laptop to allow access to my files while on-campus at CMU, and if you bypass the host keys, you run the risk of attack attempts.  I tried it once...

---

### Post by Lars Noodén on 2010-01-07
I should mention that you can grab public keys from a remote machine using [ssh-keyscan](http://linux.die.net/man/1/ssh-keyscan) and [ssh-keygen](http://linux.die.net/man/1/ssh-keygen).  If the fingerprint is right, then the key is probably legitimate and it can be added to known_hosts.  

```

# clear
echo > /tmp/keys

# grab rsa key
ssh-keyscan -t rsa *server.example.org* >> /tmp/keys
# show fingerprint
ssh-keygen -F *server.example.org* -lf /tmp/keys

# grab dsa key
ssh-keyscan -t dsa *server.example.org* >> /tmp/keys
# show fingerprint
ssh-keygen -F *server.example.org* -lf /tmp/keys


```

---

