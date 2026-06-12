---
title: "SSH/Forwarding Question"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by Whisp3r on 2010-08-31
I have my desktop set up at home to let me SSH in, or to port forward 8080 so I can browse the web securely (ha) from outside my home connection. If I wanted to set up my SSH server to port forward another port, say, 1701, in Telnet, so I have a secure telnet session on port 1701, what do I need to do?

Me -> My home box -> server I'm telneting into on port 1701.

---

### Post by dmizer on 2010-08-31
> **Whisp3r said:**
> I have my desktop set up at home to let me SSH in, or to port forward 8080 so I can browse the web securely (ha) from outside my home connection. If I wanted to set up my SSH server to port forward another port, say, 1701, in Telnet, so I have a secure telnet session on port 1701, what do I need to do?

Me -> My home box -> server I'm telneting into on port 1701.

Rather than tunnel telnet, why not just SSH into your home box, and then telnet into the second server from there?

---

### Post by CharlesA on 2010-08-31
> **dmizer said:**
> Rather than tunnel telnet, why not just SSH into your home box, and then telnet into the second server from there?

+1. You'd be better off just using SSH for both machines. Telnet isn't encrypted.

---

### Post by BkkBonanza on 2010-09-01
Assuming you have to use telnet only because ssh isn't an supported on some device...

Your question is a bit confused. Do you mean "proxy" instead of "port forward"? ie. are you using the ssh -D option to run a SOCKS proxy or have you just setup a single tunnel just for web browsing on 8080. 

If you use a tunnel then you are doing it the painful way. Using the SOCKS method you can access anything via ssh without any further tunnels. 

ssh -fND 8080 user@home

Telnet doesn't directly support SOCKS proxies but you can run tsocks to trick it.

tsocks telnet target_ip 1701

This proxies through ssh to your home machine where a connection is opened to the target_ip:1701 for telnet.

First time you need to make sure /etc/tsocks.conf has the correct proxy port, in this case 8080. tsocks is in the Ubuntu repos.

Oh, and since ssh is in the background don't forget to kill it after.

---

