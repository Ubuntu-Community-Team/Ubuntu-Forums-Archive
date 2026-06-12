---
title: "SSH problem: can't connect to my Ubuntu PC remotely"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by mjc7373 on 2010-08-26
I'm hoping someone can help me here because I haven't figured it out for months now! 

I am running Ubuntu 10.4 on my desktop PC at home. I have a Westell A90-750018-07 DSL router which I have configured port forwarding for ssh service on port 22. 

On my PC terminal, I test ssh like this, and get the following output:

```
Linux user-desktop 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

13 packages can be updated.
0 updates are security updates.

Last login: Wed Aug 25 19:07:31 2010 from localhost
```

I think this means ssh server is up and running. I can connect locally, with my laptop using the same method, but when I try to connect from the Internet like this:

```
ssh user@(exteranl ip address)
```

I get errors that the network can't be found, or that I cannot access the network. Any help would be very much appreciated. Thank you!

---

### Post by amac777 on 2010-08-26
Check your ISP's FAQ page about port blocking and security measures they take. This may not be the issue, but my ISP blocks all common incoming server ports such as 22 (and 80 etc). So I can't connect from the Internet using any standard ports. 

A work around is to modify your ssh configuration file so that it also listens on another random port. Then when you connect, specify the port your setup. That's how I solved the problem.

Edit: if ISP blocking is the problem, another way to fix it without having to change you ssh config is to configure your router to listen to some high port of your choosing and forward it to port 22 of your ubuntu box on your LAN.

---

### Post by Lars Noodén on 2010-08-26
Another question is if you can connect to your ssh server from another machine on the same LAN.  You might have to open up incoming connections for port 22 (ssh) or ease up with tcpwrappers or xinetd.

---

### Post by mjc7373 on 2010-09-02
> You might have to open up incoming connections for port 22 (ssh)...

Do you mean open port 22 on my router? I have already forwarded those ports. 


>  ...or ease up with tcpwrappers or xinetd.

I have no idea what this means. Could you elaborate please?

---

### Post by mjc7373 on 2010-09-02
> modify your ssh configuration file so that it also listens on another random port. Then when you connect, specify the port your setup. 

I switched my forwarded ports on my router to 6000, then modified my ssh config to listen on same port. When I run ssh user@ipaddy it hangs, when I run ssh -p 6000 user@ipaddy, I get "connection refised" instantly.

---

### Post by BkkBonanza on 2010-09-02
After modifying your sshd_config (note, not ssh_config) for the server you need to restart sshd. You can reboot but an easier way is,

**pkill -SIGHUP sshd** which causes it to re-read it's config.

It's also a good idea to confirm which port is being listened on, **sudo netstat -lntp** and also if there are any firewall rules blocking the port, **sudo iptables -L**.

---

### Post by mjc7373 on 2010-09-08
Thanks for all the help, I now have it working. After setting the port to 6000, I restarted the samba daemon and now I can access my Ubuntu PC from the Internet!

---

### Post by mjc7373 on 2010-09-08
> I restarted the samba daemon...

I meant to say, I restarted the ssh server.

---

