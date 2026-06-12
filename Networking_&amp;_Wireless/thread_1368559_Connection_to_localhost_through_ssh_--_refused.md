---
title: "Connection to localhost through ssh -- refused"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by mistakentridgell on 2009-12-30
Hi

I was trying to connect to my localhost using ssh and I am getting the following error:

ssh: connect to host localhost port 22: Connection refused

I checked if the port 22 was open on my system, but I think it is closed. 

Can anyone help me in solving this.

Also, if someone comes up with a solution on how to opne that port, I am assuming it is safe to close that port as soon as the work with it is finished. Could you also tell me how to close that port

System->administration->networktools->portscan->localhost.....

I did not get port 22 in the results. So I am assuming port 22 is not open

---

### Post by xtjacob on 2009-12-30
You need to install and run the SSH server on your computer. To install it open the terminal and type this in: ```
sudo apt-get install ssh
```

---

### Post by mistakentridgell on 2009-12-30
> **xtjacob said:**
> You need to install and run the SSH server on your computer. To install it open the terminal and type this in: ```
sudo apt-get install ssh
```


Thank you, that worked. BUT I thought ssh was already installed, because I was using ssh to connect to remote machines.

Will sudo apt-get install ssh install anything EXTRA than that is already present with the installation of ubuntu

---

### Post by Iowan on 2009-12-30
Ubuntu comes with several (most?) clients installed, but usually comes with few servers pre-installed, so while you can connect to SSH, Samba, (NFS?), or FTP shares without needing to install anything, sharing files usually requires installation.

---

