---
title: "Problem installing Apache 2"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by nour_al_imen on 2010-09-16
Hi, 
I need help, please
I followed the steps below to install Apache 2 but when writing the last command line en error occured
here is the error 
> 
N@Nour-al-imen-laptop:~$ **/usr/local/apache2/bin/apachectl -k start**
httpd: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open log

here are the steps


> 
Download	$ lynx [http://httpd.apache.org/download.cgi](http://httpd.apache.org/download.cgi)
Extract	$ gzip -d httpd-NN.tar.gz
$ tar xvf httpd-NN.tar
$ cd httpd-NN
Configure	$ ./configure --prefix=PREFIX
Compile	$ make
Install	$ make install
Customize	$ vi PREFIX/conf/httpd.conf
Test	$ PREFIX/bin/apachectl -k start


Je am a beginner with Apache !!!
Please help me!
Thank you

---

### Post by kreggz on 2010-09-16
1. You normally need to run sudo to elevate privileges

e.g sudo /usr/local/apache2/bin/apachectl -k start

2. You can install Apache from apt-get or aptitude by doing

sudo aptitude install apache2

3. You might need to run sudo /etc/init.d/apache2 start

---

### Post by gordintoronto on 2010-09-16
When you are installing programs in Ubuntu, always try Synaptic or Software Center first. A couple of clicks, and I had Apache working.

---

### Post by nour_al_imen on 2010-09-29
Thank you for your help
I haven't find it in synaptic but I have used this command
sudo /usr/local/apache2/bin/apachectl -k start
 
I think it's installed but don't know how to start it.

---

### Post by gordintoronto on 2010-09-29
In Synaptic, use "search" not "quick search." When you install it through Synaptic, it starts automatically when you login.

---

### Post by nour_al_imen on 2010-10-28
Thank you gordintoronto for your help .
I resolved my problem by writing this command

su 
then entering my password 
My problem that I wasn't considered as a super user

---

### Post by gordintoronto on 2010-10-29
Running constantly as a super-user is dangerous, you get no warnings about potentially damaging commands. Sudo gives you super-user status for the duration of one command.

---

### Post by lisati on 2011-09-19
> **nour_al_imen said:**
> Thank you gordintoronto for your help .
I resolved my problem by writing this command

su 
then entering my password 
My problem that I wasn't considered as a super user

For the record: The preferred way of giving yourself "super user" privileges in Ubuntu is with the "sudo" command. More information can be found here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

