---
title: "Can't connect to company's network"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by deathoftheweb on 2009-09-15
I can't connect to my company's network. I'm running Ubuntu 9.04. I go to places/connect to server. Then I click SSH. I type in the IP address and click connect. It connects to the IP address but it requires a username and password.

From what I understand there is no password for the system. You just type the user name in and you can access the server. I can log in with the Macintosh computers just fine without a password. 

What am I doing wrong? How can I log in without a password? 

The employees aren't happy with me.

---

### Post by deathoftheweb on 2009-09-15
Oh and the Server is Running Mac OSX. That might have something to do with it.

---

### Post by i.r.id10t on 2009-09-15
Well, if you are typing in an IP and getting a user/pass prompt, it means you are already on the network.

You want to connect to a network share.  If you have windows machines mapping drives, then it is almost certainly a samba share, not a SSH connection....

---

### Post by deathoftheweb on 2009-09-15
Can you please elaborate? 

The server is running OSX Server edition. I don't know if it would be windows mapping or not?

---

### Post by wojox on 2009-09-15
Well what happens when you type in the optional information like

Port: 22

User Name: <your user name>

---

### Post by deathoftheweb on 2009-09-16
I entered the information and it says "permission denied."

---

