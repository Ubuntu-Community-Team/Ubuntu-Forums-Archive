---
title: "Remote Desktop to XP/Vista machines across separate LANs?"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-02-06
I've been finding a lot of relatives are calling me with the most basic computer questions. The kind of thing that to explain to them to navigate to change the settings would take a fair chunk of time. I'd rather have the ability to remote in and just do my thing. But I'm not sure what this entails and I don't want to jeopardize whatever security they have to the public with a target on their forehead indirectly yelling "hack me hack me!"

I run Ubuntu Linux 8.10 64 bit as well as Vista Ultimate.. if I could get this to work in Ubuntu it'd be sweet. Otherwise, I'd be happy with Vista too.

Is there a way I can just have the client install a VNC package and tell me certain numbers and I can hook it all up on my end and BAM, done?

---

### Post by graysky on 2009-02-06
Easy from LINUX or Windows.  Your relatives need to install a vnc server on their box (I'm assuming windows).  TightVNC is a favorite of mine.  If they're behind a router, they'll need to forward the port (default is 5900).  You can then connect (unencrypted and insecure) from your box using any number of VNC clients.  Intrepid comes w/ vinagre but you can get whatever you want.  To connect you'll just need their IP addy.

If you want a more secure solution, have them install FreeSSHd on their windows box ([here is a good guide](http://www.windowsnetworking.com/articles_tutorials/install-SSH-Server-Windows-Server-2008.html)) and have them forward the SSH port on their router, not the VNC port.  Now, you connect to their windows box via ssh and make an [ssh tunnel](http://knoppmyth.net/phpBB2/viewtopic.php?t=19211) for vnc which is HIGHLY secure.

The main security is having them stop the port forwarding in their router when you're finished.

---

### Post by Roasted on 2009-02-06
Gah... forward ports? I'd rather explain to them how to get to device manager than forward ports on routers they may have that I'm not visually familiar with. Good to know, though! I'll write this info down so my more PC savy relatives I can test this with. :)

---

### Post by Roasted on 2009-02-09
Isn't there any free web site that'll allow me to set up an account for users to log in that I can control?

Example - I use a web site geared towards this. I create an account. It gives me a unique URL to send to clients. I link clients and give them the login information. They login, ask if I can take control, I take control and do my thing. Is that possible?

---

### Post by graysky on 2009-02-09
> **Roasted said:**
> Isn't there any free web site that'll allow me to set up an account for users to log in that I can control?

Example - I use a web site geared towards this. I create an account. It gives me a unique URL to send to clients. I link clients and give them the login information. They login, ask if I can take control, I take control and do my thing. Is that possible?

Not to my knowledge.  Why involve a 3rd party anyway?

---

### Post by spynappels on 2009-02-09
There is a purely Windows/Mac system called teamviewer that is worth looking at. No Linux client or host yet though. I've used it with absolutely PC Illiterate people and it works great.

Not found a Linux solution yet though.

---

### Post by Roasted on 2009-02-10
> **graysky said:**
> Not to my knowledge.  Why involve a 3rd party anyway?

Because explaining port forwarding with certain relatives of mine is going to take more effort than it would for me to drive 2 hours to their house to conduct a 5 minute fix.

---

### Post by jaygo on 2009-04-14
I've been really impressed with Teamviewer -- enough so that I paid the $250 for six months (commercial use). The same tool is free for personal use however. I've read that the new version of the client (4.x) works well in WINE but I haven't tested it personall (running it in virtualbox). Their Quicksupport installer is perfect for initiating new connections with less-than-savvy PC/mac users so that was a big selling point for me: no firewall setup required, just point and click, then read me some numbers over the phone.

That said, they offer no linux clients ("servers" might be more appropriate, actually) and so I'm looking into other solutions. VNC works but isn't secure. UltraVNC was a pain to manage and the better encryption caused constant crashes. SSH + VNC could work but requires more work on non-unix machines. At this point, I'm looking into [NoMachine]("http://nomachine.com") which offers clients for win, mac, linux, maybe more and has an [open-source branch]("http://freshmeat.net/projects/nx/") going as well. I've just started playing with the free version and it looks like it requires some interaction with port forwarding, SSH daemons, iptables, and more to install a linux client.

The suggestion above about using a home computer as a repeater is great as it could be a great workaround for firewall configuration.

GLHF

---

