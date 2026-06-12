---
title: "Mythexport/Apache unable to find database"
date: 2009-12-19
forum: Mythbuntu
---

### Post by bb_145 on 2009-12-19
Hi,

I've been running Mythbuntu 8.10 (installed on Xbuntu) on a system with a combined front/backend for the better part of a year, but recently tried to install Mythexport.  The installation seemed to go OK, but when I try to access the web interface, I get the 500 configuration error.  I checked the Apache log, and it says "No Backend found.  Please copy /var/www/.mythtv/config.xml from a working MythTV installation."  However, since I have a working frontend on this computer, shouldn't the config.xml file be correct?  Here is the file:

```
<Configuration>
&#8722;
<UPnP>
&#8722;
<MythFrontend>
&#8722;
<DefaultBackend>
<DBHostName>localhost</DBHostName>
<DBUserName>mythtv</DBUserName>
<DBPassword>{random letters and numbers}</DBPassword>
<DBName>mythconverg</DBName>
<DBPort>0</DBPort>
</DefaultBackend>
</MythFrontend>
&#8722;
<UDN> 
```

As far as I can tell, it matches others I've found on the web.  The only hint I can think of is that I've looked in the mythweb configuration file (which works fine), and it seems to use a password of "mythtv".  However, I'm worried if I change the password in the config.xml file, it will mess up my frontend.  Any suggestions?  I don't know enough about linux/ubuntu to know if I'm on the right track.

Thanks in advance.

---

### Post by rhpot1991 on 2009-12-19
Fist thing you should check is if /etc/mythtv/mysql.txt and /etc/mythtv/config.xml have matching usernames and passwords.  If not figure out which one is correct and update the other.  If they match then go ahead and run `locate config.xml`, check all the config.xml files to make sure they all match.

---

### Post by bb_145 on 2009-12-21
Thanks!  Though no luck yet.  The two files matched.  Here is the result of the locate

```
greg@greg-laptop:/home$ locate config.xml
/etc/mythtv/config.xml
/home/greg/.mythtv/config.xml
/home/mythtv/.mythtv/config.xml
/root/.mythtv/config.xml
/usr/share/doc/mythtv-backend/contrib/config.xml
/usr/share/mythtv/config.xml
```

The passwords in the last two didn't match the rest.  I've changed the last one, and it didn't seem to have an effect on anything.

I took a look in the folder that the Apache log said it was looking in, and it appears to be a syslink (just learning about those).  I've attached the directory listing.

```
greg@greg-laptop:/var/www$ ls -ali
total 12
3736137 drwxr-xr-x  2 root root 4096 2009-12-19 08:57 .
3678209 drwxr-xr-x 16 root root 4096 2009-02-10 21:37 ..
3736198 -rw-r--r--  1 root root   53 2009-04-06 19:58 index.html
3736261 lrwxrwxrwx  1 root root   28 2009-12-19 08:57 mythexport -> /usr/share/mythtv/mythexport
3736260 lrwxrwxrwx  1 root root   13 2009-12-19 08:57 .mythtv -> /root/.mythtv
3736195 lrwxrwxrwx  1 root root   25 2009-02-10 21:37 mythweb -> /usr/share/mythtv/mythweb
```

Is this OK?  Do I need to worry about the permissions?

Thanks in advance.

---

### Post by rhpot1991 on 2009-12-21
> **bb_145 said:**
> Thanks!  Though no luck yet.  The two files matched.  Here is the result of the locate

```
greg@greg-laptop:/home$ locate config.xml
/etc/mythtv/config.xml
/home/greg/.mythtv/config.xml
/home/mythtv/.mythtv/config.xml
/root/.mythtv/config.xml
/usr/share/doc/mythtv-backend/contrib/config.xml
/usr/share/mythtv/config.xml
```

The passwords in the last two didn't match the rest.  I've changed the last one, and it didn't seem to have an effect on anything.

I took a look in the folder that the Apache log said it was looking in, and it appears to be a syslink (just learning about those).  I've attached the directory listing.

```
greg@greg-laptop:/var/www$ ls -ali
total 12
3736137 drwxr-xr-x  2 root root 4096 2009-12-19 08:57 .
3678209 drwxr-xr-x 16 root root 4096 2009-02-10 21:37 ..
3736198 -rw-r--r--  1 root root   53 2009-04-06 19:58 index.html
3736261 lrwxrwxrwx  1 root root   28 2009-12-19 08:57 mythexport -> /usr/share/mythtv/mythexport
3736260 lrwxrwxrwx  1 root root   13 2009-12-19 08:57 .mythtv -> /root/.mythtv
3736195 lrwxrwxrwx  1 root root   25 2009-02-10 21:37 mythweb -> /usr/share/mythtv/mythweb
```

Is this OK?  Do I need to worry about the permissions?

Thanks in advance.

The error you are seeing indicates that there is an issue communicating with your backend, is it running properly?  If so then it should be a config.xml issue.  Have you rebooted since modifying the files?  I'd do that to make sure you give everything a fresh chance to start up.  You are running Karmic?

---

