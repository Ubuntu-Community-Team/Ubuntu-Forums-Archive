---
title: "MythWeb homepage loads but no other pages work"
date: 2014-10-24
forum: Mythbuntu
---

### Post by prcutler on 2014-10-24
Hi all,

I'm hoping someone may be able to help.  I've searched through the forums and found some similar threads, but no fixes.

Here's the situation:

I upgraded to 14.04 on my MythBuntu machine and upgraded from MythTV 0.25 to 0.27+fixes.  Everything is working - I can watch live TV, recorded shows and everything is fine.

Except MythWeb.  The home page for MythWeb loads, but clicking any links brings up a 404 page, for example from [http://192.168.1.101/mythweb/tv/list](http://192.168.1.101/mythweb/tv/list) (but [http://192.168.1.101/mythweb](http://192.168.1.101/mythweb) does bring up the expected page)

I thought it might be related to this bug from earlier this year:  [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/1300404](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/1300404)
I followed the instructions there, but same situation.

This thread ([http://ubuntuforums.org/showthread.php?t=2179047&highlight=mythweb](http://ubuntuforums.org/showthread.php?t=2179047&highlight=mythweb)) was similar, but there wasn't a solution.

I then did an apt-get purge mythweb and reinstalled.  Same issue.

MythWeb is enabled in the Control Centre and I am using the Mythbuntu repositories / PPA.

There are no errors in my Apache logs.  No errors when starting or restarting Apache.

This is the section from the mythweb.conf file:

```
# CHANGE THESE PATHS TO MATCH YOUR MYTHWEB INSTALLATION DIRECTORY!  e.g.#
#    /var/www
#    /home/www/htdocs
#    /var/www/html/mythweb/mythweb
#    /srv/www/htdocs/mythweb
#
    <Directory "/var/www/html/mythweb/data">
        # For Apache 2.2
        #Options -All +FollowSymLinks +IncludesNoExec
        # For Apache 2.4+
        Options +FollowSymLinks +IncludesNoExec
    </Directory>

```

I did confirm I am running Apache 2.4:

```
||/ Name           Version      Architecture Description+++-==============-============-============-=================================
ii  apache2        2.4.7-1ubunt i386         Apache HTTP Server

```

The mythweb directory is in /var/www/html/mythweb

Mod_rewrite is enabled:
```
a2enmod rewrite
Module rewrite already enabled
```

What am I missing?  

Thanks in advance.

---

