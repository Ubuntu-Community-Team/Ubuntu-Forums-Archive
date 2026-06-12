---
title: "Newbie, Help Needed!!"
date: 2012-06-21
forum: Mythbuntu
---

### Post by K9KungFu on 2012-06-21
Hi,

I am having problems setting up Mythbuntu.  I have the backend and  frontend on the same PC, static IP configured on the wireless card (no  LAN connected) this static address set on the backend and frontend along  with the port address.  I have double checked the password is the same  but when I launch the frontend it cannot connect to the database, I have  tried setting front & backend to the loopback address to eliminate  an IP problem but without success.  Any help will be gratefully received  as I have just cancelled Sky and have 3 weeks to build a replacement  PVR!!

J

---

### Post by tgm4883 on 2012-06-21
> **K9KungFu said:**
> Hi,

I am having problems setting up Mythbuntu.  I have the backend and  frontend on the same PC, static IP configured on the wireless card (no  LAN connected) this static address set on the backend and frontend along  with the port address.  I have double checked the password is the same  but when I launch the frontend it cannot connect to the database, I have  tried setting front & backend to the loopback address to eliminate  an IP problem but without success.  Any help will be gratefully received  as I have just cancelled Sky and have 3 weeks to build a replacement  PVR!!

J

After everything is up, are you able to start the mysql and mythtv-backend services?

```
sudo service mysql start
sudo service mythtv-backend start
```

---

### Post by K9KungFu on 2012-06-21
I get prompted if I want to start the service after I close the backend config page, I click yes and enter my password, I don't receive any errors so assumed it had started.  I will try your suggestion tonight and report back!

---

### Post by K9KungFu on 2012-06-21
Hi,

No joy with that I'm afraid, it says the service is already running.

---

### Post by tgm4883 on 2012-06-21
> **K9KungFu said:**
> Hi,

No joy with that I'm afraid, it says the service is already running.

What IP address are you using in the frontend?

---

### Post by K9KungFu on 2012-06-21
The IP address for the backend.

---

### Post by K9KungFu on 2012-06-21
I tried to connect to the PC via a web browser on another PC and got the following:

!!NoTrans: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) [#2002]

Does this info help at all?

---

### Post by tgm4883 on 2012-06-21
Did you enable the MythTV service in the Mythbuntu Control Center?

---

### Post by K9KungFu on 2012-06-21
Yes it's enabled.  I have gone over all the settings and can't see where I've gone wrong!

---

### Post by steeldriver on 2012-06-21
to check if the backend is running:

```
service mythtv-backend status
```to check the backend ports

```
sudo netstat -lp |grep myth
```

---

### Post by K9KungFu on 2012-06-21
Start/runnIng process 2112.  

Hang on....it's working!  Unfortunately I can't see what I did!

However if I change the hostname in the database server settings under the frontend to the IP of the backend it stops working!?

---

### Post by tgm4883 on 2012-06-21
> **K9KungFu said:**
> Start/runnIng process 2112.  

Hang on....it's working!  Unfortunately I can't see what I did!

However if I change the hostname in the database server settings under the frontend to the IP of the backend it stops working!?

What are you changing it from?

---

### Post by K9KungFu on 2012-06-22
> **tgm4883 said:**
> What are you changing it from?

Localhost, does this have to be set as this because I am running the frontend and backend on the same PC?

I think I know what got the frontend connecting - I have a dual tuner and hadn't scanned for channels on the 2nd tuner!

---

### Post by tgm4883 on 2012-06-22
> **K9KungFu said:**
> Localhost, does this have to be set as this because I am running the frontend and backend on the same PC?

I think I know what got the frontend connecting - I have a dual tuner and hadn't scanned for channels on the 2nd tuner!

No, but if you want to use the external IP address you need to enable the MythTV service in the Mythbuntu Control Center (that allows external connections to MySQL), and put that external IP address in both mythtv-setup and the frontend. You may also need to restart the MySQL service.

---

### Post by K9KungFu on 2012-06-23
Hi,

I now have the frontend working via IP, I had changed the port number in the frontend settings!

Thank you very much for all your help, without you two I would still be digging through settings I didn't need!

Now all I have to do is get the rest configured!

Regards,
J

---

