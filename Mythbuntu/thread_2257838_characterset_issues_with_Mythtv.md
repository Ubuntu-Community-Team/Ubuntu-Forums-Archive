---
title: "characterset issues with Mythtv"
date: 2014-12-22
forum: Mythbuntu
---

### Post by nainsurvolte on 2014-12-22
I thought I had found the issue and solved it but no.

I few weeks ago, for some reason I don't know, some show in the program listing started showing strange character. For example, "é" started to look like "Ã©" (most of my channel are french). The only lead I had after looking at the web was some issue in mysql between utf8 and latin1.

Following a lead on some old corruption at this link seemed promising 
[https://www.mythtv.org/wiki/Fixing_Corrupt_Database_Encoding](https://www.mythtv.org/wiki/Fixing_Corrupt_Database_Encoding)

The reason was that when getting info from mysql using the following command gave me all utf8 instead of latin1.

```
[COLOR=black][FONT=monospace]mysql -umythtv -p mythconverg -e 'status;'[/FONT][/COLOR]
```

Anyhow, I went through the directive anyway and it seem to have fix the issue, but only for some time and even that I am not sure. Now, running that same command give me all latin1. 
```
mysql  Ver 14.14 Distrib 5.5.40, for debian-linux-gnu (x86_64) using readline 6.2

Connection id:          5463
Current database:       mythconverg
Current user:           mythtv@localhost
SSL:                    Not in use
Current pager:          stdout
Using outfile:          ''
Using delimiter:        ;
Server version:         5.5.40-0ubuntu0.12.04.1 (Ubuntu)
Protocol version:       10
Connection:             Localhost via UNIX socket
Server characterset:    latin1
Db     characterset:    latin1
Client characterset:    latin1
Conn.  characterset:    latin1
UNIX socket:            /var/run/mysqld/mysqld.sock
Uptime:                 22 days 16 hours 36 min 40 sec


Threads: 12  Questions: 33014284  Slow queries: 8  Opens: 29121  Flush tables: 1  Open tables: 128  Queries per second avg: 16.838

```

When looking at the coming programs in the listing, I see correct naming, but not for the program in the next day (+approx 10hrs) from the current time.

[IMG]https://lh6.googleusercontent.com/-o--mtAAoBQA/VJj1yhBGluI/AAAAAAAACzk/iphErPkuiGk/w1284-h205-no/mythtv%2Bissue.jpg[/IMG]

Also, looking for issues with the keyword latin1 in it, I found some post regarding a mixed database having both utf8 and latin1 when looking at the mythconverg database with phpmyadmin. I checked it out, and browsing through the tables, I see "Collation" that are either "utf8_general_ci" or "latin1_swedish_ci". :confused:

Suffice to say that I am lost....

Another detail... although when I first got the issue all my scheduled recording were not working (character of the program did not match those of the program), It seem to recognize the titles or the keyword used for the scheduled recording. But they show up with weird character...

Thanks,

---

