---
title: "Mythweb on Ubuntu 16.04"
date: 2016-04-08
forum: Mythbuntu
---

### Post by jhoyt on 2016-04-08
After some issues I had to do a complete system wipe and did a clean install of Ubuntu 16.04.  The install went mostly smoothly, I managed to activate the 0.28 repo and managed to get mythbackend back up and running and restored from a database backup.  The only snag I managed to hit along the way is that mythweb will not install due to php5 and ibapache2-mod-php5 no longer being available.  Any suggestions on how to resolve the problem?

Here's the output from apt-get:

XXXX@mythtv:~$ sudo apt-get install mythweb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 mythweb : Depends: php5 but it is not installable or
                    libapache2-mod-php5 but it is not installable
           Depends: php5-mysql but it is not installable
           Recommends: libmath-round-perl but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by yonkiman on 2016-04-08
I don't have an answer for you, but I'm trying to get Mythbuntu 0.28 running on 16.04 as well.  If I get to the point where you are I'll try to help...

Along those lines - did you need to do anything special to get as far as you already have?  I've been trying this (reinstall latest 16.04 and bring up 0.28 with mythbuntu) off and on for a month or so.  Usually I ended up with mysql not starting, though once I had everything working (backend, frontend, imported database from my 14.04 system) then I tried to do the next step (hmmm...it might even have been to bring up mythweb) and I broke mysql again.  Once it goes I've never been able to bring it back.

Anyway, I'm just wondering if there's anything you found difficult to get where you are.  Did you just install 16.04 -> install mythbuntu-control-centre, and then let mcc take it from there?  I installed mysql 5.7 before I installed mcc, otherwise that's the path I'm taking...

---

### Post by yonkiman on 2016-04-08
I got to the same place with the same error.  I added some php5 repos from ppa:ondrej/php5 but mythweb still wasn't happy.  I guess we wait for mythweb to support php7?

---

