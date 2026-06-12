---
title: "SSH port forwarding problem"
date: 2010-08-15
forum: Networking &amp; Wireless
---

### Post by gummo on 2010-08-15
I would like to be able to access my desktop remotely without having it exposed directly to the internet. So what I've done is I've installed an ssh-server on an old P4 as well as on the desktop. This way I only have to open 1 port (well 2; see below) in my router and forward it to the P4 so the ssh-server on the desktop is not exposed to the internet. I ssh over internet into the P4 and from there over LAN into the desktop, so far I've got X-forwarding and vnc to work but I can't figure out how to copy files over from my desktop to my laptop or the other way around.

This is my setup:
A: Laptop with Windows 7
B: P4 Ubuntu 10.04 acting as 'gateway' to ssh into from my laptop over the internet to access desktop on LAN (ssh-server on 23232)
C: Desktop Ubuntu 10.04 (ssh-server on 23231)

Everything is behind a NAT router with only ports 23232 and 23230 forwarded to B.
The reason I opened 23230 is because I'm using port forwarding (see step 2 below) so I can connect directly from my laptop to the desktop after I've set up the forwarding (needed for easy file-transfer using winscp?). At any rate, I am testing this all locally so the ports forwarded in the router are moot at this point.

I've added the keys from the relevant machines to both ssh-servers, the keys themselves are also protected with a pass. So when I connect it looks for the key, if it finds it it prompts me for the pass of that key at which point I'm logged in.

These are the steps I take:

1)Connect from A to B:23232 (enabling X-forwarding) using putty
No problems here.

2)In the terminal from step 1 (so on B over ssh) “shh -p 23231 -L 23230:login@C:23231 login@C”
What I'm trying to do here is forward B:23230 to C:23231 so I can connect winscp/putty from A (over the internet) to B:23230 which should then forward winscp/putty to C:23231 (over lan) auto-magically. I've tried a couple of ways here (-A/-R/login@localhost) but they all result in the same outcome of step 3.

3)Connect from A to B:23230 using winscp or putty
This results is an immediate “connection refused” message, what am I missing here?

Logging in directly from A to both B:23232 and C:23231 works at this point, but from A to B:23230 does not. I've looked at auth.log (ssh on verbose) but nothing shows up.

Any help/tips would be much appreciated.

---

### Post by chopinhauer on 2010-08-15
> **gummo said:**
> 
2)In the terminal from step 1 (so on B over ssh) “shh -p 23231 -L 23230:login@C:23231 login@C”


```

ssh -p 23231 -g -L 23230:C:23231 login@C

```

Note the '-g' option that allow remote hosts (A) to connect to locally forwarded ports.

Personally I find your setup overly complicated: if you use the same (and weak) password on box B and C, a brute force attack against the box B, if successful will give the attacker an access to box C. Note that most attacks are automatic attacks from infected (Windows) computers, they'll probably won't try to connect to port 23232.

Exposing an 'ssh' server directly to the Internet is quite secure, if you are so concerned about the security of box C, why don't you disable password logins and use an RSA key?

---

### Post by gummo on 2010-08-15
> **chopinhauer said:**
> ```

ssh -p 23231 -g -L 23230:C:23231 login@C

```
Awesome, merci. I needed both the -g option and to remove the login part from the -L option; exactly as you said.

> **chopinhauer said:**
> 
Personally I find your setup overly complicated
Hehe yea I tend to do that, blame it on a lack of knowledge. Just wanted a way to fully control my desktop without having any ports to it opened. I use WOL over the internet to turn on my P4 which I then use to turn on the desktop. That way I'm securely in control of everything and with VNC enabled I can use my desktop like I'm sitting behind it.

> **chopinhauer said:**
> 
why don't you disable password logins and use an RSA key?
I do use RSA keys. The password is used to unlock the key, not to log into the server (at least that's my understanding).

---

### Post by chopinhauer on 2010-08-15
> **gummo said:**
> 
I do use RSA keys. The password is used to unlock the key, not to log into the server (at least that's my understanding).


If you use RSA keys just put:
```

PasswordAuthentication no

```in */etc/ssh/sshd_config* on your **ssh** server and all brute force attacks against it will fail miserably (and the automatic attack script will probably crash on the attacker's machine). Thus you can expose directly your C machine to the Internet.

Note that since you use port forwarding the only way to access your machine will be through the **ssh** server and that is security enough for most purposes.

---

### Post by gummo on 2010-08-15
> **chopinhauer said:**
> 
```
PasswordAuthentication no

```in */etc/ssh/sshd_config*

Just double checked and that option is indeed disabled in both config files. I've been through quite a few guides and forumposts trying to get this last part to work. I found many useful tips and tricks (like disabling aforementioned option among others) but I don't remember reading about the -g option. The man pages just confused me even more :p

So thanx again chopinhauer.

---

