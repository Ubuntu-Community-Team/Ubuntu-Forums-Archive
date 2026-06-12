---
title: "Problem With SSH"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by long.thai on 2010-03-21
Hi all.

Now, I'm using Ubuntu 9.04 x86_64 and trying to setup SSH to connect to my machine externally.

The open ssh server is already installed and I can using **ssh localhost**. Moreover, I also forward port 22 to my machine and check using [http://www.canyouseeme.org/](http://www.canyouseeme.org/)

Everything seem to be ok, but when I trying to connect using **ssh -vvv <ip-address>** I receive the following common error:
```

OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to ip-address [ip-address] port 22.
debug1: connect to address ip-address port 22: Connection refused
ssh: connect to host ip-address port 22: Connection refused

```I try to debug using **sudo /usr/sbin/sshd -d**, but it seems that there is no connection at all:
```

debug1: sshd version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-d'
debug1: Bind to port 22 on 0.0.0.0.
Server listening on 0.0.0.0 port 22.
debug1: Bind to port 22 on ::.
Server listening on :: port 22.

```The sshd is running so that I can using **ssh localhost**. So, is there anything that I miss? And, how to fix that.

PS: I currently run all commands on the machine which I intent to to connect to in the future. I read somewhere that the problem comes from the internal connection which means if I try to connect using different network than the server machine, I'll succeed. Is that correct?

---

### Post by jfparis on 2010-03-21
Did you set up a firewall on that machine? Have you open the ssh port on the interface that is associated with <ip-address>?

---

### Post by chenxiaolong on 2010-03-21
You could see if there is a "ListenAddress   " line in /etc/ssh/sshd_config. If there is, comment it out and restart the ssh daemon with "sudo /etc/init.d/sshd restart."

I hope this helps.

---

### Post by long.thai on 2010-03-21
> **jfparis said:**
> Did you set up a firewall on that machine? Have you open the ssh port on the interface that is associated with <ip-address>?

I installed Firewall but choose not to enable it. Do you mean make the port forward? I already did it and check using [http://www.canyouseeme.org/](http://www.canyouseeme.org/) Is there any ways to check them?

> You could see if there is a "ListenAddress " line in /etc/ssh/sshd_config. If there is, comment it out and restart the ssh daemon with "sudo /etc/init.d/sshd restart."I checked and it is already commented.

---

### Post by long.thai on 2010-03-21
Well, look like that the problem comes from internal access. I using a machine from different network and it successfully access to my computer. Although there is still a problem remain, but I guess it's ok now.

THank you all :)

---

