---
title: "Mythweb broken after Upgrade .24fixes to .25 on LTS"
date: 2012-04-11
forum: Mythbuntu
---

### Post by dardack on 2012-04-11
I really need mythweb to be working.  1 of the main things I like about mythtv, i can set things up when I'm traveling.  Also would like to check out the new streaming stuff.  Here is error when I try to load the mythweb website:

```
Fatal Error

!!NoTrans: Lost connection to MySQL server at 'reading initial communication packet', system error: 110 [#2013]

Backtrace
Array
(
[0] => Array
(
[file] => /usr/share/mythtv/mythweb/classes/Database/Query/mysql.php
[line] => 63
[function] => error
[class] => Database
[object] => Database_mysql Object
(
[dbh] => 
[error] => Lost connection to MySQL server at 'reading initial communication packet', system error: 110 [#2013]
[err] => Lost connection to MySQL server at 'reading initial communication packet', system error: 110
[errno] => 2013
[last_sh] => Database_Query_mysql Object
(
[dbh] => 
[query] => Array
(
[0] => SET NAMES utf8;
)

[last_query] => SET NAMES utf8;
[warnings] => Array
(
)

[num_args_needed] => 0
[num_rows] => 
[affected_rows] => 
[insert_id] => 
[db] => Database_mysql Object
*RECURSION*
)

[fatal_errors] => 1
[query_count] => 0
[query_time] => 0
[global_name] => 
[destruct_handlers] => Array
(
)

)

[type] => ->
[args] => Array
(
)

)

[1] => Array
(
[file] => /usr/share/mythtv/mythweb/classes/Database.php
[line] => 259
[function] => execute
[class] => Database_Query_mysql
[object] => Database_Query_mysql Object
(
[dbh] => 
[query] => Array
(
[0] => SET NAMES utf8;
)

[last_query] => SET NAMES utf8;
[warnings] => Array
(
)

[num_args_needed] => 0
[num_rows] => 
[affected_rows] => 
[insert_id] => 
[db] => Database_mysql Object
(
[dbh] => 
[error] => Lost connection to MySQL server at 'reading initial communication packet', system error: 110 [#2013]
[err] => Lost connection to MySQL server at 'reading initial communication packet', system error: 110
[errno] => 2013
[last_sh] => Database_Query_mysql Object
*RECURSION*
[fatal_errors] => 1
[query_count] => 0
[query_time] => 0
[global_name] => 
[destruct_handlers] => Array
(
)

)

)

[type] => ->
[args] => Array
(
[0] => Array
(
)

)

)

[2] => Array
(
[file] => /usr/share/mythtv/mythweb/classes/Database.php
[line] => 124
[function] => query
[class] => Database
[object] => Database_mysql Object
(
[dbh] => 
[error] => Lost connection to MySQL server at 'reading initial communication packet', system error: 110 [#2013]
[err] => Lost connection to MySQL server at 'reading initial communication packet', system error: 110
[errno] => 2013
[last_sh] => Database_Query_mysql Object
(
[dbh] => 
[query] => Array
(
[0] => SET NAMES utf8;
)

[last_query] => SET NAMES utf8;
[warnings] => Array
(
)

[num_args_needed] => 0
[num_rows] => 
[affected_rows] => 
[insert_id] => 
[db] => Database_mysql Object
*RECURSION*
)

[fatal_errors] => 1
[query_count] => 0
[query_time] => 0
[global_name] => 
[destruct_handlers] => Array
(
)

)

[type] => ->
[args] => Array
(
[0] => SET NAMES utf8;
)

)

[3] => Array
(
[file] => /usr/share/mythtv/mythweb/includes/database.php
[line] => 49
[function] => connect
[class] => Database
[type] => ::
[args] => Array
(
[0] => mythconverg
[1] => mythtv
[2] => mythtv
[3] => 192.168.10.106
[4] => 
[5] => mysql
)

)

[4] => Array
(
[file] => /usr/share/mythtv/mythweb/includes/init.php
[line] => 40
[args] => Array
(
[0] => /usr/share/mythtv/mythweb/includes/database.php
)

[function] => require_once
)

[5] => Array
(
[file] => /usr/share/mythtv/mythweb/mythweb.php
[line] => 20
[args] => Array
(
[0] => /usr/share/mythtv/mythweb/includes/init.php
)

[function] => require_once
)

)
!!
```

