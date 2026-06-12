---
title: "trying to ssh..."
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by zander1013 on 2009-02-15
hi,

i am trying to ssh from one ubuntu 8.10 box to another. i have installed openssh-server via apt-get install on both boxes. i can ssh to localhost and the <hostname> of each machine from that machine. i have enabled all the user privleges for each account on each machine.

but when i try to ssh between the boxes it times out on port 22.

i have tried with a single cat 5 cable between each machine and with two cat 6 cables and a switch between each machine.

also i have added 192.168.0.1 for node0 and 192.168.0.2 for node1 to /etc/hosts.

node0<---cat5--->node1

and...

node0<---cat6--->switch<---cat6--->node1

do i need to install openssh-client too?

is there anyway i can do this via wifi? i am using ibm thinkpads with each having wifi. otherwise they have ethernet ports.

please advise.

zander

---

### Post by nixscripter on 2009-02-17
Try pinging one box from another. Does that work?

---

### Post by zander1013 on 2009-02-18
> **nixscripter said:**
> Try pinging one box from another. Does that work?

i resolved this issue. the solution was to append .local to the ssh address. so for example i was trying to ssh node1 from node0 so i had to type 'ssh node1.local' from node0 to connect.

thank you,

-zander

---

### Post by nixscripter on 2009-02-18
Glad to hear it. Please mark the thread as solved (under the Thread tools menu).

---

### Post by Iowan on 2009-02-18
> **nixscripter said:**
> Glad to hear it. Please mark the thread as solved (under the Thread tools menu).
Has that feature been resurrected?

---

### Post by superprash2003 on 2009-02-18
is the SOLVED feature back?? it was taken off for sometime..

---

### Post by zander1013 on 2009-02-18
> **superprash2003 said:**
> is the SOLVED feature back?? it was taken off for sometime..

i do not see the SOLVED feature in the Thread tools menu. i would mark that if i could.

---

### Post by Embun_pagi on 2009-02-25
what should I do to activated openssh-client?... I've check on my ubuntu server and openssh already installed but not yet running.

---

### Post by Iowan on 2009-02-25
> **Embun_pagi said:**
> what should I do to activated openssh-client?... I've check on my ubuntu server and openssh already installed but not yet running.I see you got your answer in your own [thread]("http://ubuntuforums.org/showthread.php?t=1080166") (good idea!)

---

