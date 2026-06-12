---
title: "scp issue"
date: 2013-06-02
forum: Networking &amp; Wireless
---

### Post by Apagon on 2013-06-02
I install (ubuntu 12.1 - 3.5.0-30-generic):
    on pc FW, (user=fireman,ip=172.16.0.1), openssh-server
    on pc Doyle, (user=doyle,ip=172.16.0.2), openssh-client

On Doyle, I generate keys, and transfer public key to FW. I ssh FW from Doyle, no problemo, so far so good. Once in A, I try to scp a text file (from FW to Doyle), but have the following error:

ssh:connect to host 172.16.0.2 port 22: connection refused
lost connection

On FW (during ssh session), I tried:
scp file.txt doyle@172.16.0.2:/~
scp file.txt [EMAIL="doyle@172.16.0.2:/home/doyle/file.txt"]doyle@172.16.0.2:/home/doyle/file.txt[/EMAIL]
scp [EMAIL="fireman@172.16.0.1:/home/fireman/file.txt"]fireman@172.16.0.1:/home/fireman/file.txt[/EMAIL] doyle@172.16.0.2:/~
scp [EMAIL="fireman@172.16.0.1:/home/fireman/file.txt"]fireman@172.16.0.1:/home/fireman/file.txt[/EMAIL] doyle@172.16.0.2:/home/doyle/

On pc Doyle,
doyle@Doyle:~$ ps -A | grep ssh
 1744 ?        00:00:00 ssh-agent
 4098 pts/0    00:00:00 ssh
(top | grep ssh gives nothing)

and

netstat -nav | grep 172.16.0.1
tcp 0 0    172.16.0.1:22    ESTABLISHED

On pc FW,
fireman@FW:~$ ps -A | grep ssh
2154 ? 00:00:00 sshd
2157 ? 00:00:00 sshd
2172 ? 00:00:00 sshd
(top | grep ssh gives nothing)
notice: when no ssh connection, I have got only 1 line here.

and

netstat -nav | grep 22
tcp     0    0    0.0.0.0:22    0.0.0:*          LISTEN
tcp    0    0    172.16.0.1:22    172.16.0.2:35166  ESTABLISHED
tcp6    0    0    0 :::22        :::*          LISTEN

BTW (although it's not the pb I am concerned with), we have on FW:
dpkg -l | grep ssh
output
rc openssh-client    ..... (I have never installed openssh-client on FW)
rc openssh-server    .....

(if I do apt-get remove openssh-client on A, then, no way to ssh from B to A anymore)

Among others, I have gone through these links :
[https://launchpad.net/ubuntu/quantal/+package/openssh-client](https://launchpad.net/ubuntu/quantal/+package/openssh-client) -> no answer
[https://help.ubuntu.com/12.10/serverguide/openssh-server.html](https://help.ubuntu.com/12.10/serverguide/openssh-server.html) -> no answer
[http://ubuntuforums.org/showthread.php?t=1914246](http://ubuntuforums.org/showthread.php?t=1914246) (same issue solved by reinstalling everything).

I remove everything on A:
sudo apt-get remove openssh-server openssh-client
and B:
sudo apt-get remove openssh-client

and reinstall
on B:
sudo apt-get install openssh-client
and A:
sudo apt-get install openssh-server
I generated news keys, copy .pub to FW, ssh again ....

The problem persists. I don't know what to do. Any idea would be more than welcome!

---

### Post by Cheesemill on 2013-06-02
If you don't have openssh-server installed on Doyle than how can you expect to ssh to it?

From Doyle the following should work...
```
scp fireman@172.16.0.1:/home/fireman/file.txt /home/doyle/
```

This command that you tried earlier from FW...
```
scp file.txt doyle@172.16.0.2:/home/doyle/file.txt
```
would have worked if you had openssh-server installed on Doyle.

---

### Post by Apagon on 2013-06-02
Thank you Cheesemill; 
I thought the client could use the existing connection with the server to run scp command. 
simply doing from Doyle "scp [email]fireman@172.16.0.1:~/file.txt[/email] ~/" works. 
Thanks again.

---

