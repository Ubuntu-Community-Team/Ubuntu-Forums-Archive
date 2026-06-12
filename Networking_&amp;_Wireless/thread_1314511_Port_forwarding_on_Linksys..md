---
title: "Port forwarding on Linksys."
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by dimamali on 2009-11-04
Hello community!
I have a problem in port-forwarding my ssh port. I'll be quick. Here is my case.
Linksys router wag200g
Desktop PC with Linksys wireless card and ubuntu 9.10.
Laptop Acer 1690, ubuntu 9.10.
I do know how to port-forward and i have done so.
ssh works fine from desktop to laptop, but when i try to do the opossite the laptop is refused.
I did a port scan on both pcs just to find out that my desktop has port 22 closed.
No matter what i tried on my router configuration, the port is still closed.
Could my Linksys wireless card be blocking me?
Any suggestions?

---

### Post by Iowan on 2009-11-04
Probably silly question, but just to cover bases:
You have SSH server installed (and running) on desktop?

---

### Post by dimamali on 2009-11-05
Yes, i have it installed on both pcs and yes it is up an running.
Could it be a faulty key assignment?
Could it be that both the ssh-servers and both ssh-clients are listening on the same port?
Does anyone know if i can change the default port for ssh?
I see it has two configuration files, the ssh_config and the sshd_config where the port is referenced as 22. I guess the one file is for the server app and the other for the client one?
I was thinking of moving the port a bit higher just for security reasons.

---

### Post by Iowan on 2009-11-05
ssh_config would be for the client, sshd_config would be the server. Notice the line(s) in */etc/ssh/sshd_config* that reads:```
# What ports, IPs and protocols we listen for
Port 22

```The clients have the option to specify which port to use:
 ```
ssh -p2200 me@myserver
```but they'll default to port 22 unless you specify otherwise.

---

### Post by dimamali on 2009-11-12
Excuse me for the late answer.
So, to make it clear, i have both server and client installed on both pcs. Would it be right if all the ports were changed to the same? For example port 4545 for both server and client in both pcs? Could that be the problem?

---

### Post by Iowan on 2009-11-12
Right offhand, it seems like it it should work.
I'm no SSH guru, though...

---

### Post by dimamali on 2009-11-13
Ok, thanx a lot i will give it a try.

---

