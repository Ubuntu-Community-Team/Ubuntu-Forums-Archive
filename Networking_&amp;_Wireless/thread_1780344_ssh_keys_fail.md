---
title: "ssh keys fail"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by jarrah-95 on 2011-06-11
i have been trying to create a cluster computer, and as a part of that i need to have password free ssh to all of the nodes from the master node. 
so far i had created an rsa key (ssh-keygen -t rsa) 
coppyed it to the nodes (scp and ssh-copy)
attempted to log in 
and it states that logging in with the key had failed and asks for a password

what is it that i am doing wrong? and how can i fix it? 

thanks 

jarrah

---

### Post by gmargo on 2011-06-12
Did you run the **ssh-add(1)** command to add the key to your authentication agent?

---

### Post by jarrah-95 on 2011-06-12
thanks, that's all i had to do, its working perfectly now

---

