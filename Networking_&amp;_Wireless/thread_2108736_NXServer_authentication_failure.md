---
title: "NXServer authentication failure"
date: 2013-01-25
forum: Networking &amp; Wireless
---

### Post by lz1dsb on 2013-01-25
I decided to start this thread so that maybe I'll save some hours of tinkering to others who use the NoMachine's NXServer. 
So there's the situation. NXServer uses the ssh port that your ubuntu box is configured to use. By default it is 22. What happens if you want to change it to something else. No problem. Just changing the config file /etc/ssh/sshd_config with Port <port_number>. Than you read the NXServer's manual that the same port should be configured in the configuration files:
/usr/NX/etc/server.cfg and /usr/NX/etc/node.cfg under SSHDPort = "<port_number>". 
After doing this configuration change we can reset both ssh and nx services
sudo service ssh restart
sudo /usr/NX/bin/nxserver --restart
And one could conclude that everything is in order now, just reconfigure the NX client and we're good to go. Wrong! Because this is what you're going to see in the syslog when you try to log in (the client will give a message Authentication Failure):
NXSERVER-3.5.0-11[17364]: Failed SSHd authentication for user 'username', to '127.0.0.1', port '22': ' ssh_exchange_identification: read: Transport endpoint is not connected#015\n' 'NXNssUserManager::auth'
So why the NXServer is using port 22 to authenticate to the sshd? Well, because there's a tiny additional config in the /usr/NX/etc/server.cfg file
SSHDAuthPort! So your should configure it to the same port! Unless off course you're not using a separate authentication server. Bug boy, I just lost good 3 hours figuring this out :lolflag:
Enjoy!

---

### Post by lz1dsb on 2013-01-28
I'll just mark this as solved...

---

