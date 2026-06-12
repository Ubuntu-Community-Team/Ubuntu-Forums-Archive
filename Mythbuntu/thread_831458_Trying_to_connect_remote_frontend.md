---
title: "Trying to connect remote frontend"
date: 2008-06-16
forum: Mythbuntu
---

### Post by The Odometer on 2008-06-16
I have a combined backend/frontend that is working beautifully. However, I'm trying to connect a remote frontend to my system. I was initally able to ping and get a response via mysql--but after following these directions-- [http://ubuntuforums.org/showthread.php?t=799956&highlight=frontend+cannot+connect]("http://ubuntuforums.org/showthread.php?t=799956&highlight=frontend+cannot+connect&page=2") Now-I can't even get a ping back. I was getting a ping earlier--and then I lost it. The part I specifically followed was the following: 
```
mysql -u root -p

grant all privileges on mythconverg.* to 'mythtv'@'%' identified by 'password';
flush privileges;
```

After doing that--I couldn't get a ping. I later figured out that uncommenting a line in the mysql.cnf was probably my problem--but I can't get everything else fixed. Please help! I was getting a ping earlier--but I couldn't connect with my backend's database.

---

### Post by uopjohnson on 2008-06-21
Are you using mythbuntu-control-center to get these systems setup?  That will certainly save you some time and configuration.
The mysql commands you did above are not causing any problems with your network connection they just allow access to your mythconverg database from anywhere. 

Run ifconfig eth0 on both machines and post back the results.  Also try pinging the frontend from the working backend to see if the block goes both ways.

---

