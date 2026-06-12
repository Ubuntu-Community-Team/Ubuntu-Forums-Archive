---
title: "can't install mythexport: unknown hostname '-umythtv'"
date: 2010-02-16
forum: Mythbuntu
---

### Post by fauna5 on 2010-02-16
Hi, 

I hope you can help or point me to the correct mailing list. 

I upgraded from mythbuntu jaunty to 9.10 Karmic the other day. When I did the upgrade mythexport errored. I now cant install or reconfigure mythexport. The error message is: ERROR 2005 (HY000): Unknown MySQL server host '-umythtv' (1)

now my hostname variable is set and i can ping that IP. I can also connect to the mysql host using the -h mythbox option.

I've only seen the error on this page [http://ubuntuforums.org/showthread.php?t=1087955&page=17](http://ubuntuforums.org/showthread.php?t=1087955&page=17) - but no solutions.

logs below

Thanks,

Richard


mythbox@mythbox:/tmp$ sudo dpkg -i mythexport_2.1.3-0ubuntu1_i386.deb 
Selecting previously deselected package mythexport.
(Reading database ... 218434 files and directories currently installed.)
Preparing to replace mythexport 2.1.3-0ubuntu1 (using mythexport_2.1.3-0ubuntu1_i386.deb) ...
Unpacking replacement mythexport ...
Setting up mythexport (2.1.3-0ubuntu1) ...
ERROR 2005 (HY000): Unknown MySQL server host '-umythtv' (1)
dpkg: error processing mythexport (--install):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Errors were encountered while processing:
 mythexport
mythbox@mythbox:/tmp$ hostname
mythbox
mythbox@mythbox:/tmp$ ping `hostname`
PING mythbox (127.0.1.1) 56(84) bytes of data.
64 bytes from mythbox (127.0.1.1): icmp_seq=1 ttl=64 time=0.081 ms
64 bytes from mythbox (127.0.1.1): icmp_seq=2 ttl=64 time=0.098 ms
^C
--- mythbox ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.081/0.089/0.098/0.012 ms
mythbox@mythbox:/tmp$ mysql -u mythtv -ph50DPloU -h mythbox
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 3523
Server version: 5.1.37-1ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>

---

### Post by fauna5 on 2010-02-16
ok, 

so I fixed it myself after poking around a few config files. Seems that /etc/mythtv/mysql.txt didnt have a DBHostName attribute in it. Added this and the install went fine. Not sure why it didnt have this info in it in the first place. This box was a plain install of 9.04 before the upgrade.

Rich

> **fauna5 said:**
> Hi, 

I hope you can help or point me to the correct mailing list. 

I upgraded from mythbuntu jaunty to 9.10 Karmic the other day. When I did the upgrade mythexport errored. I now cant install or reconfigure mythexport. The error message is: ERROR 2005 (HY000): Unknown MySQL server host '-umythtv' (1)

now my hostname variable is set and i can ping that IP. I can also connect to the mysql host using the -h mythbox option.

I've only seen the error on this page [http://ubuntuforums.org/showthread.php?t=1087955&page=17](http://ubuntuforums.org/showthread.php?t=1087955&page=17) - but no solutions.

logs below

Thanks,

Richard


mythbox@mythbox:/tmp$ sudo dpkg -i mythexport_2.1.3-0ubuntu1_i386.deb 
Selecting previously deselected package mythexport.
(Reading database ... 218434 files and directories currently installed.)
Preparing to replace mythexport 2.1.3-0ubuntu1 (using mythexport_2.1.3-0ubuntu1_i386.deb) ...
Unpacking replacement mythexport ...
Setting up mythexport (2.1.3-0ubuntu1) ...
ERROR 2005 (HY000): Unknown MySQL server host '-umythtv' (1)
dpkg: error processing mythexport (--install):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Errors were encountered while processing:
 mythexport
mythbox@mythbox:/tmp$ hostname
mythbox
mythbox@mythbox:/tmp$ ping `hostname`
PING mythbox (127.0.1.1) 56(84) bytes of data.
64 bytes from mythbox (127.0.1.1): icmp_seq=1 ttl=64 time=0.081 ms
64 bytes from mythbox (127.0.1.1): icmp_seq=2 ttl=64 time=0.098 ms
^C
--- mythbox ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.081/0.089/0.098/0.012 ms
mythbox@mythbox:/tmp$ mysql -u mythtv -ph50DPloU -h mythbox
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 3523
Server version: 5.1.37-1ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>

---

