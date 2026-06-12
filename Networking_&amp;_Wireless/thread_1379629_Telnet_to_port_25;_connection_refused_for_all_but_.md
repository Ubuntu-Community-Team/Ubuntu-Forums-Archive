---
title: "Telnet to port 25; connection refused for all but local host"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by abasel on 2010-01-12
I can telnet (while on the actual machine) using

> telnet localhost 25

When I try and use the local machine's ip 
> telnet 192.168.100.9  25

I get
> Trying 192.168.100.9...
telnet: Unable to connect to remote host: Connection refused

When I use it's URL
> telnet rcws01.rosminicollege.school.nz 25

I get
> Trying 127.0.1.1...
telnet: Unable to connect to remote host: Connection refused

This last one is strange as I the IP looks odd.

What I am doing wrong, and how do I fix it. After much surfing many mosts say that telnet is not used anymore but I want to use it to test my smtp server.

---

### Post by gombadi on 2010-01-12
Looks like your email server is only listening on localhost. If you run the following command you can see what it is listening on -

```

sudo netstat -plntu

```

You will see a line like -

```

tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      5807/master 

```

You need to change your email server config to listen on all interfaces - differs depending on the email server you are using.

> 

Quote:
Trying 127.0.1.1...
telnet: Unable to connect to remote host: Connection refused
This last one is strange as I the IP looks odd.


My guess is you will have an entry in your /etc/hosts file for rcws01.rosminicollege.school.nz which translates to 127.0.0.1 so that is why the ip address looks like that.

---

### Post by abasel on 2010-01-12
Hi, yes you are right. How do I make it listern on other ips? I am using Postfix.

Thanks

---

### Post by gombadi on 2010-01-13
Edit /etc/postfix/main.cf and change the following line as shown -

```

inet_interfaces = all

```

Note that this change will allow any machine that can connect to your machine to be able to connect to postfix. Check out the postfix documentation for tips on how to secure your server and think about installing a firewall.

---

### Post by abasel on 2010-01-13
uhm... it looks like that is already the case

see main.cf bellow

> # See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = rcws01.rosminicollege.school.nz
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = rcws01.rosminicollege.school.nz, localhost.rosminicollege.schoo$
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all


---

### Post by gombadi on 2010-01-14
Interesting

Can you post the output of 
```

sudo netstat -plntu

```

---

### Post by abasel on 2010-01-17
The last line of main.cf, has

> inet_interfaces = all 

Here is netstat -plntu

> root@rcws01:~# netstat -plntu
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:389             0.0.0.0:*               LISTEN      3951/slapd
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      3884/mysqld
tcp        0      0 127.0.0.1:587           0.0.0.0:*               LISTEN      4020/sendmail: MTA:
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      4205/apache2
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      3794/sshd
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      4020/sendmail: MTA:
tcp6       0      0 :::389                  :::*                    LISTEN      3951/slapd
tcp6       0      0 :::22                   :::*                    LISTEN      3794/sshd


---

### Post by gombadi on 2010-01-18
> 
tcp 0 0 127.0.0.1:587 0.0.0.0:* LISTEN 4020/sendmail: MTA:
tcp 0 0 127.0.0.1:25 0.0.0.0:* LISTEN 4020/sendmail: MTA:


There is the problem - you are using sendmail and not postfix.

You need to either edit the /etc/mail/sendmail.mc file(can't remember off the top of my head the setting to change) 

or you need to remove sendmail and use postfix :-)

---

### Post by abasel on 2010-01-18
I, I've definetly installed postfix and can even run

> dpkg-reconfigure postfix


When I try to remove sendmail I get