---

### Post by tgm4883 on 2012-04-11
We're going to need a bit more info. Does the mythbackend.log file have anything of importance? What do you mean you upgraded from .24fixes to 0.25 on LTS? Do you mean 10.04 or 12.04? Are you running the latest build of 0.25?

---

### Post by dardack on 2012-04-11
> **tgm4883 said:**
> We're going to need a bit more info. Does the mythbackend.log file have anything of importance? What do you mean you upgraded from .24fixes to 0.25 on LTS? Do you mean 10.04 or 12.04? Are you running the latest build of 0.25?

10.04, hasn't given me the option to upgrade to 12.04 yet, but I think I will.  It did do a partial upgrade when upgrading to .25.

I assume latest.  I use the mythbuntu-repos.  I did a dpkg-reconfigure, selected .25 instead of .24fixes, ran update-manager, clicked check, ran update.  Did a partial upgrade, then updated.  I then did a check again, and nothing new came up.

Um either power is out at my home or my wife turned off my main computer, cause I can't VNC into it right now.  Once I can i'll let you know what the backend log says.

Took me awhile to get the backend to properly start on reboot.  Apparently my mythtv-backend.conf was using the -logfile flag which is depreciated and now uses syslog flag.  So not 100% sure where this log is now.

---

### Post by rhpot1991 on 2012-04-11
I may be confusing the wording of "Partial Upgrade."

Here is what I would try: sudo apt-get update && sudo apt-get dist-upgrade

Run that and make sure it pulls all the new mythtv packages.  Then check mythweb again.  I don't see this issue on my 0.25 box.

---

### Post by twyt88 on 2012-04-11
> **dardack said:**
> 10.04, hasn't given me the option to upgrade to 12.04 yet, but I think I will.  It did do a partial upgrade when upgrading to .25.

I assume latest.  I use the mythbuntu-repos.  I did a dpkg-reconfigure, selected .25 instead of .24fixes, ran update-manager, clicked check, ran update.  Did a partial upgrade, then updated.  I then did a check again, and nothing new came up.

Um either power is out at my home or my wife turned off my main computer, cause I can't VNC into it right now.  Once I can i'll let you know what the backend log says.

Took me awhile to get the backend to properly start on reboot.  Apparently my mythtv-backend.conf was using the -logfile flag which is depreciated and now uses syslog flag.  So not 100% sure where this log is now.

Sounded like you are trying to upgrade whilst you are away. That's pretty brave. ;)

I'd suggest you should upgrade to latest ubuntu then use the repos. Ubuntu release might includes some gcc libraries upgrade that repos might not have. Release notes ([http://www.mythtv.org/wiki/Release_Notes_-_0.25](http://www.mythtv.org/wiki/Release_Notes_-_0.25)) would have a bunch of pre-requsites that needs to be met and older ubuntu release might not have them.

Try to go back to a known state, ie revert to mythtv 0.24, then upgrade your ubuntu to the latest stable release, which is 11.10. You might have to deal with different pain before you upgrade mythtv 0.25. For me I had some issues after upgrading to 11.10 because the Lirc drivers had changed, but that's another story.

FYI, syslogs should be ouputed /var/log/syslog

---

### Post by dardack on 2012-04-11
> **twyt88 said:**
> Sounded like you are trying to upgrade whilst you are away. That's pretty brave. ;)

I'd suggest you should upgrade to latest ubuntu then use the repos. Ubuntu release might includes some gcc libraries upgrade that repos might not have. Release notes ([http://www.mythtv.org/wiki/Release_Notes_-_0.25](http://www.mythtv.org/wiki/Release_Notes_-_0.25)) would have a bunch of pre-requsites that needs to be met and older ubuntu release might not have them.

