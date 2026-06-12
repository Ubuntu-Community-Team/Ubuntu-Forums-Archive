---
title: "Port 21 &amp; 22 Cannot  Open"
date: 2011-04-16
forum: Networking &amp; Wireless
---

### Post by ishanexd on 2011-04-16
Hi, I think I posted in the right placed. Yes I have searched the forums and tried possible fixes proposed in similar posts as this one. I simply cannot get ports 21 and 22 open. I installed ssh and vsftpd and the ssh-server. I have configured my wrt300n linksys to forward both 22 and 21 to both my macbook ip as well as my linux box. I am running out of options and hope someone can find me a solution. My computer science bud told me to make my own server and I haven't rested for the past 3 days. Thus I qualify as a Server Noob..but this is the last thing I need.

---

### Post by ishanexd on 2011-04-16
I got 22 working but not 21.

---

### Post by flyingsuperhigh on 2011-04-30
How did you get 22 to work. I am on the same boat as you, my friend told me to set up a server. I tried everything. I assigned a static LAN ip to my server. I forwarded port 22 on my router's site. Still no luck. I can ssh into the server from a local computer but not from a public ip. Also when I try to see whether port 22 is open on canyouseeme.org I get an error with the reason being: connection timed out.

thanks.

---

### Post by patryk77 on 2011-04-30
> **flyingsuperhigh said:**
> I forwarded port 22 on my router's site. Still no luck. I can ssh into the server from a local computer but not from a public ip.

First thing to do is make sure you don't have a firewall running and blocking the ports...

Second of all, if you can connect from another computer on the LAN you should be able to connect from the outside too if the port is forwarded properly. In that case, it may mean your ISP is blocking access to port 22 and you can try something else, like forwarding public port 2222 from your router to private port 22 on your server.

---

