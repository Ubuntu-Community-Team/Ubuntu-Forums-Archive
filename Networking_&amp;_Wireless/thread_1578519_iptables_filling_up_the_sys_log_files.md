---
title: "iptables filling up the sys log files"
date: 2010-09-20
forum: Networking &amp; Wireless
---

### Post by pagirard on 2010-09-20
hi all,

I have an issue with my log files getting huge in a record time :
-rw-r----- 1 syslog            adm   9.8G 2010-09-20 09:06 kern.log.1
-rw-r----- 1 syslog            adm   9.8G 2010-09-20 09:03 syslog.1
-rw-r----- 1 syslog            adm   9.7G 2010-09-20 09:06 debug.1

I basically get the same messages in kern.log, syslog and debug.log :

```
Sep 20 09:06:07 pitoubuntu kernel: [34696.398341] BANDWIDTH_IN:IN=eth0 OUT= MAC=
00:15:f2:06:b4:d8:00:11:95:cc:d3:cb:08:00 SRC=205.160.245.109 DST=192.168.0.141
LEN=92 TOS=0x00 PREC=0x00 TTL=52 ID=22944 DF PROTO=TCP SPT=47964 DPT=22 WINDOW=6
5535 RES=0x00 ACK PSH URGP=0
Sep 20 09:06:07 pitoubuntu kernel: [34696.408064] BANDWIDTH_OUT:IN= OUT=eth0 SRC
=192.168.0.141 DST=205.160.245.109 LEN=92 TOS=0x10 PREC=0x00 TTL=64 ID=58489 DF
PROTO=TCP SPT=22 DPT=47964 WINDOW=65535 RES=0x00 ACK PSH URGP=0
Sep 20 09:06:07 pitoubuntu kernel: [34696.443609] BANDWIDTH_IN:IN=eth0 OUT= MAC=
00:15:f2:06:b4:d8:00:11:95:cc:d3:cb:08:00 SRC=205.160.245.109 DST=192.168.0.141
LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=22955 DF PROTO=TCP SPT=47964 DPT=22 WINDOW=6
5535 RES=0x00 ACK URGP=0
```

From what I could gather, it is apparently the results of iptables filling the logs with regular traffic information (?)

so I checked my tables and then tried to turn the log file configuration /etc/rsyslog.d/50-default.conf :

```
#  Default rules for rsyslog.
#
#                       For more information see rsyslog.conf(5) and /etc/rsyslo
g.conf

#
# First some standard log files.  Log by facility.
#
auth,authpriv.*                 /var/log/auth.log
*.*;auth,authpriv.none          -/var/log/syslog
#cron.*                         /var/log/cron.log
daemon.*                        -/var/log/daemon.log
kern.*                          -/var/log/kern.log
lpr.*                           -/var/log/lpr.log
mail.*                          -/var/log/mail.log
user.*                          -/var/log/user.log

#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
mail.info                       -/var/log/mail.info
mail.warn                       -/var/log/mail.warn
mail.err                        /var/log/mail.err

#
# Logging for INN news system.
#
news.crit                       /var/log/news/news.crit
news.err                        /var/log/news/news.err
news.notice                     -/var/log/news/news.notice

#
# Some "catch-all" log files.
#
*.=debug;\
        auth,authpriv.none;\
        news.none;mail.none     -/var/log/debug
*.=info;*.=notice;*.=warn;\
        auth,authpriv.none;\
        cron,daemon.none;\
        mail,news.none          -/var/log/messages

#
# Emergencies are sent to everybody logged in.
#
*.emerg                         *

#
# I like to have messages displayed on the console, but only on a virtual
# console I usually leave idle.
#
#daemon,mail.*;\
#       news.=crit;news.=err;news.=notice;\
#       *.=debug;*.=info;\
#       *.=notice;*.=warn       /dev/tty8

# The named pipe /dev/xconsole is for the `xconsole' utility.  To use it,
# you must invoke `xconsole' with the `-file' option:
#
#    $ xconsole -file /dev/xconsole [...]
#
# NOTE: adjust the list below, or you'll go crazy if you have a reasonably
#      busy site..
#
daemon.*;mail.*;\
        news.err;\
        *.=debug;*.=info;\
        *.=notice;*.=warn       |/dev/xconsole

```

Ant help would be appreciated, I can't stay for al ong time with a server creating 10Gb of log/week end ...

Thanks in advance

Pierre

---

### Post by CandidMan on 2010-09-20
Hi,
i don't have extensive experience with iptables, but if you're running Ubuntu and are comfortable with the command line I'd start with
```
iptables -L INPUT
```

and look for entries with LOG. The default install isn't cluttered with chains so it should be easy to spot

---

### Post by pagirard on 2010-09-20
Ohhhh,

Seems like you put your finger on something :

```
pitou@pitoubuntu:~$ sudo iptables -L INPUT
Chain INPUT (policy DROP)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere            LOG level debug prefix `BANDWIDTH_IN:'
DROP       tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds
           all  --  anywhere             anywhere
ufw-before-logging-input  all  --  anywhere             anywhere
ufw-before-input  all  --  anywhere             anywhere
ufw-after-input  all  --  anywhere             anywhere
ufw-after-logging-input  all  --  anywhere             anywhere
ufw-reject-input  all  --  anywhere             anywhere
ufw-track-input  all  --  anywhere             anywhere
pitou@pitoubuntu:~$
```

So apparently iptable is logging for all protocole, everything going everywhere !

Since I'm really not familiar with iptables, does someone know how to remove this line ?

I swear I'll read the man page in the meantime :)

Pierre

---

### Post by CandidMan on 2010-09-20
Phew, that's a relief :) :
To get rid of that rule as it stands
```
sudo iptables -D INPUT 1
```By the way, one of the admins has written a decent overview here [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

EDIT: Just thought, you'll have to enter the command above every time you restart your computer, unless the rule's been added recently.

---

### Post by pagirard on 2010-09-20
so close....yet so far.

I did run the command and verified that the iptables line waas removed :

```
pitou@pitoubuntu:/var/log$ sudo iptables -L INPUT
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
DROP       tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds
           all  --  anywhere             anywhere
```


But a short tail -f /etc/syslog shows me the same every second filling up of the log file. What else could write these messages ?

And why would they be replicated on syslog, kernel and debug log files ?

Anyway, thanks a lot for the link, I know what I'm reading tonight !

Have a good day

Pierre

---

### Post by CandidMan on 2010-09-21
Nearly there, yeah that page is really helpful
Just taking a second look, you might have a similar problem with outgoing traffic

```
sudo iptables -L OUTPUT
```

Have a good one :)

---

### Post by pagirard on 2010-09-21
Wonderful, that solved it

for the record : 

display your iptables rules for input and output :

```
sudo iptables -L INPUT
sudo iptables -L OUTPUT
```

search for the lines stating
LOG        all  --  anywhere             anywhere            LOG level debug prefix `BANDWIDTH_IN:'

and remove them : 
```
sudo iptables -D INPUT 1
sudo iptables -D OUTPUT 1
```

replace the "1" above with the line number

Thanks a lot for your help, greatly appreciated

Pierre

---

### Post by CandidMan on 2010-09-21
Don't mention it. the standard fee applies

$0.00
lol jk

Just as an aside, you might want to remedy whatever caused those rules to appear in iptables in the first place

And with that I'm out
[I]
Exit, stage left!![/I]

---

