---
title: "problem with SSH"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by Shamma009 on 2010-09-29
hello there 


So, I am using ubuntu to program my robot nao, I want to copy some files  to the robot, and I should use a secure connection SSH. However, I  looked over the net for ways to do it and I did, 
this was the command 
scp filename nao@ipaddress:/filedirectory 

but it gives me this message 
'Permission denied', 


any ideas ?


thanks

---

### Post by BkkBonanza on 2010-09-29
The user nao has to have write permissions on the target directory. 
If not then you would get that message. 

Typically nao would have write permission on it's home directory so you may need to copy it there and then locally use sudo to copy to a privileged directory.

---

### Post by Shamma009 on 2010-09-29
I did whatr you said and it is copied now, but how can I do that ? -->


then locally use sudo to copy to a privileged directory.


thanks

---

### Post by BkkBonanza on 2010-09-29
You can login with ssh and then use sudo to gain root rights for copying.

I'm assuming Ubuntu on robot too. But if not then you may be able to just login as root. Some other linuxes don't disable root login. 

(If you can login as root then you could also do scp as root without problems - so I'm guessing you can't login as root.)

eg. 

ssh nao@ipaddress
(get logged in)

sudo cp myfile /filedirectory
(sudo will ask for pwd again)

---

### Post by Shamma009 on 2010-10-03
it gives me this command


-bash: sudo: command not foun ???

this was my command 

nao@nao [127] [~]$ sudo cp libbrowneyes.so /opt/naoqi/lib


thank you again

---

### Post by BkkBonanza on 2010-10-03
Hmmm. On Ubuntu sudo would be installed by default. I'm guessing the robot doesn't have a regular Ubuntu install then. If not, then your only alternative is to login as "root", but you'll need the password for that. Then you can copy the file without sudo,

cp libbrowneyes.so /opt/naoqi/lib

but you'll need to be in the home directory for nao or use,

cp /home/nao/libbrowneyes.so /opt/naoqi/lib

---

### Post by BkkBonanza on 2010-10-03
Msg duplicated. Deleted.

---

### Post by Shamma009 on 2010-10-03
It is working now :) 

Many thanks, appreciate it :guitar:

---

