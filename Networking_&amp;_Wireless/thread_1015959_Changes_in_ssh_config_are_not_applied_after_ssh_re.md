---
title: "Changes in ssh_config are not applied after ssh restart"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by gegtot on 2008-12-19
Hi all!

I'm trying to change the ssh port to 443. 

**The problem seems to be two-fold:**
1. The changes to sshd_config don't seem to have any effect, not even after a reboot, as if I'm configuring the wrong file.
2. It seems like the stop, start and restart commandos don't work.

**How to reproduce:**
1. sudo gedit /etc/ssh/sshd_config
2. In sshd_config, change "Port 22" to "Port 443"
3. Save sshd_config and exit.
4. sudo /etc/init.d/ssh stop
5. sudo /etc/init.d/ssh start
6. ssh -p 22 localhost

**Expected result:**
[LIST]
ssh: connect to host localhost port 22: Connection refused
[/LIST]


**Actual result:**
[LIST]
[*]The authenticity of host 'localhost (127.0.0.1)' can't be established.
[*]RSA key fingerprint is 5e:a2:8a:6c:c4:a8:57:52:2c:7c:bd:80:2f:26:3a:b0.
[*]Are you sure you want to continue connecting (yes/no)?
[/LIST]

---

### Post by kevdog on 2008-12-19
Can you verify listening ports with the use of nmap please?

---

### Post by gegtot on 2008-12-19
Thanks for replying!

The output is as expected. Port 22 is still open. I'd expect 443 to be open...

xxxxx@viao:~$ nmap localhost 

Starting Nmap 4.62 ( [http://nmap.org](http://nmap.org) ) at 2008-12-19 21:14 CET
Interesting ports on localhost (127.0.0.1):
Not shown: 1711 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
111/tcp  open  rpcbind
631/tcp  open  ipp
5900/tcp open  vnc

---

### Post by kevdog on 2008-12-19
Can you post your sshd_config and ssh_config files?  Something is strange here?  You might also want to temporarily bump up your log level on the server and then examine the logs after starting the daemon, or simply start the daemon on the command line to see if any errors are generated.

---

