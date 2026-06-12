---
title: "tftpd Error code 2: Access violation [PLEASE][HELP]"
date: 2011-12-06
forum: Networking &amp; Wireless
---

### Post by mroussin51 on 2011-12-06
Hi, 

PLEASE HELP:confused:

I am getting tired of Error code 2: Access violation.

I am using tftp for an embedded linux project I am working on. I need to be able to use the put command from the client. I do not know how to set the server options needed to write files to the host. I think I need permissive and create options but I do not know how to set them. Not for lack of trying. I think I wore out xinetd due to excessive restarts. lol

I know...man page says... in.tftpd[options...] directory...

Do I append /etc/xinetd.d or simply use the command line?

Please give an example with correct syntax.

The directory I want to write to is 777 owner nobody.
 
Garbage in equals garbage out. I need help to take out the trash.

Thanks in advance,

Mike

ADDENDUM 1: I have now realized that on the host, I can simply create an empty file with appropriate file name and wr-wr-wr- and I can write over it from the client. This is a safer way to do it as well. That said, I am still interested in how to set the create and permissive bits to expand my knowledge of what I was doing so wrong...for so many hours. Thanks!

---

### Post by ego1 on 2011-12-06
I have spent several days trying to get an tftp service in my machine, but I can use "put" command, however I can't use "get" command.
Let me repeat all steps I made:

```
elder@elder-PC:~$ cat /etc/issue
Ubuntu 11.10 \n \l

elder@elder-PC:~$ sudo apt-get install tftp tftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  tftp tftpd
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/33.0 kB of archives.
After this operation, 168 kB of additional disk space will be used.
Selecting previously deselected package tftp.
(Reading database ... 178833 files and directories currently installed.)
Unpacking tftp (from .../tftp_0.17-18ubuntu2_amd64.deb) ...
Selecting previously deselected package tftpd.
Unpacking tftpd (from .../tftpd_0.17-18ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Setting up tftp (0.17-18ubuntu2) ...
Setting up tftpd (0.17-18ubuntu2) ...
Note: xinetd currently is not fully supported by update-inetd.
      Please consult /usr/share/doc/xinetd/README.Debian and itox(8).
elder@elder-PC:~$ sudo joe /etc/xinetd.d/tftp

service tftp
{
protocol        = udp
port            = 69
socket_type     = dgram
wait            = yes
user            = nobody
server          = /usr/sbin/in.tftpd
server_args     = -s /tftpboot
disable         = no
}

elder@elder-PC:~$ sudo mkdir /tftpboot
elder@elder-PC:~$ sudo chmod -R 777 /tftpboot
elder@elder-PC:~$ sudo chown -R nobody /tftpboot
elder@elder-PC:~$ sudo service xinetd reload
elder@elder-PC:~$ touch original
elder@elder-PC:~$ tftp localhost
tftp> put original
tftp> get original
Error code 2: Access violation
tftp> quit
elder@elder-PC:~$ less /var/log/syslog


Dec  6 16:02:09 elder-PC xinetd[13864]: Started working: 0 available services
Dec  6 16:06:29 elder-PC xinetd[13864]: Starting reconfiguration
Dec  6 16:06:29 elder-PC xinetd[13864]: Reading included configuration file: /etc/xinetd.d/chargen [file=/etc/xinetd.conf] [line=14]
Dec  6 16:06:29 elder-PC xinetd[13864]: Reading included configuration file: /etc/xinetd.d/daytime [file=/etc/xinetd.d/daytime] [line=28]
Dec  6 16:06:29 elder-PC xinetd[13864]: Reading included configuration file: /etc/xinetd.d/discard [file=/etc/xinetd.d/discard] [line=26]
Dec  6 16:06:29 elder-PC xinetd[13864]: Reading included configuration file: /etc/xinetd.d/echo [file=/etc/xinetd.d/echo] [line=25]
Dec  6 16:06:29 elder-PC xinetd[13864]: Reading included configuration file: /etc/xinetd.d/tftp [file=/etc/xinetd.d/tftp] [line=26]
Dec  6 16:06:29 elder-PC xinetd[13864]: Reading included configuration file: /etc/xinetd.d/time [file=/etc/xinetd.d/time] [line=11]
Dec  6 16:06:29 elder-PC xinetd[13864]: removing chargen
Dec  6 16:06:29 elder-PC xinetd[13864]: removing chargen
Dec  6 16:06:29 elder-PC xinetd[13864]: removing daytime
Dec  6 16:06:29 elder-PC xinetd[13864]: removing daytime
Dec  6 16:06:29 elder-PC xinetd[13864]: removing discard
Dec  6 16:06:29 elder-PC xinetd[13864]: removing discard
Dec  6 16:06:29 elder-PC xinetd[13864]: removing echo
Dec  6 16:06:29 elder-PC xinetd[13864]: removing echo
Dec  6 16:06:29 elder-PC xinetd[13864]: removing time
Dec  6 16:06:29 elder-PC xinetd[13864]: removing time
Dec  6 16:06:29 elder-PC xinetd[13864]: Swapping defaults
Dec  6 16:06:29 elder-PC xinetd[13864]: Reconfigured: new=1 old=0 dropped=0 (services)
Dec  6 16:08:16 elder-PC tftpd[13920]: tftpd: trying to get file: original
Dec  6 16:08:16 elder-PC tftpd[13920]: tftpd: serving file from /tftpboot
Dec  6 16:08:20 elder-PC tftpd[13922]: tftpd: trying to get file: original
Dec  6 16:08:20 elder-PC tftpd[13922]: tftpd: serving file from /tftpboot
```

