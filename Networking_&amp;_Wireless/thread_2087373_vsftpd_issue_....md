---
title: "vsftpd issue ...???"
date: 2012-11-23
forum: Networking &amp; Wireless
---

### Post by adym3333 on 2012-11-23
1 .i am trying to set vsftpd ...... vsftpd service is running but not showing status through "netstat -a | grep vsftpd"

command "netstat -a" is working fine but when i enter above command it shows nothing ... output given below ......:(

...................................................................
root@Gateway:/# service vsftpd restart
vsftpd stop/waiting
vsftpd start/running, process 2063
root@Gateway:/# netstat -a | grep vsftpd
root@Gateway:/# netstat -a | grep vsftpd
root@Gateway:/# 
...................................................................
2. I am not able to access it through browser when i enter 127.0.0.1 as it happens in windows ,so is there any other way to access it or what ....:confused:. ???? i can access it through terminal ouput given below but not through browser ...
root@Gateway:/# ftp 127.0.0.1
Connected to 127.0.0.1.
220 Welcome to FTP service.
Name (127.0.0.1:root):

---

### Post by dmac1blah on 2012-11-23
> **adym3333 said:**
> 1 .i am trying to set vsftpd ...... vsftpd service is running but not showing status through "netstat -a | grep vsftpd"
 
command "netstat -a" is working fine but when i enter above command it shows nothing ... output given below ......:(
 
...................................................................
root@Gateway:/# service vsftpd restart
vsftpd stop/waiting
vsftpd start/running, process 2063
root@Gateway:/# netstat -a | grep vsftpd
root@Gateway:/# netstat -a | grep vsftpd
root@Gateway:/# 
...................................................................
2. I am not able to access it through browser when i enter 127.0.0.1 as it happens in windows ,so is there any other way to access it or what ....:confused:. ???? i can access it through terminal ouput given below but not through browser ...
root@Gateway:/# ftp 127.0.0.1
Connected to 127.0.0.1.
220 Welcome to FTP service.
Name (127.0.0.1:root):
 
 
While I have just started working with ftp servers I want something that is easy to use. I installed vsftpd but could not connect with it. I have not put alot of time into working with it do to other projects however while reseaching I cam accross PURE-FTPD [http://www.pureftpd.org/project/pure-ftpd/doc](http://www.pureftpd.org/project/pure-ftpd/doc) I installed it remotly using SSH still working with it might be worth trying

---

### Post by kalehrl on 2012-11-24
You can check if vsftpd is active with this command:
```
 ps aux | grep vsftpd
```
If it is, you will get output like this:
```
root       845  0.0  0.2   4688  1024 ?        Ss   Nov22   0:00 /usr/sbin/vsftpd
root     23455  0.0  0.1   4392   812 pts/0    S+   18:15   0:00 grep --color=auto vsftpd
```

---

### Post by adym3333 on 2012-11-25
> **kalehrl said:**
> You can check if vsftpd is active with this command:
```
 ps aux | grep vsftpd
```
If it is, you will get output like this:
```
root       845  0.0  0.2   4688  1024 ?        Ss   Nov22   0:00 /usr/sbin/vsftpd
root     23455  0.0  0.1   4392   812 pts/0    S+   18:15   0:00 grep --color=auto vsftpd
```

yes it works ..... !! thnks ..... :P

---

