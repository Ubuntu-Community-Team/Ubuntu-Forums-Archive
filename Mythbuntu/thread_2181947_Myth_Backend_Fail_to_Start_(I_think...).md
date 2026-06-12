---
title: "Myth Backend Fail to Start (I think...)"
date: 2013-10-19
forum: Mythbuntu
---

### Post by bavid on 2013-10-19
I'm trying to install MythTV 0.27 on Xubuntu 12.04. This is not exactly the same as Mythbuntu, but should be close... right?

Everything went smoothly until I closed Myth Setup and it tried to start the backend. It prompted me for my password several times, even though I entered it correctly. Bailing out and trying "sudo start mythtv-backend" reports that the backend started correctly, but I don't see it in the process list. Further investigation of the log files looks like it quit soon after starting. (Link to full logs below).

```

Oct 19 14:28:22 Old-macbook-pro kernel: [   59.624269] init: mythtv-backend main process ended, respawning
Oct 19 14:28:22 Old-macbook-pro kernel: [   59.817266] init: mythtv-backend main process (2131) terminated with status 130
Oct 19 14:28:22 Old-macbook-pro kernel: [   59.817302] init: mythtv-backend respawning too fast, stopped

```

The MythTV log makes it look it failed to connect to the database:

```

Oct 19 14:16:42 Old-macbook-pro mythbackend: mythbackend[26188]: E CoreContext mythdbcon.cpp:216 (OpenDatabase) Unable to connect to database!
Oct 19 14:16:42 Old-macbook-pro mythbackend: mythbackend[26188]: E CoreContext mythdbcon.cpp:217 (OpenDatabase) Driver error was [1/1045]:#012QMYSQL: Unable to connect#012Database error was:#012Access denied for user 'mythtv'@'localhost' (using password: YES)

```

However, I can successfully connect from the mysql client ("mysql -u mythtv -p" using default password "mythtv"), mythtv-setup does't complain about database problems, and mysqlfilldatabase runs successfully.

Can anyone help?

Logs are at: [http://pastebin.com/f0iKkJ8s](http://pastebin.com/f0iKkJ8s)

(And I'm not using the Mythbuntu distro itself because my hardware will only boot from the live CD for 10.04 server. I need to start from that, upgrade to 12.04 server and then add the Xubuntu and mythtv packages)

---

### Post by itlarson2 on 2013-10-20
Sounds similar to a problem I had a few days ago.  I was getting the language selection/setup screen from the front-end and there were messages about not being able to connect to the database in the logs. when I checked if the back-end was running, it wasn't:

itl@itlmyth:~$ sudo service mythtv-backend status
mythtv-backend stop/waiting

restarting it didn't work:

itl@itlmyth:~$ sudo service mythtv-backend start
mythtv-backend start/running, process 3704
itl@itlmyth:~$ sudo service mythtv-backend status
mythtv-backend stop/waiting

The database was running:

itl@itlmyth:~$ sudo service mysql status
mysql start/running, process 3342

  

The solution was to reset the password for mythtv to match the one showing in the front-end setup screen:

itl@itlmyth:~$ mysql -u root -h localhost -p
Enter password:
mysql>SET PASSWORD FOR 'mythtv'@'localhost' = PASSWORD('xxxxxxx');
mysql> FLUSH PRIVILEGES;
mysql>quit

The password mysql wants is it's root password- this was the same as my linux user password.  I think that's a default mythbuntu setting, and not something I did, but I'm not 100% sure. 

I don't know why this password changed- the one showing in the front-end was the same as it had always been, and the system hadn't even been restarted.

---

### Post by bavid on 2013-10-20
For me, completely removing mythbackend and MySQL did the trick. Upon reinstallation, I found that the database password in MythWeb was a random, auto-generated string; NOT what I had set for the myth user in MySQL. So maybe it was screwed up in mythbackend too, but there's no way to tell now.

---