---

### Post by ego1 on 2011-12-08
How there is no answer, I published a bug at

[https://bugs.launchpad.net/ubuntu/+source/netkit-tftp/+bug/901273](https://bugs.launchpad.net/ubuntu/+source/netkit-tftp/+bug/901273)

Please, if you have the same issue, report it there.

---

### Post by mroussin51 on 2011-12-08
Thanks for letting me know we are experiencing similar trouble.

FYI:

mike@ubuntu:/home/TFTP-shared$ ls -l test.txt
-rwxrwxrwx 1 nobody mike 86 2011-12-02 23:20 test.txt

mike@ubuntu:~$ tftp localhost
tftp> get test.txt
Received 87 bytes in 0.1 seconds
tftp> 

Next:

mike@ubuntu:~$ ls -l test1.txt
-rwxrwxrwx 1 nobody mike 67 2011-12-08 21:25 test1.txt

tftp> put /home/mike/test1.txt /home/TFTP-shared/test1.txt
Error code 2: Access violation

It appears we have the opposite problem. I can not put a file into my server root directory and you can not get. My initial instinct for yours is that the permissions on "original" are preventing you from reading it. In my case I need to set the create bit on my root directory. I don't know how to do that. If you set the create option please me know how.

 [http://ubuntuforums.org/showthread.php?p=11516876#post11516876](http://ubuntuforums.org/showthread.php?p=11516876#post11516876)

Other thoughts: I think this is not a bug. I read the man page and they did this intentionally to protect us from ourselves.

---

### Post by mroussin51 on 2011-12-09
Please:

mike@ubuntu:~$ in.tftpd -t
mike@ubuntu:~$ in.tftpd -V
mike@ubuntu:~$ in.tftpd -V
mike@ubuntu:~$ in.tftpd -l
mike@ubuntu:~$ in.tftpd -L
mike@ubuntu:~$ in.tftpd -a
mike@ubuntu:~$ in.tftpd -c
mike@ubuntu:~$ in.tftpd -u
mike@ubuntu:~$ in.tftpd -c /tftpboot

Dec  9 04:10:00 ubuntu tftpd[2174]: unknown option -?
Dec  9 04:10:28 ubuntu tftpd[2175]: unknown option -?
Dec  9 04:17:01 ubuntu CRON[2400]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  9 04:17:35 ubuntu tftpd[2402]: unknown option -?
Dec  9 04:17:46 ubuntu tftpd[2403]: unknown option -?
Dec  9 04:18:16 ubuntu tftpd[2404]: unknown option -?
Dec  9 04:18:34 ubuntu tftpd[2405]: unknown option -?
Dec  9 04:18:42 ubuntu tftpd[2406]: unknown option -?
Dec  9 04:18:51 ubuntu tftpd[2407]: unknown option -?
Dec  9 04:19:40 ubuntu tftpd[2408]: unknown option -?


Why doesn't my in.tftpd recognize any options?

Please:

mike@ubuntu:~$ in.tftpd -t
mike@ubuntu:~$ in.tftpd -V
mike@ubuntu:~$ in.tftpd -V
mike@ubuntu:~$ in.tftpd -l
mike@ubuntu:~$ in.tftpd -L
mike@ubuntu:~$ in.tftpd -a
mike@ubuntu:~$ in.tftpd -c
mike@ubuntu:~$ in.tftpd -u
mike@ubuntu:~$ in.tftpd -c /tftpboot

Dec 9 04:10:00 ubuntu tftpd[2174]: unknown option -?
Dec 9 04:10:28 ubuntu tftpd[2175]: unknown option -?
Dec 9 04:17:01 ubuntu CRON[2400]: (root) CMD ( cd / && run-parts --report /etc/cron.hourly)
Dec 9 04:17:35 ubuntu tftpd[2402]: unknown option -?
Dec 9 04:17:46 ubuntu tftpd[2403]: unknown option -?
Dec 9 04:18:16 ubuntu tftpd[2404]: unknown option -?
Dec 9 04:18:34 ubuntu tftpd[2405]: unknown option -?
Dec 9 04:18:42 ubuntu tftpd[2406]: unknown option -?
Dec 9 04:18:51 ubuntu tftpd[2407]: unknown option -?
Dec 9 04:19:40 ubuntu tftpd[2408]: unknown option -?


Why doesn't in.tftpd recognize any options?

I am looking for an option called solved to end this thread. I have realized that the ubuntu tftpd man page and the man tftpd return differt man pages and that is why none of the options worked. Please close this thread. Most forums offer a solved option to the user that generates the thread. I don't see that on this one.

:o:D:):(:popcorn::KS[COLOR="Red"]Solved[/COLOR]

[http://http://ubuntuforums.org/showthread.php?t=767621]("http://ubuntuforums.org/showthread.php?t=767621")

As soon as type Ubuntu Forums google auto filled: ubuntu forums how to mark thread as solved. Lots of people looking for the mythical solved option.

---

### Post by ego1 on 2011-12-09
tftp server is designed without security concern.
It must be able to write and read whatever the clients wants.
I am trying to use tftpd for almost a hundred voip phones.
Voip phones need to read and writes config files and log files.
Net admin don't have to be changed permissions very time that a phone write a new file. It will be crazy!
Please, suppport the bug open, clicking on "This bug affects you"

using this link 
[https://bugs.launchpad.net/ubuntu/+source/netkit-tftp/+bug/901273](https://bugs.launchpad.net/ubuntu/+source/netkit-tftp/+bug/901273)

---

### Post by drewski22785 on 2012-05-21
Solution or atleast a work around....

Not sure if this is something with the design of TFTP but when doing a put it does not let you create a file.

Solution:

Create the file before hand and give 777 rights. Run transfer again and it should work. See Below:


SW1#copy run tftp://192.168.31.1/SW1-Full-LAB26-TE.cfg
Address or name of remote host [192.168.31.1]? 
Destination filename [SW1-Full-LAB26-TE.cfg]? 
TFTP: error code 2 received - 16739

%Error opening tftp://192.168.31.1/SW1-Full-LAB26-TE.cfg (Permission denied)

root@ubuntu:/tftpboot# touch SW1-Full-LAB26-TE.cfg
root@ubuntu:/tftpboot# chmod 777 SW1-Full-LAB26-TE.cfg

SW1#copy run tftp://192.168.31.1/SW1-Full-LAB26-TE.cfg
Address or name of remote host [192.168.31.1]? 
Destination filename [SW1-Full-LAB26-TE.cfg]? 
!!
4456 bytes copied in 1.065 secs (4184 bytes/sec)
SW1#



I hope this helps!!!!!

---