Try to go back to a known state, ie revert to mythtv 0.24, then upgrade your ubuntu to the latest stable release, which is 11.10. You might have to deal with different pain before you upgrade mythtv 0.25. For me I had some issues after upgrading to 11.10 because the Lirc drivers had changed, but that's another story.

FYI, syslogs should be ouputed /var/log/syslog


Nah I was home yesterday.  Upgraded.  Backend works, frontend in living room/bed room work.  Video's/Recordings work.

Try to access mythweb today, not working.

I'll upgrade to 12.04 once mythbuntu releases 12.04.  I stick to LTS for my backend/server.  No way am I upgrading every 6 months.  Plus Mythbuntu is going to LTS only.

---

### Post by dardack on 2012-04-11
> **rhpot1991 said:**
> I may be confusing the wording of "Partial Upgrade."

Here is what I would try: sudo apt-get update && sudo apt-get dist-upgrade

Run that and make sure it pulls all the new mythtv packages.  Then check mythweb again.  I don't see this issue on my 0.25 box.

Yea no one else seems to be having my exact problem.  I don't want to upgrade to non LTS.

SOmehow mythweb isn't communicating with Mysql and I don't know why or how to check.

I know the Mythbuntu control centre, when I click test connection on mysql tab, it fails.  But both my frontends connect fine.

Also, mythweb is being run from the backend server.  I really hope I don't have to do a fresh install.

---

### Post by dardack on 2012-04-11
OK BTW mythweb does ask for my username/password.  Once put in, now i'm getting 113 instead of 110:

Fatal Error

