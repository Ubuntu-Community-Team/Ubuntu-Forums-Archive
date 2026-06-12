---
title: "Apache not running on MythBuntu"
date: 2014-05-08
forum: Mythbuntu
---

### Post by holmz2 on 2014-05-08
Everything did seem fine... but now no mythweb.
The local host (127.0.0.1) is _**not **_running on the local box and
ps -ef | grep -i Apach
shows nothing...

Here is what happens when I try to startup apache2:

[FONT=Menlo]***user0@lbmc:/etc/apache2/sites-available$ sudo /etc/init.d/apache2 restart***[/FONT]
[FONT=Menlo]***apache2: Syntax error on line 234 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/conf.d/zoneminder.conf: No such file or directory***[/FONT]
[FONT=Menlo]***Action 'configtest' failed.***[/FONT]
[FONT=Menlo]***The Apache error log may have more information.***[/FONT]


Files are:
[B]_/etc/apache2.conf_[I]
...
# Include generic snippets of statements[/I][/B]
[B][I]Include conf.d/   #                                         <-line 234


[/I][/B]
[FONT=Menlo]user0@lbmc:/etc/apache2$ pwd[/FONT]
[FONT=Menlo]/etc/apache2
[/FONT][FONT=Menlo]user0@lbmc:/etc/apache2$ ls -lstar conf.d/[/FONT]
[FONT=Menlo]total 40[/FONT]
[FONT=Menlo] 4 -rw-r--r-- 1 root root 1424 Feb  7  2012 security[/FONT]
[FONT=Menlo] 4 -rw-r--r-- 1 root root  143 Feb  7  2012 other-vhosts-access-log[/FONT]
[FONT=Menlo] 4 -rw-r--r-- 1 root root 3296 Feb  7  2012 localized-error-pages[/FONT]
[FONT=Menlo] 4 -rw-r--r-- 1 root root  269 Feb  7  2012 charset[/FONT]
[FONT=Menlo] 0 lrwxrwxrwx 1 root root   19 May 22  2013 [COLOR=#991200]**zoneminder.conf**[/COLOR] -> [COLOR=#991200]**/etc/zm/apache.conf**[/COLOR][/FONT]
[FONT=Menlo] 0 lrwxrwxrwx 1 root root   45 May 22  2013 [COLOR=#34bbc7]**javascript-common.conf**[/COLOR] -> /etc/javascript-common/javascript-common.conf[/FONT]
[FONT=Menlo] 4 -rw-r--r-- 1 root root  237 Mar 20 06:41 apache2-doc[/FONT]
[FONT=Menlo]12 -rw-r--r-- 1 root root 9738 Apr 16 11:35 mythweb.conf[/FONT]
[FONT=Menlo] 4 drwxr-xr-x 7 root root 4096 May  8 15:45 [COLOR=#5330e1]**..**[/COLOR][/FONT]
[FONT=Menlo] 4 drwxr-xr-x 2 root root 4096 May  8 15:45 [COLOR=#5330e1][B].

[/B][/COLOR]
[FONT=Verdana]The /etc/zm/apache.conf is non existent:[/FONT][/FONT]
[FONT=Menlo] 0 lrwxrwxrwx 1 root root   19 May 22  2013 [COLOR=#991200]**zoneminder.conf**[/COLOR] -> [COLOR=#991200][B]/etc/zm/apache.conf

[/B][/COLOR][/FONT]
[FONT=Menlo]user0@lbmc:/etc/apache2$ ls -lstar /etc/zm[/FONT]
[FONT=Menlo]ls: cannot access /etc/zm: No such file or directory[/FONT]

[FONT=Menlo]Not sure how it is hosed, or if I am on the right track here...[/FONT]

---

### Post by blm-ubunet on 2014-05-08
[FONT=Menlo]Syntax error on line 234 of /etc/apache2/apache2.conf

Delete the broken symlink:
rm /etc/apache2/conf.d/zoneminder.conf[/FONT]

You should be using:
sudo service apache2 restart

---

### Post by holmz2 on 2014-05-09
Thanks. It is back up now.

It showed the following, so I probably have a bit more to do. The DHCP takes place from the modem, with most the other devices using manual (computers, printers, VoIP - and the linux box on DHCP with the iPads. But that the myth box 127.0.0.1 is internal. And the iPad is showing the myth web now. ;)

[FONT=Menlo]***user0@lbmc:/etc/apache2/conf.d$ sudo service apache2 restart***[/FONT]
[FONT=Menlo]*** * Restarting web server apache2                                                                                                                           apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName***[/FONT]
[FONT=Menlo]***apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName***

So I probably do not need to worry about that if I am using the myth box mostly, and the iPad and computer for scheduling and pulling back the movies over the gig-e.

I appreciate your input.[/FONT]

---

### Post by dannyboy79 on 2014-05-10
unless you're accessing your webserver from outside your LAN that error is fine, i get the same error.

---

