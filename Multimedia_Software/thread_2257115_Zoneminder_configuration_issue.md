---
title: "Zoneminder configuration issue"
date: 2014-12-17
forum: Multimedia Software
---

### Post by Richard_Gosling on 2014-12-17
Hi,

I had a working Zoneminder setup on12.04 LTS and decided it would be a good idea to upgrade to 14.04. It was not such a good idea!

After upgrading I found that my video capture card drivers - Techwell TW68 - did not compile on 14.04. It kept complaining of missing dependencies. My Ubuntu knowledge is not that good to try to fix it, so I decided to just go back to 12.04 again.

So I did a fresh install of 12.04 LTS, then installed zoneminder from the repositories which gave me Zoneminder 1.25.

Everything seemed to go OK. I compiled my TW68 drivers and then tried to set up a new monitor in Zoneminder.

The problem came when I tried to view the stream from the monitor. I got a blank area where the image should have been.

I checked the log file and saw this;

[TABLE="class: major table-sortable, width: 1021"]
[TR="class: log-err table-tr-group-head"]
[TD="bgcolor: #FFCCCC, align: left"]socket_sendto( /tmp/zm/zms-972667s.sock ) failed: No such file or directory[/TD]
[TD="bgcolor: #FFCCCC, align: left"]/usr/share/zoneminder/includes/functions.php[/TD]
[/TR]
[/TABLE]

There was also this error which I've seen before;
[TABLE="class: major table-sortable, width: 1021"]
[TR="class: log-err table-tr-group-head table-tr-odd, bgcolor: #F8F8F8"]
[TD="bgcolor: #FFCCCC, align: left"]'zmc -d /dev/video0' exited abnormally, exit status 255[/TD]
[TD="bgcolor: #FFCCCC, align: left"]zmdc.pl[/TD]
[/TR]
[/TABLE]

The second error I know is down to shared memory settings. So I googled the first error and most people keep pointing back to these steps which focus on ensuring that CGI is enabled in apache2;

```
1) Keep the default zone apache.conf without the ScriptAlias.

2) Stop both zoneminder and apache2
sudo service apache2 stop
sudo service zoneminder stop

2) Remove any stale sockets from /tmp/zm (default location):
sudo rm -vf /tmp/zm/*.*

3) sudo a2enmod cgi

4) Start zoneminder
sudo service zoneminder start

5) Start apache2
sudo service apache2 start

I found out that the order was important for step 4 and 5, otherwise it
doesn't work.
```


So I set my shared memory settings in /etc/sysctl.conf to;

kernel.shmall = 167772160
   kernel.shmmax = 167772160

Then followed the steps above regarding the apache 2 cgi module.

This got rid of my second error of "exit status 255", but the first error remains.

I also noted that it says that the file /tmp/zm/zms-972667s.sock does not exist, but I do not have a "zm" folder inside of "/tmp", could this be the issue?

I would be greatful for any suggestions on how to fix this as it seems like it should be just a simple configuration change.

Thanks.

---

### Post by Richard_Gosling on 2014-12-18
Just a quick update.

I've manually added the /tmp/zm folder and given www-data read/write permissions to it, but it didn't help.

---

