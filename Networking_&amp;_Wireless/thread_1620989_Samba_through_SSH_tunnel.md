---
title: "Samba through SSH tunnel?"
date: 2010-11-13
forum: Networking &amp; Wireless
---

### Post by dacoconuttman on 2010-11-13
Hello. I have a server running Ubuntu Server 10.04 that is a VirtualBox/Samba/SSH server. I have port forwarding set up for ports 22 and 3389 (SSH and RDP) and I want to access the Samba share without opening any other ports. I can connect to it from my internal network, but I want to be able to access it from school. My best guess would be to tunnel the Samba port through SSH, but I don't know how. I will be connecting to it from Ubuntu 10.10 Desktop.
Thanks.

---

### Post by spiky001 on 2010-11-13
It,s possible to do but not straight forward have a look [here]("http://jgranto.dyndns.org/joe/SSH/index.htm")

---

### Post by dacoconuttman on 2010-11-13
Thanks, but these instructions are for WinXP, so will this work in Ubuntu 10.10 Desktop?

---

### Post by spiky001 on 2010-11-13
I,ve never done it they say that samba causes the problem only using it,s own port 445. I just use vnc over ssh to get my file, but thats on lan, vnc is supposed to work the same over net

---

### Post by gradinaruvasile on 2010-11-13
Why use both when you already have ssh? There is winscp and other clients that work well.
Using the default ports is not wise for well known services like RDP and ssh.

---

### Post by dacoconuttman on 2010-11-13
VNC won't work because my server has no GUI, but how do you use it over SSH? I've never done port tunneling before.

---

### Post by gradinaruvasile on 2010-11-13
VNC over ssh is easy - just bind it only to localhost, then connect to it via ssh tunneling - Remmina (vnc/ssh/rdp client for linux) for example has this option.

---

### Post by dacoconuttman on 2010-11-13
> **gradinaruvasile said:**
> Why use both when you already have ssh? There is winscp and other clients that work well.
Using the default ports is not wise for well known services like RDP and ssh.
Thanks. I just realized the samba share I have is my server's home folder, which I can easily SSH into. By the way, I have the RDP port open for VirtualBox.

---

### Post by spiky001 on 2010-11-13
just use putty on xp machine ssh into ubuntu

---

### Post by dacoconuttman on 2010-11-13
> **gradinaruvasile said:**
> VNC over ssh is easy - just bind it only to localhost, then connect to it via ssh tunneling - Remmina (vnc/ssh/rdp client for linux) for example has this option.
I have no experience SSH port tunneling, only copying files and using it to control my server with CLL. Also, would I be able to do this with a jailbroken iPod Touch?

---

### Post by dacoconuttman on 2010-11-13
> **spiky001 said:**
> just use putty on xp machine ssh into ubuntu
I'll try that.

---

### Post by spiky001 on 2010-11-13
I know you wanna keep least amout of ports open maybe change ssh port number it,s a common number

---