> root@rcws01:~# apt-get remove sendmail
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package sendmail is not installed, so not removed
The following packages were automatically installed and are no longer required:
  gcj-4.3-base libsm-dev libstdc++5 libice-dev x11proto-xext-dev liblcms1
  libgcj9-0 ttf-wqy-zenhei libgcj-bc x11proto-kb-dev ttf-kochi-mincho
  sun-javadb-common ttf-kannada-fonts sendmail-base libjaxp1.3-java-gcj
  libxi-dev java-common libaccess-bridge-java libxdmcp-dev libxerces2-java-gcj
  ttf-kochi-gothic procmail xtrans-dev fontconfig ant-optional-gcj libxfont1
  sensible-mda imqv2 x11proto-core-dev ant default-jdk libcups2 default-jre
  libgcj-common sendmail-cf libgif4 ttf-telugu-fonts libjaxp1.3-java
  openjdk-6-jre-headless libxt-dev openjdk-6-jdk sun-javadb-core tzdata-java
  libxext-dev libice6 openjdk-6-jre openjdk-6-jre-lib libgcj9-jar
  libxerces2-java x11proto-input-dev libasound2 libpthread-stubs0-dev
  libxau-dev libpthread-stubs0 libfontenc1 glassfishv2-bin xfonts-utils
  libxtst6 rhino ttf-indic-fonts-core ttf-oriya-fonts ttf-baekmuk libsm6
  libx11-dev libxcb-xlib0-dev default-jre-headless libxi6 ca-certificates-java
  libxcb1-dev ttf-bengali-fonts ant-gcj xfonts-encodings ant-optional libxt6
  x-ttcidfont-conf make
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


Sorry, I must be missing something :oops:

---

### Post by gombadi on 2010-01-18
Even more interesting :-)

> 
```

tcp 0 0 127.0.0.1:587 0.0.0.0:* LISTEN 4020/sendmail: MTA:
tcp 0 0 127.0.0.1:25 0.0.0.0:* LISTEN 4020/sendmail: MTA: 

```


Can you please run the following command. It will tell us what actual program is listening on port 25.

```

ls -l /proc/4020 | grep exe

```

You may need to change the above number if the pid of sendmail has changed - run the netstat -plntu command again to see if it is still pid 4020.

You will see output similar to 

```

[root@system ~]# ls -la /proc/4022 | grep exe
lrwxrwxrwx  1 root root 0 2010-01-19 08:14 exe -> /usr/lib/postfix/master

```

Then lets see what package that file belongs to 

```

[root@system ~]# dpkg -S /usr/lib/postfix/master
postfix: /usr/lib/postfix/master

```

It belongs to the postfix package.

Try that on yours and lets see what package the program is from.

---

### Post by jonedney on 2012-04-29
I'd like to "re-spark" this topic, as I'm going through the same problem, but with a public IP address and port 25 being refused.

```
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      1419/sendmail: MTA:
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      5516/apache2    
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      1169/smbd       
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      18004/dovecot   
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      18004/dovecot   
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      7787/mysqld     
tcp        0      0 127.0.0.1:587           0.0.0.0:*               LISTEN      1419/sendmail: MTA:
```

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/server.crt
smtpd_tls_key_file = /etc/ssl/private/server.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.jonedneycreative.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname, /etc/postfix/virtual/domains
virtual_maps  = hash:/etc/postfix/virtual/addresses
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 216.119.142.16
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth-client
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
inet_protocols = all

