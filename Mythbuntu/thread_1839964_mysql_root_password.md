---
title: "mysql root password"
date: 2011-09-06
forum: Mythbuntu
---

### Post by wisenuts on 2011-09-06
hey what is the default root password for mysql in mythbuntu?

I just installed 11.04 and need to allow for remote connections? Is this something I can do via a menu or do I need to edit the database directly?

I tried

mysql -u root
and I get
Access denied for user 'root@localhost' (using password:NO)

thanks in advance for your help!

---

### Post by leejc on 2011-09-06
IIRC, the default config allows the operating system user 'root' to connect by default. Try

```

sudo mysql -u root

```

---

### Post by wisenuts on 2011-09-06
same thing 

ERROR 1045 (28000) Access denied etc etc

---

### Post by wisenuts on 2011-09-06
I've also set the root passwd

sudo passwd root

then

su

then as root ran

mysql -u root

still nothing. Seems like i'm missing something basic.

---

### Post by toorima on 2011-09-06
you'll find the mysql credentials in /etc/mythtv/mysql.txt

---

### Post by wisenuts on 2011-09-06
is this the root user password or just mythtv?

So i've got

DBUserName=mythtv
DBPassword=s3creT
DBName=mythconverg
DBType=QMYSQL3

---

### Post by toorima on 2011-09-06
If you want to connect other frontends to your backend mysql server then yes those are the credentials you want. 

If you really are after the root account I'm not sure if ubuntu has one by default, the root password you set earlier was for the root shell account, not mysql root user.

---

### Post by wisenuts on 2011-09-07
I understand the root shell password. Here is the crux of my problem. When I try to connect mythbox via xbmc using the credential in /etc/mythtv/config.xml

I get this
connection to mythtv host 127.0.0.1 failed

I think this has to do with my backend not accepting remote connections. I just don't know how to troubleshoot this.  

I've tried this on two windows computer running xbmc v10 and 1 linux box running v10 all throw the same error back at me.  

Thanks in advance again here.

If I could just get into the database I could prove this.....

---

### Post by toorima on 2011-09-07
The clients must connect to the IP of your mythtv backend server, not 127.0.0.1, and you must also configure your backend server to allow remote connections, you can configure that in the mythtv backend setup

---

### Post by wisenuts on 2011-09-07
where in myth backend setup?

I've gained root access and i've updated /etc/mysql/my.conf
bind-address my.ip.address

restarted and I get access denied for user

I am using the ip address and not 127.0.0.1

---

### Post by toorima on 2011-09-07
Think its under general settings, the IP there has to be the IP of the backend, not 127.0.0.1 and I think there at least used to be a check box to allow remote connections. Can't shutdown my backend now to look.

Try and connect to the backend server from the linux box, if you have a mysql client installed on it you can try

mysql -h BACKEND_SERVER_IP -u mythtv -p

or if you don't have a mysql client install you can use telnet

telnet BACKEND_SERVER_IP 3306

---

### Post by wisenuts on 2011-09-07
well i'm pretty sure i borked it :)

Going to try a new install and not use mythbuntu. haven't had much success with it anywho.

11.06 x64 here i come. shouldn't take me too long. I'll post back with good news.  hopefully.....

---

### Post by Singlebbl on 2011-09-07
The way to invoke mysql is by using the -p parm so it asks you for your password just like when you use "sudo".    
```

seth@Landon:~$ mysql -u root -p mythconverg 
Enter password: 
Reading table information for completion of table and column names 
You can turn off this feature to get a quicker startup with -A
Welcome to the MySQL monitor.  Commands end with ; or \g. 
Your MySQL connection id is 304 
Server version: 5.1.41-3ubuntu12.10 (Ubuntu)
Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

---

### Post by uncle hammy on 2011-09-08
With Mythbuntu 10.04 and on, the installer sets the MySQL root password to the same password you entered for your user account.

---

### Post by wisenuts on 2011-09-08
woot! got it all working on 11.04 x64. Now, the sad thing is that there is no live tv support for mythbox. Anyway to make this work with xbmc v10 and mythtv v.24?

---