### Post by bb_145 on 2009-12-22
Thanks again for your help.  I've been poking around some more, but I'm still at a loss.  I'm running Xbuntu 8.10, and as far as I know the backend is working fine.  (I can access it with the frontend on the same machine, and through mythweb).

I took another look at the apache log, and it says it can't find the config file:

```
[Tue Dec 22 13:22:34 2009] [error] [client 192.168.2.11] No config found; attempting to find mythbackend via UPnP.
[Tue Dec 22 13:22:38 2009] [error] [client 192.168.2.11] No backends found.  Please copy /var/www/.mythtv/config.xml from a working MythTV installation instead.
[Tue Dec 22 13:22:38 2009] [error] [client 192.168.2.11] Compilation failed in require at /var/www/mythexport/mythexportRSS.cgi line 4.
[Tue Dec 22 13:22:38 2009] [error] [client 192.168.2.11] BEGIN failed--compilation aborted at /var/www/mythexport/mythexportRSS.cgi line 4.
[Tue Dec 22 13:22:38 2009] [error] [client 192.168.2.11] Premature end of script headers: mythexportRSS.cgi
[Tue Dec 22 13:22:38 2009] [error] [client 192.168.2.11] File does not exist: /var/www/favicon.ico
```

I've looked in /var/www/.mythtv/config.xml, which I only just realized is a syslink to /root/.mythtv/config.xml, which is in turn a syslink to /etc/mythtv/config.xml.  

```
greg@greg-laptop:/etc/mythtv$ ls -ali
total 48
5072947 drwxr-xr-x   2 root   root      4096 2009-12-22 13:21 .
5070849 drwxr-xr-x 137 root   root     12288 2009-12-22 08:28 ..
3031092 -rw-rw----   1 mythtv mythtv     422 2009-12-22 08:35 config.xml
3031091 -rw-rw----   1 mythtv mythtv    1123 2009-04-06 19:58 mysql.txt
5073232 -rw-r--r--   1 root   root        32 2009-12-22 13:21 mythexport.cfg
5073114 -rw-r--r--   1 root   root      1990 2009-04-03 00:05 mythweb-canned_searches.conf.php
5073113 -rw-r--r--   1 root   root      4731 2009-04-03 00:05 mythweb-config.php
5071375 -rw-r-----   1 mythtv www-data    47 2009-04-06 19:58 mythweb-digest
5073102 -rw-r--r--   1 root   root      1110 2009-04-02 23:08 session-settings

```

and as far as I can tell, the config.xml file in this folder is correct.  So either the program is looking somewhere else, or it can't access the file for some reason???

One thing I don't understand is that when I do a locate, it finds the config.xml file in the /root/.mythtv folder, but not the /var/www/.mythtv/config.xml.

```
greg@greg-laptop:/root/.mythtv$ locate config.xml
/etc/bonobo-activation/bonobo-activation-config.xml
/etc/mythtv/config.xml
/home/greg/.config/xfce4/mixer/config.xml
/home/greg/.mythtv/config.xml
/home/mythtv/.mythtv/config.xml
/root/.mythtv/config.xml
/usr/share/doc/mythtv-backend/contrib/config.xml
/usr/share/mythtv/config.xml

```


Any suggestions would be appreciated.  Thanks in advance.

---

### Post by bb_145 on 2009-12-23
Still at a loss.  I've replaces the syslink with a copy of the actual config.xml file in the var/www/.mythtv directory, and it still says no config found.  I also tried changing the owner to mythtv.

Apache error log:
```
[Wed Dec 23 18:12:23 2009] [error] [client 192.168.2.11] No config found; attempting to find mythbackend via UPnP.
[Wed Dec 23 18:12:27 2009] [error] [client 192.168.2.11] No backends found.  Please copy /var/www/.mythtv/config.xml from a working MythTV installation instead.
[Wed Dec 23 18:12:27 2009] [error] [client 192.168.2.11] Compilation failed in require at /var/www/mythexport/mythexportRSS.cgi line 4.
[Wed Dec 23 18:12:27 2009] [error] [client 192.168.2.11] BEGIN failed--compilation aborted at /var/www/mythexport/mythexportRSS.cgi line 4.
[Wed Dec 23 18:12:27 2009] [error] [client 192.168.2.11] Premature end of script headers: mythexportRSS.cgi
[Wed Dec 23 18:12:27 2009] [error] [client 192.168.2.11] File does not exist: /var/www/favicon.ico

```

New directory listing of /var/www/.mythtv.
```
greg@greg-laptop:/var/www/.mythtv$ ls -ali
total 12
3736221 drwxr-xr-x 2 root   root   4096 2009-12-23 18:02 .
3736137 drwxr-xr-x 3 root   root   4096 2009-12-23 18:00 ..
1949707 -rw-r----- 1 mythtv mythtv  422 2009-12-23 18:02 config.xml

```

Could it be looking in a different place?

Thanks.

---

### Post by bb_145 on 2010-04-04
I think I finally got it working.  It appears to have been mostly a permission issue.  I updated to 10.4, and I had to allow write permissions for the config.xml file and the save_setup.cgi file.

```
chmod 777 /var/www/.mythtv/config.xml
```

and

```
 chmod 777 /var/www/mythexport/save_setup.cgi 
```

I can now access the interface and save the configuration files.

---

