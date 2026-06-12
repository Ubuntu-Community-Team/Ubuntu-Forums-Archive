---
title: "Mythweb remote connections"
date: 2008-05-24
forum: Mythbuntu
---

### Post by oigewan on 2008-05-24
After a clean install, I configured mythweb so that I no longer got the database password configuration issue that seems to plague all users.  I can now connect to my mythtv backend and control it remotely via the mythweb plugin from any computer on my local network.  However, when I attempt to connect via any computer outside this network, the connection will time out.  I have changed the port that apache listens to to port 8000, and have forwarded that port through my router (I know that I tried just forwarding public port 8000 through to local port 80, but that didn't work either).  I have disabled all authentication for mythweb and even set up my iptables to accept all connections.  I have also set up my Mythbuntu box in the DMZ.  Nothing seems to work.  Does anyone on this forum have any ideas that I can try?  Any help would be appreciated.  Thank you for your time and consideration.

---

### Post by oigewan on 2008-05-25
Here are a couple of things I forgot to mention:

1) SSH does not forward through the router either
2) I've tried using two different routers to the same effect (Belkin and Linksys WRT54G w/ Tomato firmare)
3) I've tried Enabling and Disabling MySQL remote connections in the M-C-C

---

### Post by oigewan on 2008-05-25
I found out what the problem was.  The server will accept connections if the client is not on the local network.  However, I was trying to use the external IP to connect to the server from inside the LAN.  Apache needs extra configuration to make this happen.  However, since this is not the aim of my project, I'm not even going to worry about it.  Sorry about the error.

---

### Post by Lester_Burnham on 2008-05-26
Maybe you just need to comment out the 127.0.0.1 in the /etc/mysql/mysql.cnf

---

### Post by mal on 2008-05-26
I regularly connect to my Mythtv server using an SSH tunnel.  To do this from a remote Windows machine, I use Putty and create a tunnel to connect a port on the Windows machine (eg 8890) to 127.0.0.1:80 on the Mythtv box.  I then just enter "localhost:8890" in a browser on the Windows machine and up comes MythWeb.

Obviously, this would also work with a remote linux machine using an appropriate ssh command.

This did not require any special router configuration, other than forwarding the SSH port (22) to the Mythtv server.

Mal

---

