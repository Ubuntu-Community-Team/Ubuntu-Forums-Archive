---
title: "accessing xampp from a windows computer"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by seth556 on 2008-12-04
I have xampp setup on my computer (ubuntu) but I'm trying to access it from another computer on the network. I've tried putting in my ip address with no luck. I'm thinking there's some firewall I need to disable.

---

### Post by Iowan on 2008-12-05
Might be firewall, but might also be that the server is set to listen only on "localhost".  Check if */etc/hosts* has a line:```
127.0.1.1 <your hostname>
```.

Might as well include a [link]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by seth556 on 2008-12-05
I checked and it does have that line.

---

### Post by jmoorse on 2008-12-07
Can you access it from the Ubuntu box it is installed on?

---

### Post by seth556 on 2008-12-08
Well yes.

---

### Post by jmoorse on 2008-12-08
On the windows box go to:

start > run > enter 'cmd'

type in:

telnet (ip of xampp box) 80

Let me know if you get "Connection Failed" or just a black screen

---

### Post by seth556 on 2008-12-08
I got a black screen with a cursor type thing going and then it went back the the cmd line without any messages.

---

### Post by jmoorse on 2008-12-08
That indicates that you were able to make a connection on port 80 (HTTP), indicating no firewall blocking inbound TCP80 on that box

Can you try perhaps a different browser to [http://(ip-of-xampp-server](http://(ip-of-xampp-server))  ?

---

### Post by seth556 on 2008-12-08
Well I've tried Firefox and IE with no luck.

---

### Post by jmoorse on 2008-12-08
Is there another system within your lan to test http access to the xampp box with?

Also you may want to try restarting xampp:

sudo /opt/lampp/lampp restart

---

### Post by seth556 on 2008-12-09
I'll go try a live cd.

---

