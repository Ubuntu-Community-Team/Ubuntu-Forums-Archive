---
title: "Telnet"
date: 2012-05-20
forum: Networking &amp; Wireless
---

### Post by kabukiM0n0 on 2012-05-20
Hey. I did a search but found nothing on telnet. 
I'm trying to get telnet to run on my system - Ubuntu 12.04 with gnome fallback. telnet has been installed, along with LAMP server - gedit the files but still nothing seems to happen. 
I can get into telnet> but it doesn't log in, neither does it seem the server is properly configured - at least my guess would be. 

The information I did manage to get hold off before trying to set this up comes from various different sources as I failed to find one article/video ... that explained from begging to end the complete setup and edit process. Maybe someone can point me in the right direction of knows what or where I went wrong...

Thank you.

K.m

---

### Post by Ms. Daisy on 2012-05-21
Is there any reason you are using telnet instead of ssh?  Ssh is preferred because it's so much more secure than telnet- telnet sends packets in clear text while ssh encrypts all traffic.  Anyone eavesdropping or intercepting packets would be able to read everything on telnet but wouldn't on ssh.  I would venture a guess that you're not finding much on telnet because of that.

I highly recommend you use ssh. And if you plan to have that LAMP server face the internet, then you absolutely need to use ssh. Here's the help wiki.

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by kabukiM0n0 on 2012-05-22
Erm .. because I didn't know you could use ssh as telnet is used. I thought it was just for tunneling - I'll have a read of the article, thank you :)

K.m

---

### Post by roelforg on 2012-05-22
> **kabukiM0n0 said:**
> Erm .. because I didn't know you could use ssh as telnet is used. I thought it was just for tunneling - I'll have a read of the article, thank you :)

K.m

It's easy to setup as well!
```

sudo apt-get install openssh-server

```
will give you a fully working ssh server!

---

