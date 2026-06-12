---
title: "Likewise Join Domain and port memberships from AD"
date: 2010-05-17
forum: Networking &amp; Wireless
---

### Post by rich33716 on 2010-05-17
in searching i never found an article that got it just right. so here it is tried and true..

1. I usually start out assigning myself a static ip address. this is not needed to join but its something I always do.

2. next i set my dns settings in resolve.conf to my local dns server

3. download likewise "apt-get install likewise-open"

4. for kerberos i just leave it blank

5. go to your nsswitch.conf file located in /etc/ and set the hosts to only files and dns

6. now you should stop your networking and start it again so that the dns changes take effect.

7. you are now ready to try and join your domain. "domainjoin-cli join fqdn.of.yourdomain administrator"  you can substitute administrator with any admin account


you should now be joined to your domain


for adding sudo rights to the "administrator" membership

1. open your sudoers file located in /etc/
2. the following line to the bottom of the file
"%DOMAIN\\administrators ALL=(ALL) ALL"

replace DOMAIN with your domain name. do not use your fqdn. all set. hope you enjoy

---

### Post by K.Mandla on 2010-05-20
Moved to Networking and Wireless.

---

### Post by LebLinux on 2010-05-20
Thanks it works!

---

