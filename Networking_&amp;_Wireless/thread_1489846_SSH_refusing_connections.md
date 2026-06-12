---
title: "SSH refusing connections"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by janthes on 2010-05-21
Hi,

My ssh mysteriously stopped working yesterday on my 10.4 server and I'm at a loss getting it running again. The error message my client gave:

```

Nighcrwaler:` james$ ssh -v james@192.168.1.100
OpenSSH_5.2p1, OpenSSL 0.9.8l 5 Nov 2009
debug1: Reading configuration data /etc/ssh_config
debug1: Connecting to 192.168.1.100 [192.168.1.100] port 22.
debug1: connect to address 192.168.1.100 port 22: Connection refused
ssh: connect to host 192.168.1.100 port 22: Connection refused
Nightcrawler:~ james$

```

Doing some googling, I've tried the following to get it working:

-> I double checked that openssh-server was installed using aptitude (it is).
-> I removed my known_hosts on my client
-> On my server, I 'tail -f' the auth.log while trying to log in and no new output is listed
-> Double checked ufw, port 22 and port 443 is allowed (443 is how I remote access my LAN, and SOCKS5 at an untrusted AP)
-> I flushed iptables
-> 'sudo service networking restart'
-> Rebooted
-> Temporarily disabled key based authentication
[updated] -> Run /etc/init.d/ssh retart and sudo service ssh restart
[updated] -> ssh localhost also returns a 'connection refused error

My server is set with a static IP and can ping my router as well as google, and it's self is pingable. Other services like Samba aren't having any problem. My clients are a MBP runnin SL, a Ubuntu PC, and a dual boot Ubunt/Win7 PC, and *ALL* give me the same message. Help would be GREATLY appreciated. Thanks!

---

### Post by wheredidrealitygo on 2010-05-21
can you ssh in from the localhost? 

log into the actual server and ```
ssh -v localhost
```

try ```
sudo /etc/init.d/ssh restart
``` to verify the ssh daemon is actually up and running, and re-verify the ports listed in your /etc/ssh/sshd_config.

possibly post your sshd_config as well.

---

### Post by janthes on 2010-05-21
Thanks for the reply, wheredidrealitygo!

I neglected to add that I also restarted ssh using init.d and service too in my op, and obviously it didn't work. [added to OP]

As for ssh -v localhost, I get the same error.

My sshd_config: [http://pastebin.com/FP2XaMBc](http://pastebin.com/FP2XaMBc)

---

### Post by wheredidrealitygo on 2010-05-21
I assume specifying the port has the same effect?

```
ssh -v server@192.168.1.100 -p 443
```

post your sshd_config?

---

### Post by janthes on 2010-05-21
Yeah, same thing. Also, I posted my sshd in my previous post, you must have looked at the post while I was editing.

---

### Post by wheredidrealitygo on 2010-05-21
Your AllowTCPForwarding is misspelled in yours, try removing it/commenting/fixing spelling, the ssh daemon wouldn't even restart properly because of it on my system. Also, using your (slightly modified) config file, since you disabled key based authentication, there's also no password authentication enabled, might want to look into that.

Looking forward to hearing how it goes.

*edit* - default sshd_config for comparison [http://pastie.org/private/odyjveqzgczncvlv399gq](http://pastie.org/private/odyjveqzgczncvlv399gq)

---

### Post by janthes on 2010-05-21
BINGO! Your the man wheredidrealitygo! Thanks a ton! Don't know how I overlooked that typo...

---

