---
title: "SSH when i press up i get  ' ^[[A ' rather then bash history"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by andey on 2011-01-10
i have a question, i just got a new ubuntu server 8.04 upgraded to 10.04 box. when i SSH into root@server it's the ssh im used to. However when i ssh into a different user that i created, it's slightly different. when i press "up" i get "^[[A" rather then the last bash command executed. also it doesn't keep my "current" directory in the cursor. And i get an error when using "screen". It's probably just a permissions thing, but i cant figure out where the problem is

---

### Post by PatchesTheCaveman on 2011-01-11
Did you locally login as the user once to create its home directory and whatnot?  You can do this easily with this command:
```
sudo su *<user>*
```

---

### Post by andey on 2011-01-11
```
andey@andey-labtop:~$ ssh root@###########
root@###########'s password: 
Linux localhost 2.6.32-27-generic-pae #49-Ubuntu SMP Thu Dec 2 00:07:52 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

0 packages can be updated.
0 updates are security updates.

Last login: Mon Jan 10 18:01:14 2011 from ###########
root@localhost:~# sudo su andey
$ ls
a2.sql.gz  andey_wz.sql
$ screen
Cannot open your terminal '/dev/pts/0' - please check.

```good idea, unfortunately that didn't do the trick

---

### Post by andey on 2011-01-11
A little IRC help from the #openssh channel

```

<andey> i have a question, i just got a new ubuntu server 8.04 upgraded to 10.04 box. when i SSH into root@server it's the ssh im used to. However when i ssh into a user i created, it's slightly diffrent. when i press "up" i get "^[[A" rather then the last bash command exucuted. also it doesn't keep my "current" directory in the cursor. And i get an error when using "screen". It's probably just a permissions thing, but i cant figure out what 
* nemysis (~nemysis@unaffiliated/nemysis) has joined #openssh
<DrLou> You are likely changing environment entirely when you ssh into that second user...  Have you looked at his .profile?
<DrLou> Also, it's quite different if you login interactive: As in # ssh - username
<DrLou> You may even be using a different shell, and/or different settings for it.
<ascheel> DrLou nailed it.  You're not using 'bash'
<DrLou> Nailed what? Mine, or andey's question...?
<ascheel> Andey's
<andey> okay so what should i do
<ascheel> andey: change your shell to bash in /etc/passwd
<andey> okay let me try that
<ascheel> it's probably /bin/sh
<ascheel> change it to /bin/bash
* variable has quit (Read error: Operation timed out)
<andey> BAMM! that worked
<andey> thanks a lot u guys!
<ascheel> I know.  :)
```

---

