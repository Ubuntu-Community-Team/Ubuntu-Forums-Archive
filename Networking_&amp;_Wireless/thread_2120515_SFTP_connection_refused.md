---
title: "SFTP connection refused"
date: 2013-02-26
forum: Networking &amp; Wireless
---

### Post by Jonor on 2013-02-26
Hi, i'm trying a phase of having only ubuntu 12.10 on my two boxes that are joined wirely by a router to a modem. 
It has gone very well overall but my usual sftp using a terminal between the boxes persistently gets the connection refused.
It is of the form :
 sftp Joey1@192.168.0.3:/home/Joey1

My usual response is to check ~.ssh/known_hosts with :
$ ssh-keygen -f  "/home/Joey1/.ssh/known_hosts" -R 192.168.0.3
but there is no .ssh/known_hosts folder/file in either system ?
So i made one for each, but still no luck. SFTP has been so straight forward for my simple setup until now, 
i'm reluctant to dive into anything more complex unless there is no other choice.
Looking at some of the other threads here, i'll post the verbose response :

```
Joey@JJ:~$ sftp -vvv Joey1@192.168.0.3:/home/Joey1 
OpenSSH_6.0p1 Debian-3ubuntu1, OpenSSL 1.0.1c 10 May 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.0.3 [192.168.0.3] port 22.
debug1: connect to address 192.168.0.3 port 22: Connection refused
ssh: connect to host 192.168.0.3 port 22: Connection refused
Couldn't read packet: Connection reset by peer
Joey@JJ:~$ 

```

Looking in /etc/ssh/ssh_config for clues there are only 5 unchecked lines in that file, being :

```
Host *
SendEnv LANG LC_*
HashKnownHosts yes
GSSAPIAuthentication yes
GSSAPIDelegateCredentials no
```

Any help appreciated.

---

### Post by squigish on 2013-02-26
A connection refused error is something you need to fix on the server (the computer you're connecting to).  

I'd advise that you troubleshoot using ssh. That's what sftp is calling anyways, and it's a bit easier to use.  

On the machine you're trying to connect to (192.168.0.3), is the sshd (ssh daemon) service running?  This is what listens for incoming ssh connections.  If it's not running, or not configured properly, you'll get a "connection refused" error.

sshd is configured by the file /etc/sshd_config so that would also be a good place to start looking.

---

### Post by papibe on 2013-02-26
Hi Jonor.

```
ssh: connect to host 192.168.0.3 port 22: Connection refused
```
This usually means these possibilities:
[LIST]
[*]openssh-server is not installed on the server (192.168.0.3).
[*]The ssh service is down on the server.
[*]The ssh service is using a custom port instead of the default 22.
[*]openssh-server is not well configured (check /etc/ssh/sshd_config on the server).
[*]Port 22 is blocked by another software on the server side. Check you firewall or iptables.
[/LIST]
Just some thoughts. Let us know how it goes.
Regards.

---

### Post by Jonor on 2013-02-26
Thanks for both of your replies, you both got me there. It can't run if it isn't installed ! 
Openssh-server is now on both machines and works perfectly.

---

