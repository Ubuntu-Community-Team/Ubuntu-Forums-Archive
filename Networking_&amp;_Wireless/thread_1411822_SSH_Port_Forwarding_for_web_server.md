---
title: "SSH Port Forwarding for web server"
date: 2010-02-20
forum: Networking &amp; Wireless
---

### Post by Eagleon on 2010-02-20
Hi Guys,

This should be easy but for some reason its not working. I don't have admin rights on one of my local networks to open the firewall for port 80 to make my server accessible remotely (from the internet). I have a remote server (OpenVZ VPS) and I want to port forward so that [http://my-vps-remote-host:8080](http://my-vps-remote-host:8080) will point to my localhost:80 from the internet itself (i can get it to work on the remote VPS server's local network)... 

How could I accomplish this? Basically, I am trying to serve webpages from behind a firewall using a VPS as a hub.

Thanks so much in advance

---

### Post by Brandon Williams on 2010-02-21
```
ssh -R 8080:localhost:80 my-vps-remote-host
```
The -R option says to forward port 8080 on the remote machine (my-vps-remote-host) to port 80 on this machine. The use of localhost assumes you are running the tunnel command on the web server.

---

### Post by Eagleon on 2010-02-21
Hi,

Thanks so much for the response. What do you mean by "The use of localhost assumes you are running the tunnel command on the web server." Does this pertain to SSH or apache?

What I am trying to do is find a way to make my local http server (which is behind a firewall) be accessible from my vps:

typing [www.my-vps-server.com:8080](www.my-vps-server.com:8080) should open up localhost:80 from the internet. Basically, anyone in the world, like a public website. Only, the actual server running that will be local and the VPS acts as a hub to defeat the firewall. I got my localhost:80 to work on the VPS itself, but it is not accessible from the internet unless I use Apache mod_proxy to divert it. But what if I wanted to accomplish the same thing for some other application for example, apart from Apache? 

Thanks again, much appreciated!

---

### Post by Brandon Williams on 2010-02-22
> **Eagleon said:**
> Thanks so much for the response. What do you mean by "The use of localhost assumes you are running the tunnel command on the web server." Does this pertain to SSH or apache?

It pertains to both. You would run the ssh command on the machine running apache. This will connect to the VPS machine, which will open port 8080 and forward any connections to vps:8080 to port 80 on the machine running the ssh command (i.e. the machine running apache).

---

### Post by Eagleon on 2010-02-23
Thanks again, very much appreciated.

---

