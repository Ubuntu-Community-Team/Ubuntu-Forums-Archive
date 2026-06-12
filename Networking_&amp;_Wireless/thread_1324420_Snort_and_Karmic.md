---
title: "Snort and Karmic"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by Mgiacchetti on 2009-11-12
I found this...
[www.snort.org/assets/113/Snort_2.8.4.1_Ubuntu.pdf]("http://ubuntuforums.org/www.snort.org/assets/113/Snort_2.8.4.1_Ubuntu.pdf")

It's for Ubuntu 9, but was written 16 Jul 2009.  I need to quickly find out what the differences between setting that up on 9.04 and 9.10.

first of all there is a bad mistype on page 11 in Starting Snort and Finishing Barnyard Config:
```

snort -c /etc/snort/snort/conf -i eth1

should be
snort -c /etc/snort/**snort.conf** -i eth1

```but when i eventually get both snort and barnyard running, i keep getting 
> 
WARNING: Can't extract timestamp extension from 'snort.log limit 128.1258055600'using base 'snort.log
when in the book it says...

> 
  Open a second CLI.
• ls -la /var/log/snort. Look for 10 digit suffix on snort.log. If there is more
  than one file, copy the latest one.
• vim /var/log/snort/barnyard.waldo
• Enter the following, then save and exit:
        • /var/log/snort
        • snort.log
        • <10 digit number from step 2 above>
        •0
• Start barnyard: /usr/local/bin/barnyard2 -c /etc/snort/barnyard2.conf -G
  /etc/snort/gen-msg.map -S /etc/snort/sid-msg.map -d /var/log/snort -f
  snort.log -w /var/log/snort/barnyard.waldo
and i see this...
```

root@michael-laptop:/home/michael# ls -la /var/log/snorttotal 24
drwxr-s---  2 snort snort 4096 2009-11-12 14:54 .
drwxr-xr-x 18 root  root  4096 2009-11-12 07:47 ..
-rw-r--r--  1   600 snort    0 2009-11-11 15:02 alert
-rw-r--r--  1 root  snort   38 2009-11-12 14:54 barnyard.waldo
-rw-r--r--  1 root  snort   38 2009-11-11 17:36 barnyard.waldo~
-rw-------  1 root  snort 5392 2009-11-12 14:56 snort.log limit 128.1258055600

```so I do this, 
```

root@michael-laptop:/home/michael# cat /var/log/snort/barnyard.waldo
/var/log/snort
snort.log
1258055600
0

```Can anyone help?

---

### Post by rkurti on 2009-11-16
Hi guys,
 
i was trying to install snort on Ubuntu 8.04 LST Server...but I am getting this error
 
[EMAIL="omerta@ssp:/etc/snort$"]omerta@ssp:/etc/snort$[/EMAIL] sudo apt-get install snort
Reading package lists... Done
Building dependency tree       
Reading state information... Done
snort is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
 
it says that it is installed...but there is nothing in the /etc/snort/ ... just a rules folder is no conf file or anything....nither in the init.d there is no snort
 
When I tried to remove it and installit again I got this:
 
[EMAIL="omerta@ssp:/etc/snort$"]omerta@ssp:/etc/snort$[/EMAIL] sudo apt-get remove snort
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  snort-rules-default snort-common libprelude2 snort-common-libraries libltdl3
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  snort
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
After this operation, 1057kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 23667 files and directories currently installed.)
Removing snort ...
invoke-rc.d: unknown initscript, /etc/init.d/snort not found.
dpkg: error processing snort (--remove):
 subprocess pre-removal script returned error exit status 100
postinst called with unknown argument `abort-remove'
Errors were encountered while processing:
 snort
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
Please could someone help me with this...cuz I need it for a school project which is due wendesday!
 
Thanks,
 
Rob

---

