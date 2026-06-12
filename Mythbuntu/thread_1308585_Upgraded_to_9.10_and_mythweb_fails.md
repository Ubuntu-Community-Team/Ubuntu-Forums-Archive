---
title: "Upgraded to 9.10 and mythweb fails"
date: 2009-10-31
forum: Mythbuntu
---

### Post by mrcidavies on 2009-10-31
A newbie and had 9.04 working fine. Took upgrade option to 9.10 and backend / frontend seems fine but mythweb I only get the following:

**Warning** at /usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/db_vars_error.php, line 23:
require(modules/_shared/tmpl/tmpl/header.php) [[function.require]("http://myth-server/mythweb/function.require")]: failed to open stream: No such file or directory
  
**Fatal error**:  require() [[function.require]("http://myth-server/mythweb/function.require")]: Failed opening required 'modules/_shared/tmpl/tmpl/header.php' (include_path='.:/usr/share/php:/usr/share/pear') in **/usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/db_vars_error.php** on line [B]23

[/B]Much Googling over past 48Hrs has come to nothing. Has anyone else seen this, know a fix, or how do you go back to 9.04. Hope its not re-install, again.

Thanks for any pointers as what I see in 9.10 looks far better than previous.

---

### Post by blackoper on 2009-11-01
try removing mythweb in package manager and then reinstalling, or remove all the myth stuff and then reinstall. I would think that would fix it. First I've ever seen this issue. If you have to, a full reinstall would fix.

---

### Post by Slate8 on 2009-11-01
I get a similar error on a clean 9.10 32-bit install:


Warning: require(modules/_shared/tmpl/tmpl/header.php) [function.require]: failed to open stream: No such file or directory in /usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/fatal.php on line 23