!!NoTrans: Lost connection to MySQL server at 'reading initial communication packet', system error: 113 [#2013]

Backtrace
Array
(
[0] => Array
(
[file] => /usr/share/mythtv/mythweb/classes/Database/Query/mysql.php
[line] => 63
[function] => error
[class] => Database
[object] => Database_mysql Object
(
[dbh] => 
[error] => Lost connection to MySQL server at 'reading initial communication packet', system error: 113 [#2013]
[err] => Lost connection to MySQL server at 'reading initial communication packet', system error: 113

---

### Post by dardack on 2012-04-11
OK let's say I can wait until 12.04 Mythbuntu is released (should be soon).  Let's say I do a full reinstall.

How would I keep all my database stuff so I can still watch recorded stuff that is previous recorded and such.

---

### Post by tgm4883 on 2012-04-11
> **dardack said:**
> OK let's say I can wait until 12.04 Mythbuntu is released (should be soon).  Let's say I do a full reinstall.

How would I keep all my database stuff so I can still watch recorded stuff that is previous recorded and such.

Did you do the "sudo apt-get update && sudo apt-get dist-upgrade"? That doesn't upgrade the distro, just allows the installation of any additional packages that are necessary.

If that doesn't resolve the issue, have you attempted "sudo apt-get purge mythweb" then reinstalling mythweb?

---

### Post by dardack on 2012-04-11
> **tgm4883 said:**
> Did you do the "sudo apt-get update && sudo apt-get dist-upgrade"? That doesn't upgrade the distro, just allows the installation of any additional packages that are necessary.

If that doesn't resolve the issue, have you attempted "sudo apt-get purge mythweb" then reinstalling mythweb?

Oh, ok I'll try that.

---

### Post by dardack on 2012-04-11
Neither of those fixed the problem.  

I verified that the directory /usr/share/mythtv/mythweb was deleted on purge.  Then reinstalled, mythweb reappears.

Same exact error.

---

### Post by tgm4883 on 2012-04-11
> **dardack said:**
> Neither of those fixed the problem.  

I verified that the directory /usr/share/mythtv/mythweb was deleted on purge.  Then reinstalled, mythweb reappears.

Same exact error.

what is the output of 
```
dpkg -l myth*
```

---

### Post by nickrout on 2012-04-11
> **dardack said:**
> OK let's say I can wait until 12.04 Mythbuntu is released (should be soon).  Let's say I do a full reinstall.

How would I keep all my database stuff so I can still watch recorded stuff that is previous recorded and such.

By backing it up and then restoring it into the new install:

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

---

### Post by dardack on 2012-04-12
> **tgm4883 said:**
> what is the output of 
```
dpkg -l myth*
```

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                       Version                                            Description
+++-==========================================-==================================================-============================================
un  mythappearance                             <none>                                             (no description available)
un  mytharchive                                <none>                                             (no description available)
un  mytharchive-data                           <none>                                             (no description available)
un  mythbrowser                                <none>                                             (no description available)
un  mythbuntu-artwork-usplash                  <none>                                             (no description available)
ii  mythbuntu-common                           0.50-0ubuntu1                                      Mythbuntu application support functions
ii  mythbuntu-control-centre                   0.62-0ubuntu1                                      Mythbuntu Configuration Application
ii  mythbuntu-default-settings                 0.96-0ubuntu1                                      default settings for Mythbuntu
un  mythbuntu-desktop                          <none>                                             (no description available)
ii  mythbuntu-gdm-theme                        0.6-0ubuntu1                                       Mythbuntu GDM theme
ii  mythbuntu-lirc-generator                   0.25-0ubuntu1~ppa1                                 Mythbuntu Lirc Configuration Generator
un  mythbuntu-live                             <none>                                             (no description available)
un  mythbuntu-live-autostart                   <none>                                             (no description available)
rc  mythbuntu-log-grabber                      0.5-0ubuntu1                                       Tool to gather diagnostic data for Mythbuntu
ii  mythbuntu-repos                            9.3-0ubuntu0+mythbuntu~auto20110703002111          Mythbuntu repository installer
un  mythbuntu-testing                          <none>                                             (no description available)
un  mythbuntu-weekly                           <none>                                             (no description available)
un  mythcontrols                               <none>                                             (no description available)
un  mythdvd                                    <none>                                             (no description available)
un  mythflix                                   <none>                                             (no description available)
un  mythgallery                                <none>                                             (no description available)
un  mythgame                                   <none>                                             (no description available)
un  mythmovies                                 <none>                                             (no description available)
un  mythmusic                                  <none>                                             (no description available)
un  mythnetvision                              <none>                                             (no description available)
un  mythnews                                   <none>                                             (no description available)
un  mythphone                                  <none>                                             (no description available)
un  mythplugins                                <none>                                             (no description available)
un  mythstream                                 <none>                                             (no description available)
un  mythtv                                     <none>                                             (no description available)
ii  mythtv-backend                             2:0.25.0+fixes.20120410.1f5962a-0ubuntu0mythbuntu1 A personal video recorder application (serve
ii  mythtv-backend-master                      2:0.25.0+fixes.20120410.1f5962a-0ubuntu0mythbuntu1 Metapackage to setup and configure a "Master
ii  mythtv-common                              2:0.25.0+fixes.20120410.1f5962a-0ubuntu0mythbuntu1 A personal video recorder application (commo
ii  mythtv-database                            2:0.25.0+fixes.20120410.1f5962a-0ubuntu0mythbuntu1 A personal video recorder application (datab
un  mythtv-doc                                 <none>                                             (no description available)
ii  mythtv-frontend                            2:0.25.0+fixes.20120410.1f5962a-0ubuntu0mythbuntu1 A personal video recorder application (clien
un  mythtv-theme-arclight                      <none>                                             (no description available)
un  mythtv-theme-blootube                      <none>                                             (no description available)
un  mythtv-theme-blootube-osd                  <none>                                             (no description available)
un  mythtv-theme-blootube-wide                 <none>                                             (no description available)
un  mythtv-theme-blootubelite-wide             <none>                                             (no description available)
un  mythtv-theme-blueosd                       <none>                                             (no description available)
un  mythtv-theme-childish                      <none>                                             (no description available)
un  mythtv-theme-glass-wide                    <none>                                             (no description available)
un  mythtv-theme-graphite                      <none>                                             (no description available)
un  mythtv-theme-gray-osd                      <none>                                             (no description available)
un  mythtv-theme-isthmus                       <none>                                             (no description available)
un  mythtv-theme-iulius                        <none>                                             (no description available)
un  mythtv-theme-iulius-osd                    <none>                                             (no description available)
un  mythtv-theme-metallurgy                    <none>                                             (no description available)
un  mythtv-theme-metallurgy-osd                <none>                                             (no description available)
un  mythtv-theme-metallurgy-wide               <none>                                             (no description available)
un  mythtv-theme-minimalist-wide               <none>                                             (no description available)
un  mythtv-theme-mono-osd                      <none>                                             (no description available)
rc  mythtv-theme-mythbuntu                     2:0.23.0+fixes25253-0ubuntu1                       The mythbuntu MythTV Theme
un  mythtv-theme-mythcenter                    <none>                                             (no description available)
un  mythtv-theme-mythcenter-wide               <none>                                             (no description available)
un  mythtv-theme-neon-wide                     <none>                                             (no description available)
un  mythtv-theme-proejctgrayhem-wide           <none>                                             (no description available)
un  mythtv-theme-projectgrayhem                <none>                                             (no description available)
un  mythtv-theme-projectgrayhem-osd            <none>                                             (no description available)
un  mythtv-theme-projectgrayhem-wide           <none>                                             (no description available)
un  mythtv-theme-retro                         <none>                                             (no description available)
un  mythtv-theme-retro-osd                     <none>                                             (no description available)
un  mythtv-theme-titivillus                    <none>                                             (no description available)
un  mythtv-theme-titivillus-osd                <none>                                             (no description available)
un  mythtv-themes                              <none>                                             (no description available)
ii  mythtv-transcode-utils                     2:0.25.0+fixes.20120410.1f5962a-0ubuntu0mythbuntu1 Utilities used for transcoding MythTV tasks
rc  mythvideo                                  2:0.24.2+fixes.20120316.322de47-0ubuntu0mythbuntu1 A generic video player frontend module for M
un  mythweather                                <none>                                             (no description available)
ii  mythweb                                    2:0.25.0+fixes.20120410.1f5962a-0ubuntu0mythbuntu1 Web interface add-on module for MythTV
```

---

### Post by dkgiles on 2012-04-29
I had this same problem, which was fixed by removing and reinstalling mythweb.  No other changes necessary.
 
sudo apt-get remove mythweb
sudo apt-get install mythweb
 
Cheers.

---

### Post by speedbacon on 2012-05-15
Similar problem here, but removing and re-adding didn't help.  My problem was that my hosts file got corrupted somehow and the hostname of the mysql server was invalid.

---

### Post by mortys on 2012-06-22
Just to add another possible solution, i got to similar situation with same error when i did some changes in configuration of ip address of myth-backend / myth-frontend. I solved the problem editing configuration file of MySQL database. I had to open /etc/mysql/my.cnf and change bind-address from 127.0.0.1 to 10.0.0.35 (IP address of backend in my LAN network). After restart of mysql and myth-backend service everything worked.

---

### Post by dannyboy79 on 2013-04-17
> **mortys said:**
> Just to add another possible solution, i got to similar situation with same error when i did some changes in configuration of ip address of myth-backend / myth-frontend. I solved the problem editing configuration file of MySQL database. I had to open /etc/mysql/my.cnf and change bind-address from 127.0.0.1 to 10.0.0.35 (IP address of backend in my LAN network). After restart of mysql and myth-backend service everything worked.
this solution worked for me as well. although my thumbnails in mythweb are still very slow to show up if at all. i am still investigating that issue

---

### Post by tgm4883 on 2013-04-18
Please open a new thread if the thread you want to post to is over 6 months old (from the last post)

---

