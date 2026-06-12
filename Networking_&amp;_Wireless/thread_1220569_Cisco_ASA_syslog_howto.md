---
title: "Cisco ASA syslog howto"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by ipguru99 on 2009-07-22
This all seemed easier on 6.06, but I have done this a couple of times on 8.04 now and I always have to hunt all over Google to find it.  
So... Syslog for the ASA on Ubuntu8.04:

All of this assumes you are root

1.  Create a directory and change ownership: ```
mkdir /var/log/asa;chown root:syslog /var/log/asa
```

2.  Create a file in /var/log/asa and change ownership: ```
touch /var/log/asa/asa;chown root:syslog /var/log/asa/asa
```

4.  Create a file: ```
touch /etc/logrotate.d/asa
```  Paste these 7 lines as follows:

```
/var/log/asa/asa {
	daily	
	rotate 365 
	missingok
	compress
	create 640 root adm
}
```

5.  Edit the /etc/default/syslogd file.  At the bottom of the file, there is a comment '# For remote UDP logging use SYSLOGD="-r"'

Put that -r in between the quotes and save the file.

6.  These are the commands I put in the ASA.. yours might be different, I am logging a bunch (that is what the 'logging trap debugging' line is)

```
logging enable
logging timestamp
logging buffered debugging
logging trap debugging
logging asdm emergencies
logging facility 17
logging host inside ip.of.Ubuntu.box
```

7.  At the bottom of /etc/syslog.conf, paste this:

```
local1.*	/var/log/asa/asa
```

Additional note... These facility/local pairings are all over the internet.. use the Google machine!  But for this exercise, I used  
local1 and facility 17.  The standard is: local0 maps to facility 16, local2 maps to facility 18, etc., etc....

8.  Restart syslog with: ```
/etc/init.d/sysklogd restart
```

9.  I found something that said to ```
logrotate -f /var/log/asa/asa
```, and I did (It stopped logging for about 60 seconds, but then everything started again).  I don't know if you need to do this, but I did... and it rotated the logs.

10.  To test if it is working, type: ```
tail -f /var/log/asa/asa
```

Another Additional note...

With this config, your /var/log/messages and /var/log/syslog will also fill up with firewall logs.  I didn't like this, so I added the following
to the /etc/syslog.conf file

On the second uncommented line:
```
*.*;auth,authpriv.none,local1.none		-/var/log/syslog

```
On the 42nd line... ending with:
```
*.=info;*.=notice;*.=warn;\
        auth,authpriv.none;\
        cron,daemon.none;\
        mail,news.none,local1.none              -/var/log/messages
```

That 'local1.none' tells it to NOT log to those files.


If anyone can add to this, please do.

---

### Post by nerdelicious on 2009-11-27
Thanks a lot for this, it has helped me a great deal with setting up ASA logging on 9.10 Karmic Koala.

A few comments for posterity, though, since Karmic seems to use rsyslog instead of syslog. I apologize in advance for possible newbie comments, I am kind of an Ubuntu newbie.

**step 4.** - you have a typo there, "toutch" instead of "touch". Here's my /etc/logrotate.d/asa

```
/var/log/asa/asa {
        rotate 20
        size=20M 
        missingok
        compress
        create 640 syslog adm
        postrotate
                reload rsyslog >/dev/null 2>&1 || true
        endscript
}
```

I've found that, due to really fast-growing logs, it makes more sense for me to rotate & compress them when they reach 20 M, rather than doing it once  a day.

** step 5.** - uncomment:
```
# provides UDP syslog reception
$ModLoad imudp
$UDPServerRun 514
``` in /etc/rsyslog.conf in order to allow remote UDP logging (instead of SYSLOGD="-r" thing in /etc/default/syslogd).

** step 8.** - you can restart rsyslog with:
```
service rsyslog restart
```[B]

step 10.[/B] - rsyslog uses /etc/rsyslog.conf , which by default includes /etc/rsyslog.d directory for rsyslog config files. So instead of editing /etc/syslog.conf I edited /etc/rsyslog.d/50-default.conf the same way you described.

By the way, ipguru99, in step 2 you ```
chown root:syslog /var/log/asa/asa 
``` but in step 4, when you configure logrotate, you seem to set it to "root:adm". Is there a reason for this?

I believe that's about it, everything else should be the same. Thanks again.

---

### Post by ipguru99 on 2009-11-27
Nerdelicious, Thanks for the typo notice!  I edited it.  

When I was last doing this (and digging all over), I noticed most of the generated logs were owned by the group adm.. I think that made the decision for the chown permissions in Step 2.

My only advice on the 20M log files is about dates.  That is why I do mine daily.  If something happened in the afternoon and I am not sure which file to look through (I know, I know.. look at the file create time)... but if I am in a hurry looking for something that I know took place on November 5, 2009, I would like to do all my file operations on that one file.. just my thoughts ;-)

I had a customer with a hosted web site and the site was attacking them.. it was so much easier to do this on one file```
root@jffnms2:~# zcat /var/log/asa/asa.1.gz | grep "Nov 05 2009" | grep [D,d]eny | grep xx\.xxx\.x\.xxx | wc -l
55209
```
and tell them this is how many times the sites was attacking per day.

I wouldn't say anything if it hadn't have come in handy one day.

By the way, thanks for adding to this.. I didn't even know what rsyslog was!

---

### Post by -lodogg- on 2010-01-04
Great write up...  I have been trying to port all of my ASA syslog data to a MySQL database and I have had pretty good luck with the following code.

-----------
nano /etc/rsyslog.conf

$ModLoad ommysql

*.*       :ommysql:IPAddress,Database,username,password
-----------

I also ran the *.sql file from the rsyslog documentation, but the problem is the main syslog data is stored in one table rather then separating the data in separate columns.  Has anyone come across MySQL databases built for ASA logging and the proper rsyslog.conf file to parse the data?

thx
-lo

---

### Post by -lodogg- on 2010-01-05
And I have the following setup in my /etc/rsyslog.conf file and all of debugging logging from my ASA is still being written to all of my log files /var/messages, /var/syslog and /var/debug and of course /var/cisco.log.  I would appreciate any help with the proper /etc/rsyslog.conf.

------------------------------------
*.*;auth,authpriv.none,local1.none    -/var/log/syslog


*.=info;*.=notice;*.=warn;\
        auth,authpriv.none;\
        cron,daemon.none;\   
        mail,news.none,local1.none    -/var/log/messages

#include exceptions for local
local7.*   -/var/log/debug

#Logging local 3 and 4 to cisco.log
local3.* /var/log/cisco.log
local4.* /var/log/cisco.log
------------------------------------

---