```

Additionally, I also installed Postfix, per the Ubuntu 11.10 Server Guide.  When I do telnet localhost 25 everything works, but when I check it via the VPS IP at MX Toolbox, it says port 25 is being refused.

Additionally, I have no firewalls set up.  The VPS package is hosted with a web host, but is user-managed, so I have no support.

Trying to learn, anything to go off of would be excellent!

Thank you,
Jon Edney

---

### Post by SeijiSensei on 2012-04-29
Try replacing 

```
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 216.119.142.16
```

with

```
mynetworks = 0.0.0.0/0 [::/0]
```

That enables connections from anywhere.

---

### Post by jonedney on 2012-04-29
Hello Seiji!

I have made the change you recommended, and am still getting "target machine actively refused connection" when I test the server from MX Toolbox.

Any advice?

Thanks,
Jon

---

### Post by SeijiSensei on 2012-04-29
Did you restart Postfix?  What do you see in /var/log/mail.log?  If there aren't any connections being logged, then you're not actually reaching the server daemon.

If you're trying to connect from a residential connection, your ISP may be blocking outbound port 25 requests.  Try "telnet aspmx.l.google.com 25".  I can't connect to that from my house, but I can connect from my virtual server at Linode.

---

### Post by jonedney on 2012-04-29
Hello!

Yes, postfix was restarted.  I am able to telnet google without problem.  I checked the log, and it seems nothing is being registered.  Below is the log after I ran the telnet server 25.

```
root@jonedneycreative:~# tail /var/log/mail.log
Apr 29 19:23:55 jonedneycreative dovecot: pop3-login: Disconnected (no auth attempts): rip=64.20.227.133, lip=216.119.142.16
Apr 29 19:23:55 jonedneycreative dovecot: imap-login: Disconnected (no auth attempts): rip=64.20.227.133, lip=216.119.142.16
Apr 29 19:27:27 jonedneycreative dovecot: config: Warning: NOTE: You can get a new clean config file with: doveconf -n > dovecot-new.conf
Apr 29 19:27:27 jonedneycreative dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:89: add auth_ prefix to all settings inside auth {} and remove the auth {} section completely
Apr 29 19:27:27 jonedneycreative dovecot: pop3-login: Disconnected (tried to use disabled plaintext auth): rip=209.85.217.139, lip=216.119.142.16
Apr 29 20:27:27 jonedneycreative dovecot: pop3-login: Disconnected (tried to use disabled plaintext auth): rip=209.85.215.6, lip=216.119.142.16
Apr 29 21:27:26 jonedneycreative dovecot: config: Warning: NOTE: You can get a new clean config file with: doveconf -n > dovecot-new.conf
Apr 29 21:27:26 jonedneycreative dovecot: config: Warning: Obsolete setting in /etc/dovecot/dovecot.conf:89: add auth_ prefix to all settings inside auth {} and remove the auth {} section completely
Apr 29 21:27:27 jonedneycreative dovecot: pop3-login: Disconnected (tried to use disabled plaintext auth): rip=209.85.215.15, lip=216.119.142.16
Apr 29 22:27:26 jonedneycreative dovecot: pop3-login: Disconnected (tried to use disabled plaintext auth): rip=209.85.217.157, lip=216.119.142.16
```

Thanks!
Jon

---

### Post by SeijiSensei on 2012-04-29
Sounds like a firewall somewhere at the server end to me, Jon.  I'm pretty much out of ideas beyond that.

If the server's address is the one in the 216 network you posted before and up above here, I get an immediate "connection refused" if I try to telnet to port 25 at that address.  If I run nmap against that address I can see a variety of open ports, but not 25.

I understand that you may not get a lot of support from the hosting company, but they should at least be able to confirm that there's nothing blocking incoming port 25.

One other diagnostic you can try is logging connections to port 25 with iptables like this:

```
sudo iptables -I INPUT -p tcp --dport 25 -j LOG
```

(Using "-I" puts this rule at the top of the ruleset in case other rules further down the list would get in the way.)  You should see entries in either /var/log/syslog or /var/log/messages; I'm not sure which applies on Ubuntu servers.

---

### Post by jonedney on 2012-04-29
Well I'm definately going to have to check with my web host.

```
PORT    STATE SERVICE
25/tcp  open  smtp

