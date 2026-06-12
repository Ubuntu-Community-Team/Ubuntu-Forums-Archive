---
title: "Windows socket connection to Ubuntu"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by malcolmne99 on 2010-03-17
[FONT=Arial][SIZE=3]Hello friends, I am a newbie to Ubuntu/Linux so I apologize in advance. I am trying to connect with Winsock – Windows sockets – from a PC running Windows XP with a utility program that enables a dialogue over sockets. I have the “listener” running on Ubuntu on Port 6330. I can telnet to the listener and interact from both the Ubuntu desktop and the XP PC. But my utility program using Winsock is unable to connect. I have no firewalls impeding this.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]Maybe there is a better vehicle than the Windows Winsock.dll? I don’t need network file access, just TCP ports/.sockets.[/SIZE][/FONT]

---

### Post by malcolmne99 on 2010-03-17
I believe it was winsock that had the problems. I switched to "SocketWrench" and it worked out of the box:
 
[http://www.catalyst.com/products/socketwrench/freeware/](http://www.catalyst.com/products/socketwrench/freeware/)

---

