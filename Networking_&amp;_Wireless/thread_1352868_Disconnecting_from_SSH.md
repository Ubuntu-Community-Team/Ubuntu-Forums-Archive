---
title: "Disconnecting from SSH"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by asai on 2009-12-12
Hi,
I have an issue with SSH on one of my servers.
The server is an 8.04 LTS.

When I start the server I'm unable to log in through SSH from a client.
I have to log on directly on the server. There I run this command:
```
ssh-keygen -q -f /etc/ssh/ssh_host_key -N '' -t rsa1
```
Now it's possible to log in. However after a few minutes the connection is dropped and i get the following message when I try to log back in:
```
ssh: connect to host 10.10.160.4 port 22: Connection refused
```

I have 3 other servers running, but this does not happen on these servers.

Any suggestions on this matter?

---

### Post by earthpigg on 2009-12-12
have you looked at the log files on that one server?

anything obvious distinguishes this server from the others? example: is this one server wireless for some reason, and the rest wired?

---

### Post by asai on 2009-12-12
All servers are on the same wired network.

Found these lines in the auth.log file:
```
Dec 12 20:46:20 xbmc sshd[756]: Server listening on :: port 22.
Dec 12 20:46:20 xbmc sshd[756]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
Dec 12 20:47:57 xbmc su[7504]: pam_unix(su:session): session closed for user root
```

---

### Post by earthpigg on 2009-12-12
that server otherwise has a stable connection? ie: clients connecting for whatever else the server is used for don't randomly drop?

---

### Post by jobix on 2009-12-12
That second line seems strange:
> error: Bind to port 22 on 0.0.0.0 failed:

0.0.0.0? It's as if there's something messed up with the IP address.

You might also want to compare the ssh_config and sshd_config files of the bad server with those of a good server.

---

### Post by asai on 2009-12-14
I agree that the second line from the log file is strange.
I have set up an static ip adress. Perhaps something wrong with this? I installed the openssh-server package when the server had DHCP ip adress and changed it to static.

---

### Post by asai on 2009-12-21
I never found any real solution for this problem, so I reinstalled the system. Works perfect now.

---

