---
title: "Connect to mythbackend via crossover cable"
date: 2008-01-05
forum: Mythbuntu
---

### Post by teet on 2008-01-05
My mythbackend machine accesses the internet via a wireless card.  I acquired an old P4 with 224 mb of RAM that I would like to use as a second frontend machine.  I would like to connect the two machines directly  together via a crossover cable (I don't have a router).  I don't need internet on the secondary frontend.

I was able to get the 2 machines "networked" by assigning a static IP address to the card in my primary machine as follows:
IP address:  192.168.2.7
Gateway:  192.168.2.100

On the secondary frontend, I assigned a static IP address as follows:
IP address:  192.168.2.8
Gateway:  192.168.2.7

I could ssh into my main machine from the secondary frontend and I could access mythweb from the secondary fronted, so I am pretty sure the 2 machines were "networked" properly.

Now, I tried to configure mysql/mythtv to let the frontend connect.  I changed the IP address of the master backend to 192.168.2.7 (instead of localhost) in the frontend and backend settings (and manually in ~/.mythtv/mysql.txt and /etc/mythtv/mysql.txt).  I also commented out the bind-address line in /etc/mysql/my.cnf.  I rebooted both machines, but after the reboot, mythbackend on the primary machine wouldn't connect to the mysql database properly.  When I changed all the IP address information back to 'localhost' everything worked again...but to be able to access the database from the secondary backend, I need to set a real IP address on the master backend.

What am I missing?

Note: I use the 'root' account to access the mysql database instead of the default 'mythtv' account.

-teet

---

