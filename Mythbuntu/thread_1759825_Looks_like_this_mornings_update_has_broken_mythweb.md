---
title: "Looks like this mornings update has broken mythweb."
date: 2011-05-16
forum: Mythbuntu
---

### Post by SteveGodfrey on 2011-05-16
Mythweb working perfectly until I did an apt-get update/upgrade early this morning. 

I get access the main mythweb page but when I click on a programme in the guide the option to record has gone and I see this error at the top of the page.

```
Warning at /usr/share/mythtv/mythweb/modules/tv/detail.php, line 310:
!!NoTrans: Invalid argument supplied for foreach()!!

Warning at /usr/share/mythtv/mythweb/modules/_shared/tmpl/default/header.php, line 16:
!!NoTrans: Cannot modify header information - headers already sent by (output started at /usr/share/mythtv/mythweb/includes/errors.php:150)!!
```

Seems the problem is caused by an old version of MythBackend.php but there's only one on my system!

```

user@NAS:/usr/share/mythtv/mythweb/classes$ aptitude show mythweb
Package: mythweb
State: installed
Automatically installed: no
Version: 2:0.24.0+fixes.20110516.b5a3805-0ubuntu0mythbuntu1
Priority: optional
Section: graphics
Maintainer: MythTV Ubuntu Maintainers <ubuntu-mythtv@lists.ubuntu.com>
Uncompressed Size: 6,627k
Depends: mythtv-common (>= 2:0.24.0+fixes.20110516.b5a3805-0ubuntu0mythbuntu1), apache2-mpm-prefork | httpd, php5 |
         libapache2-mod-php5, php5-mysql, debconf (>= 0.5) | debconf-2.0
Recommends: libmath-round-perl
Description: Web interface add-on module for MythTV
 MythWeb provides a web interface which can be used to view listings, schedule recordings, delete recordings, and search
 for programs. It can also browse mythmusic's music database, and may eventually support playing music streams as well.

```

---

### Post by tgm4883 on 2011-05-16
> **SteveGodfrey said:**
> Mythweb working perfectly until I did an apt-get update/upgrade early this morning. 

I get access the main mythweb page but when I click on a programme in the guide the option to record has gone and I see this error at the top of the page.

```
Warning at /usr/share/mythtv/mythweb/modules/tv/detail.php, line 310:
!!NoTrans: Invalid argument supplied for foreach()!!

Warning at /usr/share/mythtv/mythweb/modules/_shared/tmpl/default/header.php, line 16:
!!NoTrans: Cannot modify header information - headers already sent by (output started at /usr/share/mythtv/mythweb/includes/errors.php:150)!!
```

Seems the problem is caused by an old version of MythBackend.php but there's only one on my system!

```

user@NAS:/usr/share/mythtv/mythweb/classes$ aptitude show mythweb
Package: mythweb
State: installed
Automatically installed: no
Version: 2:0.24.0+fixes.20110516.b5a3805-0ubuntu0mythbuntu1
Priority: optional
Section: graphics
Maintainer: MythTV Ubuntu Maintainers <ubuntu-mythtv@lists.ubuntu.com>
Uncompressed Size: 6,627k
Depends: mythtv-common (>= 2:0.24.0+fixes.20110516.b5a3805-0ubuntu0mythbuntu1), apache2-mpm-prefork | httpd, php5 |
         libapache2-mod-php5, php5-mysql, debconf (>= 0.5) | debconf-2.0
Recommends: libmath-round-perl
Description: Web interface add-on module for MythTV
 MythWeb provides a web interface which can be used to view listings, schedule recordings, delete recordings, and search
 for programs. It can also browse mythmusic's music database, and may eventually support playing music streams as well.

```

Just updated, works fine here

```
thomas@ares:~$ dpkg -l mythweb
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                   Version                                Description
+++-======================================-======================================-============================================================================================
ii  mythweb                                2:0.24.0+fixes.20110516.b5a3805-0ubunt Web interface add-on module for MythTV
thomas@ares:~$ 

```

Did you try restarting the backend process?

---

### Post by SteveGodfrey on 2011-05-17
I have restarted the backend, then out of desperation rebooted!

Given the update worked for you it looks like I'm going to have to reinstall. 

Thanks for the suggestion.

Can you tell me where your BackEnd.php is located?

---

### Post by tgm4883 on 2011-05-17
> **SteveGodfrey said:**
> I have restarted the backend, then out of desperation rebooted!

Given the update worked for you it looks like I'm going to have to reinstall. 

Thanks for the suggestion.

Can you tell me where your BackEnd.php is located?

By reinstall, I hope you mean the packages and not the OS. I'll check where mine is located when I get home. In the meantime, can you post the output of the following

```
dpkg -l myth*
```

---

### Post by SteveGodfrey on 2011-05-17
Weird. 

I simply ignored the error and recorded a few programmes and now the error has gone......

---

### Post by Dan_R on 2011-05-17
I had this problem also, this was on a fresh install of 10.04 0.24 fixes with no recordings. Once I recorded something and there were items to list in mythweb the errors disappeared.

---

### Post by bcg30506 on 2011-05-29
I am now getting the following at the top of the details page:
```
Warning at /usr/share/mythtv/mythweb/modules/tv/detail.php, line 310:
!!NoTrans: Invalid argument supplied for foreach()!!

Warning at /usr/share/mythtv/mythweb/modules/_shared/tmpl/default/header.php, line 16:
!!NoTrans: Cannot modify header information - headers already sent by (output started at /usr/share/mythtv/mythweb/includes/errors.php:150)!!
```
And the recorded program details takes minutes (yes, truly minutes) to come up now, but it eventually does.  Before upgrading from 0.23 to 0.24 these errors did not show up and it was very fast.  I've optimized the database and have several recordings in the group.  Any ideas?

I see these messages repeat over and over very quickly in the backend log while the browser is waiting for the response:
```
2011-05-29 16:46:41.160 adding: mythbox as a client (events: 2)
2011-05-29 16:46:41.189 MainServer::ANN Monitor
2011-05-29 16:46:41.226 adding: mythbox as a client (events: 2)
2011-05-29 16:46:41.255 MainServer::ANN Monitor
2011-05-29 16:46:41.285 adding: mythbox as a client (events: 2)
2011-05-29 16:50:01.715 MainServer::ANN Monitor
2011-05-29 16:50:01.746 adding: mythbox as a client (events: 0)

```
You can see 4 minutes go by before the events change from 2 to 0 and that is when I get the details page finally in my browser.

---

### Post by adamc on 2011-07-24
Just out of curiosity, what kind of capture card are you using? I'm experiencing this with a build including a Leadtec DTV2000DS but haven't seen the same issue with the one with a Leadtec DTV1000S. I'll have to swap the cards and see if the issue follows or stays.

---

### Post by bcg30506 on 2011-07-24
I have 2 types:  Hauppauge PVR-150 and SiliconDust HDHomeRun.

---

### Post by nzdanmc on 2011-09-21
Anybody have a fix for this yet? Im getting the same issue with a fresh install of mythbuntu using a HD Homerun.

---

### Post by bcg30506 on 2011-09-21
I just did the latest 0.24.1-fixes update this morning and the error messages on the details screen are gone, but it still took 4 minutes for the details to come up waiting for the video playback first frame.  I cannot find any activity in the log files during that time.

---

