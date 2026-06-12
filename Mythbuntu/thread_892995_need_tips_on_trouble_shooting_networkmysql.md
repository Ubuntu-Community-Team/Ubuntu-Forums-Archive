---
title: "need tips on trouble shooting network/mysql"
date: 2008-08-17
forum: Mythbuntu
---

### Post by il-luzhin on 2008-08-17
I've had a mythtv machine (see sig for stats) for a while and now I want to make a frontend on a second pc (compaq presario 5320CA w/ ATI Radeon 9250)

Though my connection fields are correct, it will not connect to mysql database.  Unlike most ubuntu/linux products I've had trouble finding help.  Can anyone suggest a source to trouble shoot this particular problem?

Thnx folks

---

### Post by nasha on 2008-08-17
When you say it will not connect... What errors are you experiencing? Do you have network level connectivity?

---

### Post by il-luzhin on 2008-08-17
thanks for replying nasha, but it seems I've since made a royal mess of things.

It seemed as though I had to make a new mysql user; same user name, but different location, so I did that.  Success, but now the primary front/backend won't connect.  

I'm going to try re-adding my former mysql user but I'm not optimistic.  I've been trying to restore formerly working sysyem but current error reads 'cannot connect to port 6543 on 127.0.0.1'

How can that be!...ugh

---

### Post by il-luzhin on 2008-08-17
okay, I obviously have a completely different issue than I originally thought.  I guess I'm going to have to get more familiar with mySQL.

I'm not going to mark this thread as solved just in case some good soul wants to offer me some help.

thnx guys

---

### Post by uncle hammy on 2008-08-18
on your backend, run

sudo dpkg-reconfigure mythtv-database
sudo dpkg-reconfigure mythtv-common

this will allow you to set you root user password, and the user/pass (should just be mythtv) of the user that will access the mythconverg database.  It will also allow you to specify if you will have other mythtv computers that will need to access your backend, make sure you say YES.  This will add the proper permission entry in MySQL for the mythtv user from other loactions on the network.

After this is done, make sure your connections are set to the proper IP of your backend, with the mythtv username and the password you setup in the above steps.

Just in case, reconfigure mythtv-common executes this command (I am assuming) in MySQL to allow the network access

GRANT ALL ON mythvconverg.* TO mythtv@'%' IDENTIFIED BY 'THE_PASSWORD_YOU_SELECTED';

FLUSH PRIVILEGES;

Hope that helps,
Scott

---

