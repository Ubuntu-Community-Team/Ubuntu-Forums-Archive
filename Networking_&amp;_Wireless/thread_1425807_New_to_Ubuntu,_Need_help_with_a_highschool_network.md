---
title: "New to Ubuntu, Need help with a highschool network assignment"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by eyg12 on 2010-03-09
Hi my group recently got an in class school assignment for grade 12 computer class to make a basic client-server network with ubuntu to share a file with a few ubuntu 9.10 clients. We have ubuntu 9.10 server edition installed on one of the computers and I have installed the gnome GUI on it to make it easier for us to navigate around ubuntu because the OS is foreign to us right now. No one has any experience with ubuntu although i am becoming more familiar with the command line. We have tried many server making guides on the web but they have all failed. If anyone knows of a useful tutorial or can walk us though it that would be great. Please help quick ;)

For everyone's information:
- we have 1 9.10 server edition running the gnome GUI
- 5 clients running ubuntu desktop edition
- connected through a D-link DSS-16+ box

---

### Post by howlingmadhowie on 2010-03-09
do you have to write the software yourself to transfer the file? if not, ubuntu supports a number of file transfer protocols, for example:

ftp
sftp
nfs
smb
tftp

and quite a few others.

i'd recommend starting with ftp. try installing vsftpd and reading the documentation.

---

### Post by eyg12 on 2010-03-09
Yes we can use ftp, can you bring any insight on how to use it? We were trying to use samba for the longest time

---

### Post by howlingmadhowie on 2010-03-09
don't worry with samba. it's way too complicated.  it does lots of broadcasting and stuff and never really works right.

i'd recommend installing vsftpd on the server. you can do that be entering:
```

sudo apt-get install vsftpd

```
then you should read /etc/vsftpd.conf and change any configurations you don't like. then restart the service by typing:
```

sudo /etc/init.d/vsftpd restart

```
then you can find the ip address of the server (ifconfig) and on the clients click on places->connect to a server.  a window will open and you can fill in the relevant details.


that's the basic plan. configuration of the vsftp daemon is not quite trivial, but the configuration file is pretty well documented.

---

### Post by eyg12 on 2010-03-09
Alright, I have also been chatting with someone over IRC and we have figured out how to use the basics of SSH and we already have it working. If for some reason SSH is not useful in our application, I will certainly PM you back about FTP.

---

### Post by howlingmadhowie on 2010-03-09
you can use ssh as well, once you've installed the ssh server on your server, then you can log in over the same dialog window on the clients as you would use for ftp.  ssh is a lot safer than ftp as well.

---

