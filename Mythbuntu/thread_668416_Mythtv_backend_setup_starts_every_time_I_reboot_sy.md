---
title: "Mythtv backend setup starts every time I reboot system. How to stop it?"
date: 2008-01-15
forum: Mythbuntu
---

### Post by donjuan2001 on 2008-01-15
Hey guys, 
I installed mybuntu 7.10 and I can watch TV, schedule recording with my PVR-150. 

I install phpmyadmin using the following command: 

sudo apt-get install phpmyadmin

Again, every thing is working fine there phpmyadmin. 


Now, every time I reboot my PC, myth backend setup starts up first as if I was doing the initial setup.

I am new to linux and mythtv, so I am not sure where look. 

How do I stop this?

---

### Post by donjuan2001 on 2008-01-16
Any suggestions on how to stop this from happening?

---

### Post by volkswagner on 2008-01-16
In my experience this usually means a general setting is incorrect.  Most cases mysql password or location.

Make sure you can log into mysql with mythtv user and password.  On the backend with mysql installed setting localhost as location of mysql server, and all other machines point to the ip address of the mysql machine worked best for me.

Check password in etc/mythtv/mysql.txt.
You must be able to access mysql using this password.  

My guess is check in mythbunt-control-centre and see what is listed for mysql location in the masterbackend machine.

---

### Post by donjuan2001 on 2008-01-17
Thank you. I will double check my settings.

---

