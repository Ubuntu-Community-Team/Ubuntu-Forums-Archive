---
title: "scp over ssh"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by rponceaci4 on 2010-10-15
Hello, I have a trouble.

I think that should be very easy but I'm not able.

You see, for connect to my job from my house I use ssh -p nnn [EMAIL="myuser@xxx.xxx.xxx"]myuser@xxx.xxx.xxx[/EMAIL] and then for connect to my computer I use again ssh [EMAIL="myuser@mycomputer.xxx.xxx"]myuser@mycomputer.xxx.xxx[/EMAIL] over the same terminal. The problem is when I need to copy some files, normaly from another server I use scp [EMAIL="myuser@xxx.xxx.xxx"]myuser@xxx.xxx.xxx[/EMAIL] and working, but in this case I need scp on [EMAIL="myuser@mycomputer.xxx.xxx"]myuser@mycomputer.xxx.xxx[/EMAIL] and for get access to my computer I need [EMAIL="myuser@xxx.xxx.xx"]myuser@xxx.xxx.xx[/EMAIL].

I've probed scp -p nnn [email]myuser@xxx.xxx.xx:myuser@xxx.xxx.xxx:/Desktop/file.py[/email] /home/Desktop/

But this way doesnt work.

If someone knows to solve that, I would be greatful.

P.D.: sorry for my mistakes, I'm learning english.

---

### Post by luvshines on 2010-10-15
Try this:
[http://cafe.jenkster.com/permalink/cafe/multiple_hop_scp](http://cafe.jenkster.com/permalink/cafe/multiple_hop_scp)

I have just give it a try, working good

For you the syntax would be:
```
scp -p -o "ProxyCommand ssh myuser@xxx.xxx.xxx nc mycomputer.xxx.xxx.xxx 22" myuser@mycomputer.xxx.xxx.xxx:/Desktop/file.py /home/Desktop
```

---

### Post by rponceaci4 on 2010-10-15
Thank you, I'll try this as soom as get in my house

---

### Post by rponceaci4 on 2010-10-18
Hi, I've solved that. 

Firstly I proved "Proxycommand ...." but I didn't get something and then I asked for ProxyCommand in my Job and people told me the server is too old and don't have that.

Well I solved that making a copy with scp between my computer (in my work) and the server and then I had to do a new copy between the server and my laptop (in my house).

In sumary, I did two ssh instead of make a bridge.

Thanks for all.

Rafa

---

