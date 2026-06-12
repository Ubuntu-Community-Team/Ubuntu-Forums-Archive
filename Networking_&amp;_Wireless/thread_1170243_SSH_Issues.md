---
title: "SSH Issues"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by ceylonerana on 2009-05-26
I'm using Ubuntu 8.10 and usually transfer data through SSH between my desktop and Laptop.I installed SSH server to both computers. I can access the Laptop from my desktop. But cannot access Desktop from Laptop. When I try to do so it shows following

Cannot display location "sftp://192.168.2.4/"
Host Key verification failed

Why is this happen?

Any suggetions?

---

### Post by ceylonerana on 2009-05-26
Hey Guys...

I accessed my Desktop from my Laptop using the Terminal. Its pretty simple.
I typed in the terminal,

ssh -l[USERNAME] -g[IP Address]

Then it asks the password of the remote computer. That's all :guitar:.

---

### Post by iiska on 2009-05-26
Your laptop's ~/.ssh/known_hosts file probably contains different host key entry for ip 192.168.2.4 than your actual desktop's host key.

Try to access your desktop using terminal with following command:

$ ssh -o 'StrictHostKeyChecking=ask' 192.168.2.4

Then ssh should inform you if this is the case and it will also show the line which contains the key in known_hosts. You could remove that line and then try again.


ps. Seems like you solved this, while I was posting my reply. Maybe your sftp app had stricter host key checking than commandline ssh app.

---

