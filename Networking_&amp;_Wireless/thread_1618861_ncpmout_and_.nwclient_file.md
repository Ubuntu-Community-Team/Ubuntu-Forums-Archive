---
title: "ncpmout and .nwclient file"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by skyde77 on 2010-11-11
Hello,

I have managed to mount Netware servers with the ncpmount command but I have hit a small problem when I try to use .nwclient file for the passwords.

When I run this command everything works fine although it will ask my password.

~$ sudo ncpmount -m -S SERVER -V VOLUME -U Username -u uid -g gid -f 600 -d 700 -y utf8 -p cp850 -A ip_adress_here  TEST/
Logging into SERVER as USERNAME
Password:

Since I run a script which mounts multiple server/volumes it will ask my password for all of them. From what I understand in order to eliminate the asking of password I should create a .nwclient file into the /root/ -directory (since I am sudo'ing) and just put 

SERVER/USERNAME password 

there. However when I run the script it asks for the password again. I then tried to remove -S Server and -U Username and even -u uid parts of the commands but then I get 

ncpmount: Unknown user (0x89FC) in find_conn_spec

What am I doing wrong? (the rights of .nwclient file are set to 0600)

Best regards,
skyde

---