### Post by jhoyt on 2016-04-08
Nothing in particular that was difficult.  I installed 16.04 then added the mythbuntu ppa.  I then went into syntaptic and installed "mythbuntu-desktop" and all of the plugins I wanted (minus mythweb :().  Once mythbuntu-desktop installed, I restored my database from a backup and my myth user's home directory from a backup and everything just worked.

---

### Post by jhoyt on 2016-04-08
Yep, sorry I should have noted that I tried out the php5 repos last night to no success.

I was hoping one of the mythbuntu dev's would see this forum post and check into their launchpad build.

If I get no success here, I'll probably try to ping the rest of the mythtv community on the mailing list.  Alternatively, the last time I had similar problems I started my own autobuilds on launchpad, was just trying to save myself some time/hassle.

---

### Post by yonkiman on 2016-04-08
Ahhh..*mythbuntu-desktop*.  I've been installing mythbuntu-control-centre and then telling it to set up a frontend and a primary backend.  The backend went OK.  Now I installed mythbuntu-desktop as you suggested and it installed (literally) about 100 packages.  And...it killed mysql.  Can't connect.  Get the same 

> ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I've been getting and unable to repair for the last month.  Guess I'll try again before I reinstall 16.04 from scratch again.  At least I know what to do next time - thanks!

---

### Post by jhoyt on 2016-04-08
Looks like a mysql issue, perhaps try:
    sudo apt-get purge mysql-server
    sudo apt-get autoremove
    sudo apt-get install mysql-server

---

### Post by yonkiman on 2016-04-08
Thanks again - I have a working Myth 0.28 installation on Xenial now!  Only open issue (besides mythweb) is mythbackend isn't starting on boot.  Does yours?

---

### Post by yonkiman on 2016-04-08
> **jhoyt said:**
> Looks like a mysql issue, perhaps try:
    sudo apt-get purge mysql-server
    sudo apt-get autoremove
    sudo apt-get install mysql-server

Thanks, but I didn't even try that this time (I did that and a dozen variations in the last few months).  I remembered I'd imaged the new 16.04 installation right before I started the mythbuntu installation, so I just restored to that and basically followed your instructions (mythbuntu-desktop) and it seems to be working correctly now.

---

### Post by yonkiman on 2016-04-08
> **yonkiman said:**
> Thanks again - I have a working Myth 0.28 installation on Xenial now!  Only open issue (besides mythweb) is mythbackend isn't starting on boot.  Does yours?

Fixed startup issue: [http://ubuntuforums.org/showthread.php?t=2319953](http://ubuntuforums.org/showthread.php?t=2319953)

---

### Post by jhoyt on 2016-04-08
That explains why mine just worked, I restored both my /home/mythtv and /home/mythuser directories from the backup as well (e.g. no symlink issues).

Glad to hear that you're up and running!

---

### Post by vidtek on 2016-04-09
I've been struggling with a few issues with Xenial, I had so many mysql problems with the 2002 error as well, but it is now working really well.  

Mine has always started on boot though.


Mythweb just gives a blank white screen or if I mess about with the directory listings in:   /etc/apache2/sites-available/mythweb.conf           

I get just a directory listing, but this surely shows that mythweb is working with php7, but I'm such a numpty I just can't configure it correctly?

Tony

edit- I also have the mcc issue with no option to save the mythweb plugin, there's a simple fix but I can't quite remember it.

---

### Post by jhoyt on 2016-04-09
Strange, I just installed mythweb manually and it worked (you may need to update mythweb.conf a little to match your database setup).

Here's what I did:
     sudo apt-get install php llibapache2-mod-php php-mysql
Then followed the directions here making sure to pull down the 0.28 version of mythweb
     [https://www.mythtv.org/wiki/Build_from_Source#Install_MythWeb](https://www.mythtv.org/wiki/Build_from_Source#Install_MythWeb)

Have you checked the systemctl status or apache2 logs to make sure everything actually loaded?

::original post had libapache2-mod-php listed incorrectly as libapache2-mod-apache (not enough coffee)::

---

### Post by vidtek on 2016-04-09
[QUOTE=]

Have you checked the systemctl status or apache2 logs to make sure everything actually loaded?[/QUOTE]

I know apache is loading correctly by manually starting it with ```
systemctl restart apache2.service
```
and I don't get any errors. 

I'll have a go at your build method and report back, it'll take a while, got to consider the WAF!

Thanks for your input

Tony

---

### Post by vidtek on 2016-04-09
> **jhoyt said:**
> Strange, I just installed mythweb manually and it worked (you may need to update mythweb.conf a little to match your database setup).

Here's what I did:
     sudo apt-get install php libapache2-mod-apache php-mysql
Then followed the directions here making sure to pull down the 0.28 version of mythweb
     [https://www.mythtv.org/wiki/Build_from_Source#Install_MythWeb](https://www.mythtv.org/wiki/Build_from_Source#Install_MythWeb)


Weird how you could do this and this:

```
tony@linuxmint:~$ sudo apt-get install php libapache2-mod-apache php-mysql
[sudo] password for tony: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libapache2-mod-apache

```

is not in my repos.

I did a google search on libapache2-mod-apache and got some very strange results.


Oh well, keep on looking/trying

It seems the Archlinux guys have got it sorted with a pacman patch, so it is possible.

Cheers, Tony.

edit-

Just found this:  libapache2-mod-php7.0

at this:  [https://packages.debian.org/search?keywords=libapache2-mod-php7.0](https://packages.debian.org/search?keywords=libapache2-mod-php7.0)    site and installed, see if it works.

---

### Post by yonkiman on 2016-04-09
> **vidtek said:**
> 
```
E: Unable to locate package libapache2-mod-apache
```
is not in my repos.

Same here.

> Just found this:  libapache2-mod-php7.0
at this:  [https://packages.debian.org/search?keywords=libapache2-mod-php7.0](https://packages.debian.org/search?keywords=libapache2-mod-php7.0)    site and installed, see if it works.

Are you saying it worked for you?

**jhoyt: **Do you know where you got your **libapache2-mod-apache** from?  I'd rather get it from a standard repo if possible...

---

### Post by tgm4883 on 2016-04-09
The package is libapache2-mod-php not libapache2-mod-apache.

I've also just pushed a dependency fix for this, which should be in tonights builds.

---

### Post by jhoyt on 2016-04-09
yep libapache2-mod-php, sorry for the typo.  I'll correct the original post.

Also, thanks for the quick fix!!!

---

### Post by vidtek on 2016-04-09
Yes, this worked, I still have an error on the front page, but at least mythweb now works (sort of).

---

### Post by yonkiman on 2016-04-10
> **vidtek said:**
> Yes, this worked, I still have an error on the front page, but at least mythweb now works (sort of).
What's your error?  With the latest build I finally get the MythWeb "framework", but there's no data, just:

[INDENT]Error

Unable to connect to the master backend at 192.168.1.100:6543.
Is it running?[/INDENT]

Interestingly, mythtv-status *mostly* works:

[INDENT]$ mythtv-status

MythTV status for localhost
===========================
Status...........: 2016-04-10 18:07:31
Total Disk Space.: Total space is 5.4 TB, with 4.6 TB used (85.2%)
Next Recording In: 35 Minutes

Scheduled Recordings:
2016-04-10 18:43:00 - Fear the Walking Dead (AMC HD (Pacific))
2016-04-10 20:00:00 - Madam Secretary (KIONDT (KION-DT))

Schedule Conflicts:
Unable to access MythTV Perl API.  Try with --verbose to find out why.[/INDENT]

When I try --verbose, I see what appears to be the same issue I have with mythweb:

[INDENT]Failed to load Perl API
Couldn't communicate with 192.168.1.100 on port 6543:  IO::Socket::INET::MythTV: connect: Connection refused[/INDENT]

That's really weird, isn't it?  mythtv-status seems to be able to connect to the database for scheduled recordings but not conflicts?

Anyone have any ideas?

---

### Post by vidtek on 2016-04-11
> **yonkiman said:**
> What's your error?  With the latest build I finally get the MythWeb "framework", but there's no data, just:[INDENT]Error

Unable to connect to the master backend at 192.168.1.100:6543.
Is it running?[/INDENT]

Interestingly, mythtv-status *mostly* works:[INDENT]$ mythtv-status

MythTV status for localhost
===========================
Status...........: 2016-04-10 18:07:31
Total Disk Space.: Total space is 5.4 TB, with 4.6 TB used (85.2%)
Next Recording In: 35 Minutes

Scheduled Recordings:
2016-04-10 18:43:00 - Fear the Walking Dead (AMC HD (Pacific))
2016-04-10 20:00:00 - Madam Secretary (KIONDT (KION-DT))

Schedule Conflicts:
Unable to access MythTV Perl API.  Try with --verbose to find out why.[/INDENT]

When I try --verbose, I see what appears to be the same issue I have with mythweb:[INDENT]Failed to load Perl API
Couldn't communicate with 192.168.1.100 on port 6543:  IO::Socket::INET::MythTV: connect: Connection refused[/INDENT]

That's really weird, isn't it?  mythtv-status seems to be able to connect to the database for scheduled recordings but not conflicts?

Anyone have any ideas?

Yonkiman-

It looks like a permissions problem, you can't login with the correct credentials, check your mythweb.conf's and sites-enabled/sites-available.

My mythweb is working apart from the front page which just comes up with:

*An unknown module was specified*

The listings page shows this:

[I]Fatal Error

!!NoTrans: SQL Error: Expression #1 of SELECT list is not in GROUP BY clause and contains nonaggregated column 'mythconverg.channel.chanid' which is not functionally dependent on columns in GROUP BY clause; this is incompatible with sql_mode=only_full_group_by [#1055]!!

If you choose to submit a bug report please make sure to include a brief description of what you were doing, along with the following backtrace as an attachment (please don\'t just paste the whole thing into the ticket) 
[/I]
Then I get a box with the backtrace.

On the recording schedule (manual) I get this:

[I]Recording Options:

Channel: 
    Fatal Error

    !!NoTrans: SQL Error: Expression #1 of SELECT list is not in GROUP BY clause and contains nonaggregated column 'mythconverg.channel.chanid' which is not functionally dependent on columns in GROUP BY clause; this is incompatible with sql_mode=only_full_group_by [#1055]!!
  
[/I]

Recorded Programmes gives this:

[I]atal Error

!!NoTrans: SQL Error: Expression #2 of SELECT list is not in GROUP BY clause and contains nonaggregated column 'mythconverg.recordedmarkup.data' which is not functionally dependent on columns in GROUP BY clause; this is incompatible with sql_mode=only_full_group_by [#1055]!!

[/I]

Every other page seems to behave normally, although I have not yet investigated more than one page deep into the links (the first page).

This is the upcoming recordings page:

[IMG]https://www.dropbox.com/s/l44i9u1lt7v1ij0/mythweb_recordings.jpg?dl=0[/IMG]


I just did a screendump of it.  

So obviously it's working in some parts, sounds like I'm further on than you, but not by much.

I have sent the backtrace off as requested.

[I]#12719: Mythweb listings page brings this error
----------------------------------+-------------------------
 Reporter:  vidtek99@&#8230;            |          Owner:  kormoc
     Type:  Bug Report - General  |         Status:  new
 Priority:  minor                 |      Milestone:  unknown
Component:  Plugin - MythWeb      |        Version:  0.28
 Severity:  medium                |     Resolution:
 Keywords:  Mythweb listings      |  Ticket locked:  0
----------------------------------+-------------------------
Changes (by vidtek99@&#8230;):

Attachment "mythweb_bug.txt" added
[/I]
BTW, why is this thread marked as solved?  Clearly it isn't.

Cheers, Tony.

---

### Post by jhoyt on 2016-04-11
> **vidtek said:**
> 
BTW, why is this thread marked as solved?  Clearly it isn't.

Cheers, Tony.

Tony, I marked the thread as solved because when I opened the thread the problem was that Mythweb wasn't installable from the mythbuntu repos.  That issue has been resolved.

The subsequent problems are a bit of unintentional thread-jacking by myself (the original poster) and others.

These other issues should really move into their own dedicated thread, as the initial problem truly is solved.

---

### Post by yonkiman on 2016-04-11
Apologies.  I weighed the drawbacks of threadjacking (and asking for help in a "SOLVED" thread) vs the benefits of keeping all discussion on this topic ("Mythweb on Ubuntu 16.04") in a single thread, and...I guess I made the wrong call.  I'll start a new thread.

---

### Post by vidtek on 2016-04-12
jhoyt-

Fair do's.  As you are not quite as far along as I, it's probably best for you to start a new one.

Cheers, Tony.

---

### Post by yonkiman on 2016-04-18
A solution to the SQL Fatal Error mentioned above is a tweak to the /etc/mysql/conf.d/mythtv.cnf file.  Add "sql_mode=NO_ENGINE_SUBSTITUTION" (without the quotation marks) to the end of the /etc/mysql/conf.d/mythtv.cnf file.  I believe the error was caused by an incompatibility between mysql 5.7 and databases from older versions of mysql.

There may be other and better solutions (I imagine the problem will be fixed by the devs), but this one works for now.

---

### Post by Matthew_LaPine on 2016-08-02
Thank you for this quick workaround.  Of course the mysql daemon has to be restarted to reload the cnf file.  Much appreciated.

---

### Post by thundre on 2016-11-28
I was unable to find pointers to the other thread(s) about this sub-issue, so here I am in this one.

> **yonkiman said:**
> A solution to the SQL Fatal Error mentioned above is a tweak to the /etc/mysql/conf.d/mythtv.cnf file.  Add "sql_mode=NO_ENGINE_SUBSTITUTION" (without the quotation marks) to the end of the /etc/mysql/conf.d/mythtv.cnf file.  I believe the error was caused by an incompatibility between mysql 5.7 and databases from older versions of mysql.

There may be other and better solutions (I imagine the problem will be fixed by the devs), but this one works for now.

This change, followed by a restart of mysql, solved the mythweb problem instantly for me.  Thank you, Yonkiman.  

But after 7 months I would expect some kind of fix to make its way into the distribution.  I was bitten after I upgraded from 15.10 to 16.04 yesterday.  Has nobody told the developers?

---

### Post by trshyd on 2017-03-08
> **yonkiman said:**
> A solution to the SQL Fatal Error mentioned above is a tweak to the /etc/mysql/conf.d/mythtv.cnf file.  Add "sql_mode=NO_ENGINE_SUBSTITUTION" (without the quotation marks) to the end of the /etc/mysql/conf.d/mythtv.cnf file.  I believe the error was caused by an incompatibility between mysql 5.7 and databases from older versions of mysql.

There may be other and better solutions (I imagine the problem will be fixed by the devs), but this one works for now.

I am currently on Ubuntu 16.10, kernel 4.8.0

I can confirm that this solution worked like a charm.

Added "sql_mode=NO_ENGINE_SUBSTITUTION" to mythtv.cnf

All my functions were already working on mythweb, except for the "Recorded Programs" page.

This solved that issue

My suspicion is a permission issue or other mysql user access issue.

The error I had, which was displayed on the mythweb webpage itself:
"error string: !!NoTrans: SQL Error: Expression #2 of SELECT list is not in GROUP BY clause and contains nonaggregated column 'mythconverg.recordedmarkup.data' which is not functionally dependent on columns in GROUP BY clause; this is incompatible with sql_mode=only_full_group_by [#1055]!! filename: /usr/share/mythtv/mythweb/classes/Database/Query/mysqlicompat.php"

---

