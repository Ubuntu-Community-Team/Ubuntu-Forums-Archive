---
title: "how share files"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by Deicider on 2009-12-12
i have a laptop with karmic and a desktop with jaunty, how do i connect these two so i can share files?
note that both laptop and desktop are connected through ethernet to the router,they share internet,what do i do to share/connect??

---

### Post by pilp4 on 2009-12-12
if your looking for a LAN connection i cannot help you, but there is a great online service called dropbox which once installed automatically syncs two folders on two different computers. there's a link in my sig if your interested.

---

### Post by Dennis N on 2009-12-12
> **Deicider said:**
> i have a laptop with karmic and a desktop with jaunty, how do i connect these two so i can share files?
note that both laptop and desktop are connected through ethernet to the router,they share internet,what do i do to share/connect??

The simple way that I use is to use SSH. Install openssh-server from the Ubuntu repository on the machines, then you can access one from the other using:

```
Places > Connect to Server
```

and filling in the details such as ip address, user name, and password.

Connecting that first time, a nautilus window will open for the remote machine. Set a nautilus bookmark for your (remote) home folder. Next time, you can use the bookmark to connect from nautilus. You then only need the password.

---

### Post by Iowan on 2009-12-12
You will need to install a server component for your sharing protocol on the serving machine(s) the client portion is probably already installed. 
Some options: [NFS]("http://ubuntuforums.org/showthread.php?t=249889"), [FTP]("http://ubuntuforums.org/showthread.php?t=249889"), [SSH]("https://help.ubuntu.com/community/SSH"), [SSHFS]("http://https://help.ubuntu.com/community/SSHFS").

---

### Post by Deicider on 2009-12-12
damn =/
i was hoping that it would be easy like with windows :S

---

### Post by Iowan on 2009-12-12
It's not particularly difficult - the How-To's should help, and the forums should be able to fill in any blanks.

---

### Post by Dennis N on 2009-12-13
> **Deicider said:**
> damn =/
i was hoping that it would be easy like with windows :S

Actually with SSH server the whole thing can be ready to use in a few minutes with the defaults. Later you can do some tweaks on the configuration setup and learn advanced features. SSH (secure shell) in my opinion is a simple and reliable way to go. The openssh-server package handles SFTP (secure file transfer protocol) transfers.

With SSH, you can also run remote applications (programs on the remote computer), or work with remote files from your local machine.

---

### Post by deathbyswiftwind on 2009-12-13
I use samba for my comps. I have an old desktop that I just basically use for storage and with a few minutes of setting up samba I can copy and paste from both comps over my wlan through my router. Its basically like setting up my desktop as a file server but it works great

---

### Post by Deicider on 2009-12-14
can you find me a how to for ssh? i don't know how to install and use it,i tried on the tutorial section but still no luck finding that tut,the search button didn't helped me as always,or better if you know how to do it just share teh knowledge (:

---

### Post by MarkMcLT on 2009-12-14
I actually did this myself last night - very simple. There's a how-to here: 

[https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html)

but there's actually more information there than you need to get going. You really just need to install the ssh server on the machine you want to ssh to, with -

sudo apt-get install openssh-server

You should already have the client installed, so then just go 'ssh <username>@<ipaddress>' on the client machine and you should be prompted for your password on the server machine.

You can install the server on both machines to enable you to login in either direction.

---

### Post by Iowan on 2009-12-14
[Here]("https://help.ubuntu.com/community/SSH") is another SSH link - it also contains the above link...

---

### Post by Deicider on 2009-12-14
i set up the ssh-server on the pc i want to use as a server,the client was already installed on my laptop.
And configured as the Guide was tellin me.
i went to places>connect to server with my laptop and i chose/wrote :

Service type: SSH
Server : 192.168.1.2     (its the ip that ifconfig shows)
While the rest is optional i tried once:
Port: 22    (default)
Folder: /home/deicider/Public

i tried many times without the optional options and it asked to Insert Username and a Password (dunno if its the remote or local pc) and after that it asked me to insert a password (am guessing the connection password)but in the config file i disabled passwords. :S
Anyway,i can't login,am missing something

---

### Post by jflaker on 2009-12-14
> **Dennis N said:**
> Actually with SSH server the whole thing can be ready to use in a few minutes with the defaults. Later you can do some tweaks on the configuration setup and learn advanced features. SSH (secure shell) in my opinion is a simple and reliable way to go. The openssh-server package handles SFTP (secure file transfer protocol) transfers.

With SSH, you can also run remote applications (programs on the remote computer), or work with remote files from your local machine.

Patience is the key....Windows sharing and Linux sharing are different animals...

---

### Post by Deicider on 2009-12-14
also,how do i start/stop an ssh server.

---

### Post by Deicider on 2009-12-15
am actually using PuTTy from the client laptop to connect to my desktop server ,i enter the ip and port of the server and it shows a window that says :
"Login As :"

But i don't know what to type there,i checked the auth log in the server pc:

"Dec 15 07:56:43 desktop sshd[5750]: Connection from 192.168.1.3 port 56362
Dec 15 07:56:48 desktop sshd[5750]: Invalid user deicider from 192.168.1.3"
And PuTTy shows :

"Server unexpectedly closed network connection"

I disabled the need for password in the configuration file according to the SSH guide.
But still asking for password.
What do i do?

---

### Post by Deicider on 2009-12-15
help me, i just wanna transfer files from one to another comp T.T

---