```

I think that says it all.

Jon

---

### Post by SeijiSensei on 2012-04-29
Just to make sure, did you run nmap against the external 216 address and not localhost?

---

### Post by jonedney on 2012-05-04
Hello all!

Didn't realize I didn't post a response.  After chatting with someone in IRC, I decided against running  a mailserver until I get uber Ubuntu skills.

Jon

---

### Post by xefialtis on 2012-05-09
I am also having this problem.

I am hoping someone can help me debug this issue...

My mail server suddenly went deaf on the 27th of last month. It just stopped receiving and sending mail.

Frustrating, as I changed NOTHING until AFTER I started to debug the issue, but it doesn't seem that anything I do changes anything...

Others have checked my config files, and nothing seems amiss, but when we look at the "netstat" output, SMPT is not in the list...
How do I crank up SMTP or what else might be wrong?

```
Proto Recv-Q Send-Q Local Address Foreign Address State PID/Program name
tcp 0 0 0.0.0.0:993 0.0.0.0:* LISTEN 1477/dovecot
tcp 0 0 127.0.0.1:3306 0.0.0.0:* LISTEN 952/mysqld
tcp 0 0 127.0.0.1:139 0.0.0.0:* LISTEN 10434/smbd
tcp 0 0 192.168.x.x:139 0.0.0.0:* LISTEN 10434/smbd
tcp 0 0 0.0.0.0:143 0.0.0.0:* LISTEN 1477/dovecot
tcp 0 0 0.0.0.0:10000 0.0.0.0:* LISTEN 1596/perl
tcp 0 0 192.168.x.x:53 0.0.0.0:* LISTEN 852/named
tcp 0 0 127.0.0.1:53 0.0.0.0:* LISTEN 852/named
tcp 0 0 0.0.0.0:22 0.0.0.0:* LISTEN 1086/sshd
tcp 0 0 127.0.0.1:1143 0.0.0.0:* LISTEN 1535/imapproxyd
tcp 0 0 0.0.0.0:31416 0.0.0.0:* LISTEN 1145/boinc
tcp 0 0 0.0.0.0:25 0.0.0.0:* LISTEN 11036/master
tcp 0 0 127.0.0.1:953 0.0.0.0:* LISTEN 852/named
tcp 0 0 127.0.0.1:445 0.0.0.0:* LISTEN 10434/smbd
tcp 0 0 192.168.x.x:445 0.0.0.0:* LISTEN 10434/smbd
tcp6 0 0 2002:43a6:xxxx:xxxx:139 :::* LISTEN 10434/smbd
tcp6 0 0 fe80::21b:xxxx:xxxx:139 :::* LISTEN 10434/smbd
tcp6 0 0 :::80 :::* LISTEN 1529/apache2
tcp6 0 0 :::113 :::* LISTEN 7620/gidentd
tcp6 0 0 :::53 :::* LISTEN 852/named
tcp6 0 0 :::22 :::* LISTEN 1086/sshd
tcp6 0 0 :::25 :::* LISTEN 11036/master
tcp6 0 0 ::1:953 :::* LISTEN 852/named
tcp6 0 0 :::443 :::* LISTEN 1529/apache2
tcp6 0 0 2002:43a6:xxxx:xxxx:445 :::* LISTEN 10434/smbd
tcp6 0 0 fe80::21b:xxxx:xxxx:445 :::* LISTEN 10434/smbd
udp 0 0 192.168.1.5:137 0.0.0.0:* 10442/nmbd
udp 0 0 0.0.0.0:137 0.0.0.0:* 10442/nmbd
udp 0 0 192.168.x.x:138 0.0.0.0:* 10442/nmbd
udp 0 0 0.0.0.0:138 0.0.0.0:* 10442/nmbd
udp 0 0 0.0.0.0:10000 0.0.0.0:* 1596/perl
udp 0 0 192.168.x.x:53 0.0.0.0:* 852/named
udp 0 0 127.0.0.1:53 0.0.0.0:* 852/named
udp 0 0 0.0.0.0:68 0.0.0.0:* 963/dhclient3
udp 0 0 0.0.0.0:68 0.0.0.0:* 1052/dhclient3
udp6 0 0 :::53 :::* 852/named

```

---

