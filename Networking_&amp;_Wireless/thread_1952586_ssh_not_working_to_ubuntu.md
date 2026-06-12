---
title: "ssh not working to ubuntu"
date: 2012-04-04
forum: Networking &amp; Wireless
---

### Post by bmike1 on 2012-04-04
Well.... the title says it all. When I ssh to my laptop from ubuntu it goes through but I can not ssh to the ubuntu. when I do the connection times out. I now know that openssh-server is the daemon that listens for ssh requests and that the error means openssh-server is not installed. However if I try to install it with apt I am told:
  openssh-server is already the newest version.
  openssh-server set to manually installed.
I know port 22 is open
You know.... this is my printserver and I also am having problems getting the XP machine to print. Perhaps I should reinstall because it was printing at one time.

---

### Post by ajgreeny on 2012-04-04
Perhaps there is a clash between your print server port and ssh, both trying to use port 22.

I always change the ssh port on my system as suggested in some ubuntu literature on configuring ssh.  You just need to change the port lines in the /etc/ssh/sshd_config and ssh_config files.
[SSH/OpenSSH/Configuring]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring") 
[https://help.ubuntu.com/10.10/serverguide/C/openssh-server.html](https://help.ubuntu.com/10.10/serverguide/C/openssh-server.html)

Worth a try, surely?

---

### Post by bmike1 on 2012-04-04
Yes worth a try.... please.... what is the proper syntax to ssh to it after a change the port? 
Is it 'ssh <ipaddress>:<port>?'

---

### Post by bmike1 on 2012-04-04
nope.... didn't work. with the appended ':22' it says'service not known and without it still times out. Did I do it wrong?

---

### Post by ajgreeny on 2012-04-05
The simplest way to make sure this happens is to change the port used in both the sshd_config and the ssh_config files of all the machines you use.  That means that the client will look for the server on port ####, eg 2299 (whatever unused port you choose) and the server will be listening on that same port as well.

If you do that you will not need to specify the port used when connecting from the client to server, as they will both automatically use the new one chosen by you.  I know it works as that is what I have done between my family's computers.

If you want to leave the clients as port 22 default, you will need to specify the server's port you have chosen when connecting to your server with ```
ssh *<user@IP>* -p ####
```

---

