---
title: "Reverse SSH Tunneling"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by xiainx on 2011-02-02
Hi all,
I want to be able to SSH into my computer that I can't expose port 22 on. I've tried the ssh -R ... several times, but can't manage to make it work.

I have my home computer (want to SSH into), server (can SSH into), and some computer I want to SSH from.

Do I need to install the sshd on the machine I want to SSH into? What are the commands I need to enter to forward from my server to my home computer?

Thanks!

---

### Post by Brandon Williams on 2011-02-03
Let's say that A is the machine you want to ssh into, B is the machine that you can ssh into, and C is the machine you want to ssh from.

First, you must install openssh-server on machine A. You can't ssh into it if it's not running sshd.

Then, on machine A, reconfigure sshd so that it only listens on localhost. To do this, use sudo to edit /etc/ssh/sshd_config and change this line: ```
#ListenAddress 0.0.0.0
``` to this ```
ListenAddress 127.0.0.1
``` After changing the config, restart sshd on machine A with ```
sudo service ssh restart
```.

Now, set up the tunnels. On machine A, open the reverse tunnel listening on port 222 on machine B ```
ssh -R 2222:localhost:22 B
``` On machine C, open a local tunnel listening on port 2222 to tunnel packets to port 222 on machine B ```
ssh -L 2222:localhost:2222 B
```

Once the tunnels are set up, you can ssh from C to A via B with ```
ssh -p 2222 localhost
```

---

