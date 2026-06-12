---
title: "tftpd-hpa Problem"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by Asterix99 on 2009-06-14
Hello,
 I've installed tftpd-hpa server on my Kubuntu 9.04 x86_64 (IP: 192.168.178.27).
 The tftpd daemon is running successfully.
```

user@kiste:~$ ps -ef | grep tftpd
root      3732     1  0 15:12 ?        00:00:00 /usr/sbin/in.tftpd -l -s /var/lib/tftpboot
user     15403 12958  0 22:34 pts/2    00:00:00 grep tftpd

```I have the directory /var/lib/tftpboot/ 
```

user@kiste:~$ ll /var/lib/tftpboot/
insgesamt 2064
drwxrwxrwx  2 nobody root      4096 2009-06-05 22:29 .
drwxr-xr-x 61 root   root      4096 2009-06-05 17:49 ..
-rwxrwxrwx  1 nobody root   2097152 2009-06-01 18:49 initrd.gz
-rw-r--r--  1 user   user        27 2009-06-05 22:29 test.txt

```My local tftp client is working
```

user@kiste:~$ tftp 192.168.178.27
tftp> get
(files) test.txt
Received 30 bytes in 0.0 seconds
tftp> get
(files) initrd.gz
Received 2109827 bytes in 0.1 seconds
tftp>

```but with an tftp client on another pc in my lan tftp isn't working.
I allways get a time out. Ping is ok.

Nmap says port is filtered ???
```

user@kiste:~$ sudo nmap -sU -sT -p69 192.168.178.27

Starting Nmap 4.76 ( http://nmap.org ) at 2009-06-06 21:03 CEST
Interesting ports on mars (192.168.178.27):
PORT   STATE         SERVICE
69/tcp closed        tftp
69/udp open|filtered tftp

Nmap done: 1 IP address (1 host up) scanned in 2.11 seconds

```Any Idea what I must do to get tftp running for all clients?

BR
Asterix99

---

### Post by jonobr on 2009-06-14
I would recommend using a wirehakr trace for this.

If you downlaod wireshark on the client , it should show the point at which the tftp is failing.

From your config, it looks like it shoudl be ready to go, so again, maybe the wirehark trace should show whats up.

If you dont want to install wireshark,

on the client (or server, 

you could run tcpdump -vvv -i <portname or any> 69

---

### Post by Asterix99 on 2009-06-16
Hello jonobr,  thanks for your hint. I'll try this. But I'm not very familiar with wireshark, so this will take a little bit time.  I thought there is an easy solution and this is a known "problem" and more users have the same problem.  BR Asterix99

---

### Post by azzid on 2010-03-09
I have issues similar to the original here.

I've installed ubuntu 9.10 for a client, they want to run tftp so I've been banging my head against tftpd-hpa for a few hours now.

When I try to fetch data from the server with my windows machine it fails like so:
```
H:\>tftp 192.168.4.153 get testfil.txt
Timeout occurred
 Connect request failed
```

During the failed transfer I get the following in my /var/log/daemon.log:
```
Mar  9 18:23:44 computername in.tftpd[2521]: RRQ from 192.168.4.120 filename testfil.txt
Mar  9 18:23:45 computername in.tftpd[2523]: RRQ from 192.168.4.120 filename testfil.txt
Mar  9 18:23:47 computername in.tftpd[2524]: RRQ from 192.168.4.120 filename testfil.txt
Mar  9 18:23:51 computername in.tftpd[2525]: RRQ from 192.168.4.120 filename testfil.txt
Mar  9 18:23:59 computername in.tftpd[2526]: RRQ from 192.168.4.120 filename testfil.txt
Mar  9 18:24:07 computername in.tftpd[2527]: RRQ from 192.168.4.120 filename testfil.txt
Mar  9 18:24:15 computername in.tftpd[2528]: RRQ from 192.168.4.120 filename testfil.txt
Mar  9 18:24:23 computername in.tftpd[2529]: RRQ from 192.168.4.120 filename testfil.txt

```
tftpd-hpa is not running under any kind of inet.d but as a standalone client:
```
$ ps -ef | grep tftp
root      2453     1  0 18:06 ?        00:00:00 /usr/sbin/in.tftpd -vvvvvvvvvvvvv -c -l -s /var/lib/tftpboot
```

The windows tftp-client is the one "built in" to windows server 2008.

I've attached the pcap-file I got when running wireshark on the client while trying to get a file.  From what I can understand though the only error I receive is the expected one when the connection times out.

When I run the tftp-hpa-client from another linux machine the process is actually working, but that will hardly be enough for the end user:
```
 $tftp -vvv 192.168.4.153 -c get testfil.txt
Connected to 192.168.4.153 (192.168.4.153), port 69
getting from 192.168.4.153:testfil.txt to testfil.txt [netascii]
Received 13 bytes in 0.1 seconds [1830 bit/s]
```

Also, putting a file is impossible on both platforms:
```
$ tftp -vvv 192.168.4.153 -c put test.sh
Connected to 192.168.4.153 (192.168.4.153), port 69
putting test.sh to 192.168.4.153:test.sh [netascii]
Transfer timed out.
```
```
H:\>tftp 192.168.4.153 PUT keyadd.bat
Timeout occurred
 Connect request failed
```

Any help would be appreciated, going insane here... :frown:

---

### Post by azzid on 2010-03-11
Feeling a little bit ignored... :(

---

### Post by azzid on 2010-03-12
Another interesting detail is that when I put a file it gets created but not filled with data.

[Server] Before:```
# ls -l /var/lib/tftpboot | grep testfil.tst
```

[Client] Then I run:```
~$ tftp -v 192.168.4.155 -c put testfil.tst
Connected to 192.168.4.155 (192.168.4.155), port 69
putting testfil.tst to 192.168.4.155:testfil.tst [netascii]
Transfer timed out.
```

[Server] After:```
# ls -l /var/lib/tftpboot | grep testfil.tst
-rw-rw-rw- 1 root root  0 2010-03-12 10:43 testfil.tst
```

The file should be 12 bytes, no 0.

---

### Post by azzid on 2010-03-12
Just realized that all my linux<->linux issues where due to some other network issue. Cut a few routers out of the picture and it worked.

The Windows 2008 R2 tftp client still wont work with tftpd-hpa though...

---

