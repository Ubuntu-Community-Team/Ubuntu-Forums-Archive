---
title: "MythTv frontend help"
date: 2008-08-18
forum: Multimedia Software
---

### Post by lintoon on 2008-08-18
I have a main "server" which is running Mythtv backend and frontend.
The frontend works fine and I can watch TV on the "server".

I would like to be able to run the frontend on my laptop over my home lan but am unable to.
When I launch the frontend from the Applications menu nothing happens.
When I type "mythtv" in terminal I get the following and it just sticks there:

2008-08-18 21:59:43.621 Using runtime prefix = /usr, libdir = /usr/lib
2008-08-18 21:59:43.629 XScreenSaver support enabled
2008-08-18 21:59:43.629 DPMS is active.
2008-08-18 21:59:43.630 Empty LocalHostName.
2008-08-18 21:59:43.630 Using localhost value of Toshub
2008-08-18 21:59:43.631 Testing network connectivity to 192.168.1.7
2008-08-18 21:59:43.650 New DB connection, total: 1

Any ideas???

Thank you.

---

### Post by lintoon on 2008-08-18
I forgot to mention that /etc/mythtv/mysql.txt has the same user details as the "server".  
I have set "DBHostName" to the ip address of my backend.

---

### Post by wyliecoyoteuk on 2008-08-18
"mythtv" runs the backend.
You need to run "mythfrontend" in the terminal, and connect to your server.

---

### Post by lintoon on 2008-08-18
Thanks for you advice.  I tried mythfrontend and this is the output:

2008-08-18 22:14:36.083 Using runtime prefix = /usr, libdir = /usr/lib
QServerSocket: failed to bind or listen to the socket
2008-08-18 22:14:36.085 MediaRenderer::HttpServer Create Error
2008-08-18 22:14:36.093 XScreenSaver support enabled
2008-08-18 22:14:36.094 DPMS is active.
2008-08-18 22:14:36.094 Empty LocalHostName.
2008-08-18 22:14:36.094 Using localhost value of Toshub
2008-08-18 22:14:36.095 Testing network connectivity to 192.168.1.7
2008-08-18 22:14:36.129 New DB connection, total: 1

I port is set to 6543 within mysql.txt on both systems.  Is that right??

Cheers.

---

### Post by lintoon on 2008-08-18
What's happening to my typing?  That should have read

"The port is set to 6543 within mysql.txt on both systems. Is that right??"

---

### Post by lintoon on 2008-08-18
PS

Cool sig wyliecoyoteuk

---

### Post by lintoon on 2008-08-18
Also, the details in /etc/mythtv/mysql.txt and ~/.mythtv/mysql.txt are identical.

---

### Post by lintoon on 2008-08-19
anyone????

---

### Post by lintoon on 2008-08-19
Update: It's working. Here's how for anyone interested.

On the backend system I ran:

sudo killall mythtv-backend
then 
sudo /etc/init.d/mythtv-backend start

On the remote frontend I ran

mythfrontend

This launched setup so I confirmed my settings and clicked next a few times and now I can watch TV on my laptop on the lan. 
It's still working after rebooting both systems. Fantastic.

---

### Post by wyliecoyoteuk on 2008-08-24
Glad you got it working.
Glad you liked the sig :)

sorry to be so slow replying, but I scan a lot of forums.

---

### Post by lintoon on 2008-08-25
No problem.  Thanks for your help.

---

