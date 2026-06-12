---
title: "Problem with webserver please help."
date: 2010-03-27
forum: Networking &amp; Wireless
---

### Post by jmr423 on 2010-03-27
Hey, so I just finished setting up a Ubuntu server with  lamp/proftpd/phpbb3/openssh and everything works 100% in my local  network.

I have a dynamic ip address and my isp blocks ports 21.25.80.110.6667.135-139.443.445.1433.1434. 

I am trying to put my website online. So i went into  the  /etc/apache2/ports.conf and changed both the listen port and the  virtualhost to 81 and the ssl port to 450.  i also change it from port 80 to 81 in  /etc/apache2/sites-enabled/000-default

I restarted apache.

I then tried accessing my  site through my internal ip and i am able to access is through both  ports 80 and 81. (the ssl port 450 doesnt work but i do not care about  that atm). I then  followed this guide.

[http://portforward.com/english/route...567/Apache.htm]("http://portforward.com/english/routers/port_forwarding/Siemens/Gigaset-SE567/Apache.htm")

to forward port 81 and port 450 and then went to my external  ipaddress:81 and it does not connect.

What am i doing wrong?                                                                                                                                    *                                              [Last  edited by jmr423]("http://ubuntuforums.org/posthistory.php?p=9034562"); 1 Minute Ago at 04:10 AM*

---

### Post by Iowan on 2010-03-27
Are you accessing from outside your network? Some routers won't let you specify the external address port from inside the network - to keep someone from spoofing an internal address from outside the network.

---

### Post by jmr423 on 2010-03-28
solved it

i had to changed the virtual hosts to blank, listening port to 81,download the no-ip.com ubuntu client, forward my router to port 81 and forward the no-ip domain to myip:81


Note i still can not connect to my server through my external ip or domain name in my home network i have to go to a diferent network and connect.

---

### Post by Iowan on 2010-03-29
From inside your network, you should be able to use the server's internal IP address.

---

