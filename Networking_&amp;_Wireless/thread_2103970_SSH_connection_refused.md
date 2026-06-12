---
title: "SSH connection refused?"
date: 2013-01-11
forum: Networking &amp; Wireless
---

### Post by jldalton97 on 2013-01-11
Every time I try to connect my two laptops via SSH 

```
 ssh [username]@192.xxx.x.xx 
```I get:

```
 ssh: connect to host 192.xxx.x.xx port 22: connection refused 
```What is the problem? Is there something I have to enable on any of the computers?

---

### Post by ahallubuntu on 2013-01-11
You have to install/enable the OpenSSH server on any computer you are trying to connect to with ssh.  Just because you have the ssh client installed doesn't mean the server is installed.

You could simply install the metapackage for ssh that gets you both server and client:

```
sudo apt-get install ssh
```

on the Ubuntu machine you are trying to connect to.

I should mention that enabling the ssh server puts that computer at greater security risk, as port 22 will now be open and anyone on a local network that can access that computer could try to access any user account via ssh.  So if you enable it, be aware of that!

---

### Post by jldalton97 on 2013-01-11
Thanks, works great now. I did that on both machines and now works just as wanted!

---

