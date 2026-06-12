---
title: "Connecting from university through SSH"
date: 2012-09-25
forum: Networking &amp; Wireless
---

### Post by fzaffa on 2012-09-25
Hi everyone,
this is my first message, and since i'm not an expert in this forum i hope it's posted in the right section, if not, my apologizes. 

I take this opportunity to introduce myself: I'm a 18 year old student, from italy. I just started aerospace engineering in Milan. I had used ubuntu and debian for some years, and learned a lot.

Now, let's jump to my question: I'd like to connect from the university (laptop) to my computers at home, through SSH, but i have some doubts. I know i can connect to only one computer by forwarding the 22 port to my desktop ip, but it's not enough.  I'd like to be able to connect to *every* computer in the LAN, but i have no ideas on how i could do this. I know port forwarding works only with an ip, so how can I, if I can, choose from remote to what computer connect?

Thank you for the time you spent reading, and sorry for my English. I'm not a native speaker as you read.

Franceco

---

### Post by redmk2 on 2012-09-25
> **fzaffa said:**
> Hi everyone,
this is my first message, and since i'm not an expert in this forum i hope it's posted in the right section, if not, my apologizes. 

I take this opportunity to introduce myself: I'm a 18 year old student, from italy. I just started aerospace engineering in Milan. I had used ubuntu and debian for some years, and learned a lot.

Now, let's jump to my question: I'd like to connect from the university (laptop) to my computers at home, through SSH, but i have some doubts. I know i can connect to only one computer by forwarding the 22 port to my desktop ip, but it's not enough.  I'd like to be able to connect to *every* computer in the LAN, but i have no ideas on how i could do this. I know port forwarding works only with an ip, so how can I, if I can, choose from remote to what computer connect?

Thank you for the time you spent reading, and sorry for my English. I'm not a native speaker as you read.

Franceco
Do you need to connect simultaneously?  If not, once you have connected to the first host in the LAN you can connect to the second host via SSH from the first.

I don't connect from the WAN side, but I do hop from one host to another like this:

host1..ssh to host2>>> host2..ssh to host3>>> Host3..ssh to host4  and so on...  When you exit from each host you will move back down the chain.

---

### Post by fzaffa on 2012-09-25
Wow, quite messy! if it's the only way to go without buying more ips, ok! thank you so much for the answer!

---

### Post by Lars Noodén on 2012-09-25
You could use one computer as a 'jump host' and connect to the others via it.  Or you could forward other ports than port 22 to your other computers.

---

