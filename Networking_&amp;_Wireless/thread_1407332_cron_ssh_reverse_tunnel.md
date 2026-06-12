---
title: "cron ssh reverse tunnel"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by amanik on 2010-02-15
Hi,

I am trying to access my work PC (Ubuntu 9.04) from home. I do not have control over the router/firewall at work. I am able to establish a reverse ssh tunnel from my work pc to my home PC while i am at work and then use this connection to vnc from home. however i am not able to run the ssh command thru cron so that the ssh tunnel can be created automatically. I have searched the net and tried the solutions provided but they dont seem to work. the ssh command executes thru terminal but does not work thru cron. after some debugging i am getting the error "Host key verification failed"

can somebody please help me

Thanks in advance

---

### Post by mobilediesel on 2010-02-15
> **amanik said:**
> Hi,

I am trying to access my work PC (Ubuntu 9.04) from home. I do not have control over the router/firewall at work. I am able to establish a reverse ssh tunnel from my work pc to my home PC while i am at work and then use this connection to vnc from home. however i am not able to run the ssh command thru cron so that the ssh tunnel can be created automatically. I have searched the net and tried the solutions provided but they dont seem to work. the ssh command executes thru terminal but does not work thru cron. after some debugging i am getting the error "Host key verification failed"

can somebody please help me

Thanks in advance

If you truly need to access your work computer, your immediate supervisor would be the one to ask. If you're accessing company resources from outside the company without company permission, you're just asking to be fired.

---

### Post by roskiy on 2010-02-15
config SSH with [StrictHostKeyChecking=no] option. usually it's in /etc/ssh
however this maay make your PC vulnerble.

---

### Post by amanik on 2010-02-15
Hi,

Thanks tried that the error has stopped coming however ssh tunnel is not forming below is my crontab entry

> */1 * * * * /usr/bin/ssh -i /home/USERNAME/.ssh/id_rsa USERNAME@URL >> /home/USERNAME/ssh.log 2>&1

appreciate your help

thanks

---

