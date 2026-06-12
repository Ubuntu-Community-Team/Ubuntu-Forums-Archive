---
title: "scp suddenly not working?"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by mikeg113 on 2010-10-30
I'm trying to copy folders from one ubuntu machine to another. Both have ssh and openssh-server installed and have worked in the past. I'm using "scp -r Pictures username@192.168.1.1:/home/username" after entering the remote password, I get a bunch of lines. What am I doing wrong?

---

### Post by eric_1982 on 2010-11-01
That seems correct to me if you are using this command on the  machine your coping the files from. 


Are you able to just ssh into the machine to test that the ssh server is running correctly?

---

### Post by luvshines on 2010-11-01
> **mikeg113 said:**
> I'm trying to copy folders from one ubuntu machine to another. Both have ssh and openssh-server installed and have worked in the past. I'm using "scp -r Pictures username@192.168.1.1:/home/username" after entering the remote password, I get a bunch of lines. What am I doing wrong?

Can you paste the 'bunch of lines' which are displayed :)

---

### Post by mikeg113 on 2010-11-02
The problem was caused by having the program "fortune" in my .bashrc. After removing it everythings fine. Thanks for your responses!

---

