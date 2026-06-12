---
title: "windows network"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by TroyStachnik on 2010-03-14
i will be using my laptop with netbook remix on it at school, i know my login name and password, how do i connect to the server so i can access my files on the network drive registered to my username. (the network is a wired network and i believe my school is running windows server 2003)

---

### Post by johnson.d on 2010-03-15
You can Connect to the windows server by using the following steps:

1) Goto Gnome Menu-> Places-> Connect to server.
2) A window will open.
3) Drop down the menu and select 'Windows share'.
4) Enter the ip-address or the server in 'Server' Field.
5) Enter the login name in 'User name' field.
6) Enter the domain name
7) Click connect and enter the password when asked for.

Now check whether you are able to browse the shares.

---

### Post by Liveman on 2010-03-15
Trying to connect to my Win network via wireless. But impossible to find the network in ubuntu. What am i doing wrong???
//Liveman

---

### Post by RyanRahl on 2010-03-15
try actually seting up your samba config file (/etc/samba/smb.conf). You need to make sure your Samba is presenting itself properly to the windows network if you want to see anything.

---

