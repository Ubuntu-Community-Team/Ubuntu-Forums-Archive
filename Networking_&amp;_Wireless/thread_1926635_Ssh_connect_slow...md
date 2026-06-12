---
title: "Ssh connect slow.."
date: 2012-02-16
forum: Networking &amp; Wireless
---

### Post by eladner on 2012-02-16
I have an issue when using SSH from my Ubuntu 11.04 machine to anywhere else (worked fine under 10.10), the connection takes 12-16 seconds.  

I've read all the posts about UseDNS no, and other networking related issues, but after running both sides of SSH in debug, the bizarre thing is the delay seems totally on the client (Ubuntu side).


Debug from Client:

[email]blah@blarg:~/.ssh[/email]$ ssh -vvvl blah server
OpenSSH_5.8p1 Debian-7ubuntu1, OpenSSL 1.0.0e 6 Sep 2011
debug1: Reading configuration data /home/blah/.ssh/config
debug1: Applying options for *
debug3: cipher ok: arcfour256 [arcfour256,arcfour128,arcfour]
debug3: cipher ok: arcfour128 [arcfour256,arcfour128,arcfour]
debug3: cipher ok: arcfour [arcfour256,arcfour128,arcfour]
debug3: ciphers ok: [arcfour256,arcfour128,arcfour]
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0

 (pause here for 12-16 sec, lines after the pause are almost instant)

debug1: Connecting to pasmsor2 [999.99.99.999] port 22.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/blah/.ssh/id_rsa" as a RSA1 public key
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
etc, etc.

Debug from Server:
debug3: fd 4 is not O_NONBLOCK
debug1: Server will not fork when running in debugging mode.
debug3: send_rexec_state: entering fd = 7 config len 337
debug3: ssh_msg_send: type 0
debug3: send_rexec_state: done
debug1: rexec start in 4 out 4 newsock 4 pipe -1 sock 7
debug1: inetd sockets after dupping: 3, 3
debug1: audit connection from 999.99.99.99 port 34339 euid 0
Connection from 999.99.99.99 port 34339

The debug on the server side does not even show any output until the "Connecting to.." line from the client, so all the debug output from the server takes place 0.5 seconds before I get a command prompt in the client window.

Any ideas?

---

### Post by Perkins on 2012-02-21
I can't say for certain, I'm not an SSH expert, but since the question is several days old I'll give it a stab, my best guess is that the newer install is using elliptic curve encryption, which takes more processor power to run, and it's the calculation time on that that is slowing you down.  I could, of course, be wrong, but it might be worth looking a the cpu usage while it's pausing like that to see.

---

