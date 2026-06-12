---
title: "Mythbuntu 14.04.1 Apache not starting up"
date: 2014-08-15
forum: Mythbuntu
---

### Post by flecki on 2014-08-15
After upgrading from 12.04 to 14.04.1 i noticed mythweb not working - first i thought it is the issue that is already described in here but i checked the config files and everything was fine for Apache 2.4

It seems that Apache did not start up but when i used: sudo /etc/init.d/apache2 restart it satrted and brought up this message:

* Restarting web server apache2        AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
 
Afterwards i had mythweb back - since i am a complete noob to linux i would like to ask if someone can point me to the files that need editing to start Apache automatically like it did in 12.04 or provide a hint why it did not come up at start.

---

### Post by wyliecoyoteuk on 2014-08-15
I have that message as well, but it does not stop Apache running, it is only a warning.

You can eliminate it with these 2 lines of code in a terminal:

echo "ServerName localhost" | sudo tee /etc/apache2/conf-available/fqdn.conf
 sudo ln -s /etc/apache2/conf-available/fqdn.conf /etc/apache2/conf-enabled/fqdn.conf

---

### Post by flecki on 2014-08-15
Well it is not actually the error line that bothers me as mythweb runs anyway after i manually start apache - more the fact that apache seems not to start automatically at startup.

Any idea where i can correct that ?

---

### Post by wyliecoyoteuk on 2014-08-16
[http://ubuntuguide.net/how-to-manage-startupboot-up-services-in-ubuntu](http://ubuntuguide.net/how-to-manage-startupboot-up-services-in-ubuntu)

---

### Post by flecki on 2014-08-16
It´s Solved - once i had activated it manually it started up with every system start....

---

