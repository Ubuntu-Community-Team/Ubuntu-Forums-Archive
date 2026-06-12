---
title: "send mail to gmail or yahoo"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by mahmoodn on 2011-05-15
I want to send an email to gmail or yahoo account from ubuntu. I have installed sendmail and read a lot o pages to see how to do that. However till now I have not received any email !!!
can someone help step by step how to do that? 

Please start with a simple example that send mail from command line. Then I will complete it with bash script

---

### Post by conradin on 2011-05-16
Me too! Bump! Im trying a macro, but it keeps breaking.... :(

---

### Post by conradin on 2011-05-16
psst, mahmoodn, is using an FTP server ok for what youre doing?
Coz i can figure that one out no problem.

---

### Post by d3v1150m471c on 2011-05-16
```

man mail

mail -s "subject" email@email.com

```edit:
mail also accepts pipes, ie:
```

mail -s "subject" email@email.com < content.txt
# or
cat content.txt | mail -s "subject" email@email.com

```

you may also need to use `sudo' or otherwise have root privileges. It can take a few minutes for mail to show up so be patient.

---

### Post by mahmoodn on 2011-05-16
Is "mail" different from "sendmail"?
Which package should I install?

---

### Post by d3v1150m471c on 2011-05-16
i'm using bsd-mailx, but i'm almost certain mail is a standard linux command.

---

### Post by mahmoodn on 2011-05-16
this is the mail.info log after I executed this command
```
mail -s "subject" someone@yahoo.com < content.txt
```


```
May 16 14:41:38 srv1 sendmail[21686]: p4GABZ9c021686: from=mahmood, size=86, class=0, nrcpts=1, msgid=<201105161011.p4GABZ9c021686@srv1>, relay=mahmood@localhost
May 16 14:41:38 srv1 sm-mta[22375]: p4GABcSv022375: from=<mahmood@srv1>, size=319, class=0, nrcpts=1, msgid=<201105161011.p4GABZ9c021686@srv1>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
May 16 14:41:38 srv1 sendmail[21686]: p4GABZ9c021686: to=<someone@yahoo.com>, ctladdr=mahmood (1000/1000), delay=00:00:03, xdelay=00:00:00, mailer=relay, pri=30086, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (p4GABcSv022375 Message accepted for delivery)
May 16 14:42:58 srv1 sm-mta[22377]: p4GABcSv022375: to=<someone@yahoo.com>, ctladdr=<mahmood@srv1> (1000/1000), delay=00:01:20, xdelay=00:01:20, mailer=esmtp, pri=120319, relay=h.mx.mail.yahoo.com. [66.94.236.34], dsn=4.0.0, stat=Deferred: h.mx.mail.yahoo.com.: No route to host

```

as you can see, at first it says:
[COLOR="Red"]stat=Sent (p4GABcSv022375 Message accepted for delivery)[/COLOR]

but after some minutes it says
[COLOR="Red"]stat=Deferred: h.mx.mail.yahoo.com.: No route to host[/COLOR]

strange because, I am able to ping that address
```

mahmood@srv1:~$ ping h.mx.mail.yahoo.com
PING h.mx.mail.yahoo.com (66.94.236.34) 56(84) bytes of data.
64 bytes from mta-v2.mail.vip.mud.yahoo.com (66.94.236.34): icmp_seq=1 ttl=43 time=232 ms
64 bytes from mta-v2.mail.vip.mud.yahoo.com (66.94.236.34): icmp_seq=2 ttl=43 time=234 ms
64 bytes from mta-v2.mail.vip.mud.yahoo.com (66.94.236.34): icmp_seq=3 ttl=43 time=243 ms
^C
--- h.mx.mail.yahoo.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 3904ms
rtt min/avg/max/mdev = 232.591/236.784/243.664/4.919 ms

```

---

### Post by d3v1150m471c on 2011-05-16
humor me and try installing bsd-mailx and/or postfix, i think bsd-mailx might rely on postfix or vice versa...and then try that command again.

edit:
or try doing that command one more time as root.

---

### Post by mahmoodn on 2011-05-16
```
mahmood@srv1:~$ which mail
/usr/bin/mail
mahmood@srv1:~$ dpkg -l | grep "bsd-mailx"
ii  bsd-mailx                            8.1.2-0.20090911cvs-2ubuntu1          simple mail user agent

```

I ran that command after installing bsd-mailx

---

### Post by d3v1150m471c on 2011-05-16
> **mahmoodn said:**
> ```
mahmood@srv1:~$ which mail
/usr/bin/mail
mahmood@srv1:~$ dpkg -l | grep "bsd-mailx"
ii  bsd-mailx                            8.1.2-0.20090911cvs-2ubuntu1          simple mail user agent

```I ran that command after installing bsd-mailx

I used the following to send a message, as root, to my gmail account and it worked perfectly, it just took it a few minutes to arrive:
```

sudo mail -s "subject" myaccount@gmail.com < file.txt

```I'm running bsd-mailx and I also have postfix installed. I do not have sendmail installed.

```

#additional info:

d3v11@d3v11m4ch1n3:~$ dpkg --get-selections | grep install | grep mail
bsd-mailx                    install
libmail-sendmail-perl                install
libmailtools-perl                install
libmailutils2                    deinstall
mailutils                    deinstall
openoffice.org-emailmerge            install
d3v11@d3v11m4ch1n3:~$ dpkg --get-selections | grep install | grep postfix
postfix                        install
d3v11@d3v11m4ch1n3:~$ 

```


note: I've noticed I am no longer able to send mail except as root. I'm wondering if this has something to do with security changes when I upgraded from karmic to 10.04

---