Fatal error: require() [function.require]: Failed opening required 'modules/_shared/tmpl/tmpl/header.php' (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/fatal.php on line 23

Any ideas?

---

### Post by xinix on 2009-11-01
I've had this error for a while too.  I posted asking for help on it but no answers yet.  I have even tried a clean install and no luck.

---

### Post by Lindsay.Mathieson on 2009-11-01
I believe its an issue with mythbackend and/or mysql listening on mismatched IP's, i.e localhost versus the public IP. If you've setup your mythbox so remote frontends can connect this is probably the problem.

Go into mytbuntu-control-centre, the MySQL Tab and enable the Master Backend Role. Then reboot.

---

### Post by maddojf on 2009-11-01
I had the same problem.  I went into the mythbuntu-control-center, clicked on the plugins tab, and enabled "Password Protect Mythweb".  It then took about a minute for the settings to be applied, and now mythweb is working.  

For what its worth, I am using a clean install of 9.10.  I backed up the database from my 9.04 installation and then restored it using the directions on the upgrade page of the mythbuntu wiki.  I have been having a number of problems with trying to migrate the database so this is the second time I have installed 9.10 today.  The last time I installed 9.10, mythweb was working fine (but that was before restoring the old database).  This time I didn't check mythweb until after I restored the database, so I can't be sure but it seems like restoring the old database is what caused the problem.  

To see what would happen, I then disabled the mythweb password and the pages loaded with a different error at the top of the page (something about timezone and php headers).  I then re-enabled the password and mythweb started working fine again.

Update: After a reboot another mythweb problem came up.  Again, going to the plugins tab of mythbuntu-control-center and clicking reconfigure in the mythweb password menu fixed the problem.

---

### Post by comptechgeek on 2009-11-02
I think I fixed the problem.  I ran sudo dpkg-reconfigure mythtv-common and when it asked for the address i put in the actual ip address and not leave it blank like it was.
Then i ran sudo dpkg-reconfigure mythweb .  Now mythweb loads correctly.

---

### Post by Slate8 on 2009-11-03
I have just run through every possible fix mentioned on this page but still get

```

Warning: require(modules/_shared/tmpl/tmpl/header.php) [function.require]: failed to open stream: No such file or directory in /usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/fatal.php on line 23

Fatal error: require() [function.require]: Failed opening required 'modules/_shared/tmpl/tmpl/header.php' (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/fatal.php on line 23
```


The line that errors is ```
require 'modules/_shared/tmpl/'.tmpl.'/header.php';
```

A bit stuck but will plough on. Really missing my mythweb :(

---

### Post by Slate8 on 2009-11-03
Just managed to get it working. In my case I commented out the offending line in

```
/usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/fatal.php

```

so it looks like 

```
 //require 'modules/_shared/tmpl/'.tmpl.'/header.php';
```

Then I checked mythweb again and received a more useful error about the table mythweb_sessions table already existing. So I when into my mythconverg database and dropped mythweb_sessions and everything started working.

No idea what went on there but happy I am up and running again. Hope this helps someone.

---

### Post by xinix on 2009-11-03
Ironically, after I edited the fatal.php file, mythweb was complaining that mythweb_sessions already existed!  I looked into the table with phpmyadmin and it gave me an error saying that the table uses an extension that is not in the current version of mysql.  I have no clue what that actually means, but I emptied all info from the table and it worked.  Well, sort of, then I got an error about mythweatherscreens not existing.  So I simply removed the module from the mythweb folder and all is good now.

---

### Post by tdiaz on 2009-11-04
I did a fresh install of Mythbuntu 9.10 and it was working fine .. 

Lost power on that box as it was not on it's UPS yet, and on reboot I get the same problem plus the two RAID containers setup with Palimpsest have problems. The RAID5 does not auto mount, I can see that - it wants to allow you to see all the partitions there first, but the RAID1 one, it's disassociated and it's container gone. 

I've always said software RIAD sucks. I guess it's karma.

---

### Post by tdiaz on 2009-11-04
Dropping the table, dropping the plugin .. do not work either, in this case.

---

### Post by writ on 2009-11-16
In my case, the bind-address variable in /etc/mysql/my.cnf and /etc/mysql/conf.d/mythtv.cnf were clobbered during the upgrade to 9.10. In both files, I set "bind-address" to the ip address of my myth server which resolved the problem for me.

After you make these changes, both files should have a line that looks like:

bind-address=192.168.0.211

Please let me know if this resolves the problem.

---

### Post by bblboy54 on 2009-11-19
> **writ said:**
> In my case, the bind-address variable in /etc/mysql/my.cnf and /etc/mysql/conf.d/mythtv.cnf were clobbered during the upgrade to 9.10. In both files, I set "bind-address" to the ip address of my myth server which resolved the problem for me.

After you make these changes, both files should have a line that looks like:

bind-address=192.168.0.211

Please let me know if this resolves the problem.

I tried this and now Mysql is refusing to start.  Tried changing back to 127.0.0.1 in my.cnf and 0.0.0.0 in mythtv.cnf but no luck.....  also, nothing showing up in log files

EDIT: actually, its possible that mysql hadn't been running in the first place.....  not sure why.  After my updated to 9.10 things seem to have gone bad.

---

### Post by bblboy54 on 2009-11-19
Just to update everyone, it seems my problem was simply that mysql wasn't loading.  The reason is that apparently if you do the dist-upgrade from command line mysql isn't properly upgraded to 5.1.  I solved this problem by doing:

apt-get install mysql-server-5.1 mysql-server-core-5.1

After that I changed the my.cnf file and replaced the bind address with my server's real IP as suggested above and everything seemed to work fine.

---

### Post by bakerjs on 2009-11-19
For me, this was solved simply by setting the mythweb password in Mythbuntu Control Centre (Plugins -> Password Protect Mythweb -> Enable).

---

### Post by PsyberS on 2009-12-04
> **bakerjs said:**
> For me, this was solved simply by setting the mythweb password in Mythbuntu Control Centre (Plugins -> Password Protect Mythweb -> Enable).

I can confirm this fix worked for me on a fresh install of 9.10.

---

### Post by MountainX on 2009-12-06
> **bakerjs said:**
> For me, this was solved simply by setting the mythweb password in Mythbuntu Control Centre (Plugins -> Password Protect Mythweb -> Enable).

worked for me without setting a password. I just ran dpkg reconfigure and it worked.

---

### Post by metu71 on 2009-12-11
Removing mythweb_sessions table helped for me. Thanks!

---

### Post by tickopa on 2009-12-26
> **Slate8 said:**
> Just managed to get it working. In my case I commented out the offending line in

```
/usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/fatal.php

```

so it looks like 

```
 //require 'modules/_shared/tmpl/'.tmpl.'/header.php';
```

Then I checked mythweb again and received a more useful error about the table mythweb_sessions table already existing. So I when into my mythconverg database and dropped mythweb_sessions and everything started working.

No idea what went on there but happy I am up and running again. Hope this helps someone.

Just wanted to say thank you Slate8. Saved me from reinstalling my fedora12 server.

My problem was my mythweb hostname declaration, it was set to 'localhost', changing this to '127.0.0.1' made it work. Damn! It's 3:26am :(

---

### Post by CaveMole on 2010-12-03
> **blackoper said:**
> try removing mythweb in package manager and then reinstalling, or remove all the myth stuff and then reinstall. I would think that would fix it. First I've ever seen this issue. If you have to, a full reinstall would fix.

I have the same problem.
re-install does not help.

---

### Post by mteppo on 2011-10-05
For me - the password was already set during the installation but this kept on coming. (Clean installation of 9.04LTS)
There is also Reconfigure option in the list (Mythbuntu Control Center - Plugins - Mythtv - Password Protect MythWeb).
Selecting that & setting the password again did the trick for me.

---

