---
title: "Cannot ssh to *one* server from *one* location; everything else works"
date: 2012-03-16
forum: Networking &amp; Wireless
---

### Post by wolfgangmcq on 2012-03-16
I remotely administer a friend's server. He has a dynamic IP address, so I use freedns.afraid.org to give it a domain name. This server is running an Apache server, an FTP server, and an SSH server for remote administration. All of these services are running fine. 

One day about three months ago, I tried to SSH to the server from work around 10:30, and got an error message. I assumed the server had crashed, since I had SSHed just fine from work to the server around 8:00 that morning. I had my friend restart the server, but it still wasn't working. All of my efforts to track down the problem have been in vain. Since that day, when I attempt to ssh to the server from work, I get:
```

ssh_exchange_identification: Connection closed by remote host
```after a pause of 5 to 8 seconds. I only get this error when I **ssh** to **this** server **from work**--not when I connect to this server from anywhere else, nor when I connect to another SSH server form work, nor when I connect to HTTP or FTP from work. I'm completely mystified, as I can't find anything special about this particular setup that would cause anything to break. I'm using my laptop, so it's not because it's a different computer. The Director of Technology assures me that he hasn't twiddled with the firewall (although someone else might have, it's not particularly likely.) If it helps any, I also have sshguard installed on the server, although the documentation says that if sshguard were causing the problem, it would have gone away by now.

If anybody has any ideas, I'd be very grateful. I was using the remote server to do some testing from work, and not having it available has introduced some complexity that I'd prefer not to have to deal with.

---

