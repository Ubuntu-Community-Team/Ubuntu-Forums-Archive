---
title: "transfer/share files from behind firewall to seperate network using ssh? ftp?"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by johnnyoc3 on 2009-02-25
**the problem**
i am trying to share files with my brother who lives in another part of the country. he is using a couple of windows xp boxes through a router running tomato and im using ubuntu through my school network.


**my setup**
computer A:
i am currently at university and the firewall we have blocks all incoming connections but allows ssh and ftp outgoing connections just fine. I have ssh and ftp servers running on my computer that are accessible from inside my university network but not from outside it due to the firewall.

computer B:
I have set up my brothers router to run the tomato firmware and enabled the ssh server on it. using ssh i have tunneled Internet traffic from my computer at school through my brothers router successfully. He has multiple xp boxes on his home network that are all using windows shares. they also have ssh and ftp clients installed. 


**my goal**
to be able to transfer files to/from the xp boxes in his home network to my computer. I don't really care how but im sure there is a way to do it using ftp or ssh.....possibly with reverse ssh tunneling?

since i can ssh to his router and forward ports is there a way that he could connect to my ssh server or to a samba share on my computer? what are my options for doing this? 



thanks a bunch!

---

### Post by johnnyoc3 on 2009-02-25
i found this tutorial that seems to be what i need. 
[http://www.marksanborn.net/howto/bypass-firewall-and-nat-with-reverse-ssh-tunnel/](http://www.marksanborn.net/howto/bypass-firewall-and-nat-with-reverse-ssh-tunnel/)

i will post my results when i get a chance to try it

---

