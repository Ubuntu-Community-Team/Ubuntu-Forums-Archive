---
title: "Confused with SSH port numbers"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by Shak_Ismonov on 2008-12-05
Hello to all,

I am a little confused about the definition of the ports during the ssh tunnel set up and I hope somebody here will clarify it for me. Let's take an example command to connect my local computer to remote one:

$ ssh -L 50000:localhost:5900 -p 22 [email]user@your.home.pc[/email]

As far as I know in the above example command: 50000 is the port out from my machine, 5900 is the port into the remote machine. But I've seen the usage of additional port definition: "-p 22" or any nonstandard port number such as "-p 1023". Is this port on the remote computer as well? Then why are we using 2 different ports: 5900 and 22?

Thanks for any input in advance.

---

### Post by puppywhacker on 2008-12-05
There are two connections you are talking about here, one is the ssh connection, and the other is a tunnel on top of the ssh connection.

the "-p 22" is the port where the ssh connection is running over. since 22 is the default you don't have to specify that. If you decide to run your ssh-server on port 1023 you will have to specify that in your ssh-client as well

Once the ssh connection has been established from any tcp port on your machine to tcp port 22 on the ssh-server also a tunnel is established. That tunnel starts at your machine at port 50000 and runs through the ssh connection and from there it will reach out to localhost:5900 where localhost is your ssh-server itself.

I guess you want to connect to your VNC server on "your.home.pc" you can create the ssh connection and then point your VNC client to connect to localhost:50000 which tunnels to your.home.pc:5900

---

### Post by Shak_Ismonov on 2008-12-05
Puppywhacker,

Thanks a lot for the clarification. That really helped me. Now, I understand that ssh goes thru more general port to connect two pc's, and the other two ports run inside the ssh tunnel.

So, then if I have to use any port for SSH, do I have to open that port number (ex: port 22) on both remote and local pcs or would it be sufficient to open it on my remote computer only?

Thanks a lot,
---
Shak

---

### Post by Shak_Ismonov on 2008-12-05
Puppywhacker,

Thanks a lot for the clarification. That really helped me. Now, I understand that ssh goes thru more general port to connect two pc's, and the other two ports run inside the ssh tunnel.

So, then if I have to use any port for SSH, do I have to open that port number (ex: port 22) on both remote and local pcs or would it be sufficient to open it on my remote computer only?

Thanks a lot,
---
Shak

---

### Post by superprash2003 on 2008-12-05
open the port only on the pc running sh

---

### Post by puppywhacker on 2008-12-05
For TCP/IP a connection (or better socket) consists of a source and destination ip address and port. your client uses a non-privileged port (higher than 1024) and the server always uses port 22

so if you have two simultanious ssh connections the connection-pair will look like this.

client:1024 - server:22
client:1025 - server:22

Now, your tunnel is not visible on the network all communication is done inside the ssh connection. so if you have a firewall in between you only need to open port 22 to be abled to run SSH, which also will run your tunnel

---

