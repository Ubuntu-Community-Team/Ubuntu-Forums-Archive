---
title: "SSH problem: No /etc/init.d/sshd script present"
date: 2011-08-15
forum: Networking &amp; Wireless
---

### Post by kpuz on 2011-08-15
Hi,
I am trying to install the ssh server on my computer so I can access it using my phone. I installed the server using:

```
sudo apt-get install openssh-server
```
and then setup the sshd_config file in the /etc/ssh/ folder. But when I tried to restart the server using
```
sudo /etc/init.d/sshd restart 
```I got an error saying that there is no sshd file. When I navigate to the directory /etc/init.d/, sure enough, there is no sshd script (there is the ssh script though).
How should I go about solving this problem?

---

### Post by Doug S on 2011-08-15
yes, your installation seems correct. To restart the SSH server daemon you enter:```
sudo /etc/init.d/ssh restart
```

---

