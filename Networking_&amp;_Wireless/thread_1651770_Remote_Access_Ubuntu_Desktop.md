---
title: "Remote Access Ubuntu Desktop"
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by EgoGratis on 2010-12-23
What would be the best approach to have access to Ubuntu Desktop remotely **but**:

1.) On that machine there is no person to accept connections (should i only use password in vino server?)
2.) If that PC restarts i should be somehow able to log in remotely (vino server can't do that in secure way?)

Thanks for answers!

---

### Post by spiky001 on 2010-12-23
How about using ssh

---

### Post by EgoGratis on 2010-12-23
Do you mean SSH (openssh-server) + vino for ssh tuneling? Or X11 forwarding over SSH?

Is there a way to log in into gnome desktop session with VNC (remotely)? XDMCP is a option to do that but  i read it is insecure so it should not be used?

---

### Post by spiky001 on 2010-12-23
Think this will help [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by EgoGratis on 2010-12-23
I went trough all this and it is too much for beginner. I need first hand experience and clear direction.

-FreeNX
-X11 forwarding over SSH
-XDMCP 
-something else?

What should i use for secure remote acess to Ubuntu Desktop (login after reboot included).

---

### Post by EgoGratis on 2010-12-23
I have new question:

Is it possible or better yet does VNC (any free  server available for Ubuntu) allow remote login to session (gnome) without XDMCP.

---

### Post by spiky001 on 2010-12-24
Vnc is not secure to use over internet, I dont know if by tunneling it with ssh how secure that makes it **prehaps some one can advise** Do you need to have it Graphical? Ssh is secure but is command line

---

### Post by EgoGratis on 2010-12-24
1.) Yes but is VNC able to log in to gnome session or must the session be runing allready? And if it is, how to do it. Is it posible to SSH in the box, login and then start gnome session (not with root user) and then use VNC to log in to that session?

2.) So far i found XDMCP is for login to the session remotely, but is insecure and only usable for trusted local networks?


3.) I tried SSH -X and it works but i have a problem. When i close SSH client the GUI program is gone? Or how would i keep the GUI program running and when i SSH -X again  to the box call that same running GUI program? Is that possible or not?

4.) What about FreeNX and NX? If i start a new session, does that session close (log out) when i close the client? But it does allow login in to gnome session if i am  correct?

I found this link:

[http://sinewalker.wordpress.com/2007/03/22/remote-desktop-acces-suse-cygwin-x-and-xdmcp/](http://sinewalker.wordpress.com/2007/03/22/remote-desktop-acces-suse-cygwin-x-and-xdmcp/)

---

### Post by Ceiber Boy on 2010-12-26
> **EgoGratis said:**
> 1.) Yes but is VNC able to log in to gnome session or must the session be runing allready? And if it is, how to do it. Is it posible to SSH in the box, login and then start gnome session (not with root user) and then use VNC to log in to that session?

2.) So far i found XDMCP is for login to the session remotely, but is insecure and only usable for trusted local networks?


3.) I tried SSH -X and it works but i have a problem. When i close SSH client the GUI program is gone? Or how would i keep the GUI program running and when i SSH -X again  to the box call that same running GUI program? Is that possible or not?

4.) What about FreeNX and NX? If i start a new session, does that session close (log out) when i close the client? But it does allow login in to gnome session if i am  correct?

I found this link:

[http://sinewalker.wordpress.com/2007/03/22/remote-desktop-acces-suse-cygwin-x-and-xdmcp/](http://sinewalker.wordpress.com/2007/03/22/remote-desktop-acces-suse-cygwin-x-and-xdmcp/)

Try using the nohup command before your ssh -X this means whenyou close the terminal the session you started from it should continue to rum

Good luck

---

### Post by EgoGratis on 2010-12-26
No answers?

But OK i think i understand the situation! For safe remote desktop connection to running GUI session or to login and start new GUI session something like NX technology would be good in the FOSS world. Then Ubuntu would have this kind of support in default installation! Maybe in the future there will be something like this available to FOSS community and then this will work by default in Ubuntu. Certainly something  we could look forward to!

P.S. Ceiber Boy

I will look in to it!

---

### Post by EgoGratis on 2010-12-26
While i was reading about nohup i found a mention of GNU Screen:

[http://en.wikipedia.org/wiki/Nohup](http://en.wikipedia.org/wiki/Nohup)

> There are other ways to accomplish the ability to keep a program running  after the user has been logged out. For example, the program could be  run inside a [GNU Screen]("http://en.wikipedia.org/wiki/GNU_Screen")-style  screen multiplexer. The screen can be then detached. GNU Screen  maintains the illusion that the user is always logged in, and allows the  user to reattach at any time. This has the advantage of being able to  continue to interact with the program once reattached (impossible with  nohup alone).

Does GNU Screen work with GUI aplications and over ssh -X?

---

### Post by EgoGratis on 2010-12-27
OK i will ask it like this:

If i have 2 Ubuntu boxes and I use** ssh -X** to connect  from one to another. Is it possible to:

Open Gedit and write in letters ABCD and then close remote connection. But later on to connect to that same box again and see that already opened Gedit program with ABCD letters in it and write EFGH in it?

This is something i would like to know. If GUI application can still do it's job when ssh -X connection is closed and if it 's still accessible in next connection over **ssh -X** or not? And **how** to do that** if it's possible**! :)

---

### Post by EgoGratis on 2010-12-28
I won't settle for no answer!

---

### Post by spiky001 on 2010-12-28
Dont know this helps I just installed Remmina [RDC) I can connect via ssh, when I close Remmina it leaves the server as I left it.

---

### Post by EgoGratis on 2011-01-22
With RDC i can connect remotely to Ubuntu OS and start GUI session in a secure way? Or is that just for connecting to Windows?

I would like to use ssh -X and leave GUI application running when disconnecting and then connect to that same GUI application again. **Is this possible or not?**

---

