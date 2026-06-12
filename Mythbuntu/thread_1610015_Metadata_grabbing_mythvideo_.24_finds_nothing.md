---
title: "Metadata grabbing mythvideo .24 finds nothing"
date: 2010-10-31
forum: Mythbuntu
---

### Post by Herman Gerritsen on 2010-10-31
Hi there,

I replied this before to a thread that had the prefix solved in the title, I now realize that that might not work. So here again in a new thread. 

I recently updated to mythbuntu repos .s4 (revision 27009) from mythbuntu repos .23.1-fixes on a ubuntu 10.04 os.
After the update I started using metadata grabbing for my videos (mythvideo), so I am not sure it ever worked for me.

From the Frontend logs I see this:

```
2010-10-30 22:38:17.307 Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M The Matrix
2010-10-30 22:38:17.341 No results found for The Matrix 0 0 

```When I run tmdb.py manually (from /usr/share/mythtv/metadata/Movie/) it returns this error:

```
me@be:/usr/share/mythtv/metadata/Movie$ ./tmdb.py -l en -M The Matrix

The subdirectory "tmdb" containing the modules tmdb_api.py (v0.1.3 or greater), tmdb_ui.py,
tmdb_exceptions.py must have been installed with the MythTV python bindings.
Error:(No module named lxml.etree)

```When I investigate the /usr/share/pyshared/Mythtv/tmdb directory on my backend the requested modules are there. Since these modules are there I believe the myth-phyton bindings are installed (I had to do this manually on the back-end server). But I think something went wrong. (sudo apt-get install libmyth-python)

I am lost from here, are there any pointers?

Thanks,
Herman

---

### Post by joshoekstra on 2010-10-31
Check the thread I started where you responded as well, should help. :)

---

### Post by iitywygms on 2010-11-15
I am having the same issue.  Can someone point to the thread the above poster mentioned?  Or is a simple fix available?
Thanks.

---

### Post by tazz4vr on 2010-11-15
perhaps - [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1594811](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1594811)

---

### Post by superm1 on 2010-11-15
This has popped up from time to time.  After those initial problems from the other thread were resolved, the only remaining issue i've seen with this is people with stuff in /usr/local.

Please try running the mythpython binary and see if it works.  If it doesn't, check in /usr/local for remenants from an old hand install or non mythbuntu-produced debs.

---

### Post by iitywygms on 2010-11-15
Thanks for the info.
If I go to my backend and run ./tmdb.py -l en -M Avatar I get all the correct info for avatar

If I go to my frontend machine and run "retrieve all details"

My frontend log fills with this.

MythUIHelper, Error: LoadScaleImage(gallery-folder-reg.png)Unable to find image file

I am a bit of a linux idiot also.  Not sure how I should do
check in /usr/local for remenants from an old hand install or non mythbuntu-produced debs. 
I looked in that area and saw nothing out of the norm as far as I can tell.
Thanks

Edit:
Before I read this, I did a sudo apt-get purge myth* on both the frontend and backend machines.  Installed the auto-builds so I can run .24
After all that, I am still having the same issue.  Mythtv works fine.
I have an issue with mythnetvision also.  Not filling with info.  I wonder if these two problems are related????
Anyway, I would rather work on the metadata stuff first.

---

### Post by tazz4vr on 2010-11-16
Just curious.... has anyone tried checking info in -
[http://www.mythtv.org/wiki/MythNetvision](http://www.mythtv.org/wiki/MythNetvision) - 

under the Trouble Shooting it references:
***I don't see any sites when I try to subscribe to tree views! ***
This is generally an indication that you are missing a prerequisite for the script to run. See the list of prerequisites at the top of this page, and try running the script with the argument -v to see what you might be missing.

---

### Post by iitywygms on 2010-11-16
deleted.

---

### Post by tazz4vr on 2010-11-16
[http://www.mythtv.org/wiki/MythNetvision_Grabber_Script_Format](http://www.mythtv.org/wiki/MythNetvision_Grabber_Script_Format)
Contents includes - Metadata Standards (5)
*****
Hope info is helping, if not I do apologize... let me know and i'll stick with what I do know, like pool and dancing! :biggrin:

---

### Post by tgm4883 on 2010-11-16
I believe I see where the issue is. I'm going to try and get an update pushed before the build in 2.5 hours

---

### Post by iitywygms on 2010-11-16
> **tgm4883 said:**
> I believe I see where the issue is. I'm going to try and get an update pushed before the build in 2.5 hours

Really appreciate the help.  I will update then report back.

---

### Post by iitywygms on 2010-11-16
Okay, got the latest and greatest isntalled.
Added the Matrix to the mix.
Ran scan for changes.
Ran Retrieve all details.

Nothing updated.

mythfrontend.log shows

2010-11-16 18:50:15.672 Adding :  : The_Matrix.avi : 7ecfdd95e8e685ec
2010-11-16 18:50:15.901 Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M The Matrix
2010-11-16 18:50:15.922 No results found for The Matrix 0 0

Any ideas?

---

### Post by tgm4883 on 2010-11-16
2 things

1) what is the output of these commands 

```
dpkg -S /usr/share/mythtv/metadata/Movie/tmdb.py
dpkg -l libmyth-python libmythtv-perl mythtv-frontend mythtv-backend mythtv-common mythvideo
ls -l /usr/local/
```

2) I missed the build time with my commit by 6 minutes, so my fix isn't in there :(. Unfortunatly you already have tmdb.py there, so there is something else going on.

---

### Post by iitywygms on 2010-11-16
This is from my frontend machine


dpkg -S /usr/share/mythtv/metadata/Movie/tmdb.py

dpkg: /usr/share/mythtv/metadata/Movie/tmdb.py not found.   

kevin@mythbigscreen:/var/log/mythtv$ dpkg -l libmyth-python libmythtv-perl mythtv-frontend mythtv-backend mythtv-common mythvideo
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                          Version                       Description
+++-=============================-=============================-==========================================================================
ii  libmyth-python                1:0.24.0+fixes27251-0ubuntu0+ A python library to access some MythTV features
un  libmythtv-perl                <none>                        (no description available)
rc  mythtv-backend                1:0.24.0+fixes27220-0ubuntu0+ A personal video recorder application (server)
ii  mythtv-common                 1:0.24.0+fixes27251-0ubuntu0+ A personal video recorder application (common data)
ii  mythtv-frontend               1:0.24.0+fixes27251-0ubuntu0+ A personal video recorder application (client)
ii  mythvideo                     1:0.24.0+fixes27251-0ubuntu0+ A generic video player frontend module for MythTV


kevin@mythbigscreen:/var/log/mythtv$ ls -l /usr/local/
total 32
drwxr-xr-x 2 root root 4096 2009-10-27 10:15 bin
drwxr-xr-x 2 root root 4096 2009-10-27 10:15 etc
drwxr-xr-x 2 root root 4096 2009-10-27 10:15 games
drwxr-xr-x 2 root root 4096 2009-10-27 10:15 include
drwxr-xr-x 3 root root 4096 2010-07-05 18:21 lib
lrwxrwxrwx 1 root root    9 2010-01-05 19:15 man -> share/man
drwxr-xr-x 2 root root 4096 2009-10-27 10:15 sbin
drwxr-xr-x 8 root root 4096 2010-05-16 17:42 share
drwxr-xr-x 2 root root 4096 2009-10-27 10:15 src

---

### Post by iitywygms on 2010-11-16
from backend machine

kevin@mythbackend:~$ dpkg -S /usr/share/mythtv/metadata/Movie/tmdb.py
mythtv-backend: /usr/share/mythtv/metadata/Movie/tmdb.py
kevin@mythbackend:~$ 


kevin@mythbackend:~$ dpkg -l libmyth-python libmythtv-perl mythtv-frontend mythtv-backend mythtv-common mythvideo
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                          Version                       Description
+++-=============================-=============================-==========================================================================
ii  libmyth-python                1:0.24.0+fixes27251-0ubuntu0+ A python library to access some MythTV features
ii  libmythtv-perl                1:0.24.0+fixes27251-0ubuntu0+ A PERL library to access some MythTV features
ii  mythtv-backend                1:0.24.0+fixes27251-0ubuntu0+ A personal video recorder application (server)
ii  mythtv-common                 1:0.24.0+fixes27251-0ubuntu0+ A personal video recorder application (common data)
rc  mythtv-frontend               1:0.24.0+fixes27220-0ubuntu0+ A personal video recorder application (client)
rc  mythvideo                     1:0.24.0+fixes27220-0ubuntu0+ A generic video player frontend module for MythTV
kevin@mythbackend:~$ 

kevin@mythbackend:~$ ls -l /usr/local/
total 36
drwxr-xr-x  2 root root 4096 2010-04-05 19:52 bin
drwxr-xr-x  2 root root 4096 2010-04-05 19:52 etc
drwxr-xr-x  2 root root 4096 2010-04-05 19:52 games
drwxr-xr-x  2 root root 4096 2010-04-05 19:52 include
drwxr-xr-x  5 root root 4096 2010-04-05 19:52 lib
lrwxrwxrwx  1 root root    9 2010-04-13 23:33 man -> share/man
drwxr-xr-x  2 root root 4096 2010-04-05 19:52 sbin
drwxr-xr-x 13 root root 4096 2010-04-05 19:59 share
drwxr-xr-x  2 root root 4096 2010-04-05 19:52 src
drwxr-xr-x  3 root root 4096 2010-08-29 01:05 ZebraNetworkSystems
kevin@mythbackend:~$

---

### Post by superm1 on 2010-11-16
> **iitywygms said:**
> from backend machine

kevin@mythbackend:~$ dpkg -S /usr/share/mythtv/metadata/Movie/tmdb.py
mythtv-backend: /usr/share/mythtv/metadata/Movie/tmdb.py
kevin@mythbackend:~$ 


kevin@mythbackend:~$ dpkg -l libmyth-python libmythtv-perl mythtv-frontend mythtv-backend mythtv-common mythvideo
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                          Version                       Description
+++-=============================-=============================-==========================================================================
ii  libmyth-python                1:0.24.0+fixes27251-0ubuntu0+ A python library to access some MythTV features
ii  libmythtv-perl                1:0.24.0+fixes27251-0ubuntu0+ A PERL library to access some MythTV features
ii  mythtv-backend                1:0.24.0+fixes27251-0ubuntu0+ A personal video recorder application (server)
ii  mythtv-common                 1:0.24.0+fixes27251-0ubuntu0+ A personal video recorder application (common data)
rc  mythtv-frontend               1:0.24.0+fixes27220-0ubuntu0+ A personal video recorder application (client)
rc  mythvideo                     1:0.24.0+fixes27220-0ubuntu0+ A generic video player frontend module for MythTV
kevin@mythbackend:~$ 

kevin@mythbackend:~$ ls -l /usr/local/
total 36
drwxr-xr-x  2 root root 4096 2010-04-05 19:52 bin
drwxr-xr-x  2 root root 4096 2010-04-05 19:52 etc
drwxr-xr-x  2 root root 4096 2010-04-05 19:52 games
drwxr-xr-x  2 root root 4096 2010-04-05 19:52 include
drwxr-xr-x  5 root root 4096 2010-04-05 19:52 lib
lrwxrwxrwx  1 root root    9 2010-04-13 23:33 man -> share/man
drwxr-xr-x  2 root root 4096 2010-04-05 19:52 sbin
drwxr-xr-x 13 root root 4096 2010-04-05 19:59 share
drwxr-xr-x  2 root root 4096 2010-04-05 19:52 src
drwxr-xr-x  3 root root 4096 2010-08-29 01:05 ZebraNetworkSystems
kevin@mythbackend:~$

Minor modification.  Need to see what else is in /usr/local to evaluate if that's where the problem is.  From the broken box please provide the output of both of these commands:

#mythpython --version

#ls -alhR /usr/local

---

### Post by iitywygms on 2010-11-17
Frontend machine

kevin@mythbigscreen:~$ mythpython --version
MythTV Python Bindings
  local versions
    bindings version:   0.24.0.0
    ttvdb version:      1.2.1
    tmdb version:       v0.2.5
  external versions
    lxml version:       2.2.4
    MySQLdb version:    1.2.2.final.0
  protocol versions
    backend:            63
    schema:             1264
    video schema:       1038
    music schema:       1017
    netvision schema:   1007
kevin@mythbigscreen:~$ ls -alhR /usr/local
/usr/local:
total 40K
drwxr-xr-x 10 root root 4.0K 2009-10-27 10:15 .
drwxr-xr-x 11 root root 4.0K 2009-10-27 10:18 ..
drwxr-xr-x  2 root root 4.0K 2009-10-27 10:15 bin
drwxr-xr-x  2 root root 4.0K 2009-10-27 10:15 etc
drwxr-xr-x  2 root root 4.0K 2009-10-27 10:15 games
drwxr-xr-x  2 root root 4.0K 2009-10-27 10:15 include
drwxr-xr-x  3 root root 4.0K 2010-07-05 18:21 lib
lrwxrwxrwx  1 root root    9 2010-01-05 19:15 man -> share/man
drwxr-xr-x  2 root root 4.0K 2009-10-27 10:15 sbin
drwxr-xr-x  8 root root 4.0K 2010-05-16 17:42 share
drwxr-xr-x  2 root root 4.0K 2009-10-27 10:15 src

/usr/local/bin:
total 8.0K
drwxr-xr-x  2 root root 4.0K 2009-10-27 10:15 .
drwxr-xr-x 10 root root 4.0K 2009-10-27 10:15 ..

/usr/local/etc:
total 8.0K
drwxr-xr-x  2 root root 4.0K 2009-10-27 10:15 .
drwxr-xr-x 10 root root 4.0K 2009-10-27 10:15 ..

/usr/local/games:
total 8.0K
drwxr-xr-x  2 root root 4.0K 2009-10-27 10:15 .
drwxr-xr-x 10 root root 4.0K 2009-10-27 10:15 ..

/usr/local/include:
total 8.0K
drwxr-xr-x  2 root root 4.0K 2009-10-27 10:15 .
drwxr-xr-x 10 root root 4.0K 2009-10-27 10:15 ..

/usr/local/lib:
total 12K
drwxr-xr-x  3 root root  4.0K 2010-07-05 18:21 .
drwxr-xr-x 10 root root  4.0K 2009-10-27 10:15 ..
drwxrwsr-x  4 root staff 4.0K 2010-05-16 18:16 python2.6

/usr/local/lib/python2.6:
total 16K
drwxrwsr-x 4 root staff 4.0K 2010-05-16 18:16 .
drwxr-xr-x 3 root root  4.0K 2010-07-05 18:21 ..
drwxrwsr-x 2 root staff 4.0K 2009-10-27 10:15 dist-packages
drwxrwsr-x 2 root staff 4.0K 2010-05-16 18:16 site-packages

/usr/local/lib/python2.6/dist-packages:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2009-10-27 10:15 .
drwxrwsr-x 4 root staff 4.0K 2010-05-16 18:16 ..

/usr/local/lib/python2.6/site-packages:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2010-05-16 18:16 .
drwxrwsr-x 4 root staff 4.0K 2010-05-16 18:16 ..

/usr/local/sbin:
total 8.0K
drwxr-xr-x  2 root root 4.0K 2009-10-27 10:15 .
drwxr-xr-x 10 root root 4.0K 2009-10-27 10:15 ..

/usr/local/share:
total 32K
drwxr-xr-x  8 root root  4.0K 2010-05-16 17:42 .
drwxr-xr-x 10 root root  4.0K 2009-10-27 10:15 ..
drwxrwsr-x  2 root staff 4.0K 2009-10-27 10:16 ca-certificates
drwxrwsr-x  2 root staff 4.0K 2009-10-27 10:23 fonts
drwxr-xr-x  3 root root  4.0K 2009-10-27 10:27 games
drwxr-xr-x  2 root root  4.0K 2009-10-27 10:15 man
drwxrwsr-x  7 root staff 4.0K 2009-10-27 10:16 sgml
drwxrwsr-x  6 root staff 4.0K 2010-05-16 17:42 xml

/usr/local/share/ca-certificates:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2009-10-27 10:16 .
drwxr-xr-x 8 root root  4.0K 2010-05-16 17:42 ..

/usr/local/share/fonts:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2009-10-27 10:23 .
drwxr-xr-x 8 root root  4.0K 2010-05-16 17:42 ..

/usr/local/share/games:
total 12K
drwxr-xr-x 3 root root 4.0K 2009-10-27 10:27 .
drwxr-xr-x 8 root root 4.0K 2010-05-16 17:42 ..
drwxr-xr-x 2 root root 4.0K 2009-10-27 10:27 fortunes

/usr/local/share/games/fortunes:
total 8.0K
drwxr-xr-x 2 root root 4.0K 2009-10-27 10:27 .
drwxr-xr-x 3 root root 4.0K 2009-10-27 10:27 ..

/usr/local/share/man:
total 8.0K
drwxr-xr-x 2 root root 4.0K 2009-10-27 10:15 .
drwxr-xr-x 8 root root 4.0K 2010-05-16 17:42 ..

/usr/local/share/sgml:
total 28K
drwxrwsr-x 7 root staff 4.0K 2009-10-27 10:16 .
drwxr-xr-x 8 root root  4.0K 2010-05-16 17:42 ..
drwxrwsr-x 2 root staff 4.0K 2009-10-27 10:16 declaration
drwxrwsr-x 2 root staff 4.0K 2009-10-27 10:16 dtd
drwxrwsr-x 2 root staff 4.0K 2009-10-27 10:16 entities
drwxrwsr-x 2 root staff 4.0K 2009-10-27 10:16 misc
drwxrwsr-x 2 root staff 4.0K 2009-10-27 10:16 stylesheet

/usr/local/share/sgml/declaration:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2009-10-27 10:16 .
drwxrwsr-x 7 root staff 4.0K 2009-10-27 10:16 ..

/usr/local/share/sgml/dtd:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2009-10-27 10:16 .
drwxrwsr-x 7 root staff 4.0K 2009-10-27 10:16 ..

/usr/local/share/sgml/entities:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2009-10-27 10:16 .
drwxrwsr-x 7 root staff 4.0K 2009-10-27 10:16 ..

/usr/local/share/sgml/misc:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2009-10-27 10:16 .
drwxrwsr-x 7 root staff 4.0K 2009-10-27 10:16 ..

/usr/local/share/sgml/stylesheet:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2009-10-27 10:16 .
drwxrwsr-x 7 root staff 4.0K 2009-10-27 10:16 ..

/usr/local/share/xml:
total 24K
drwxrwsr-x 6 root staff 4.0K 2010-05-16 17:42 .
drwxr-xr-x 8 root root  4.0K 2010-05-16 17:42 ..
drwxrwsr-x 2 root staff 4.0K 2010-05-16 17:42 declaration
drwxrwsr-x 2 root staff 4.0K 2010-05-16 17:42 entities
drwxrwsr-x 2 root staff 4.0K 2010-05-16 17:42 misc
drwxrwsr-x 2 root staff 4.0K 2010-05-16 17:42 schema

/usr/local/share/xml/declaration:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2010-05-16 17:42 .
drwxrwsr-x 6 root staff 4.0K 2010-05-16 17:42 ..

/usr/local/share/xml/entities:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2010-05-16 17:42 .
drwxrwsr-x 6 root staff 4.0K 2010-05-16 17:42 ..

/usr/local/share/xml/misc:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2010-05-16 17:42 .
drwxrwsr-x 6 root staff 4.0K 2010-05-16 17:42 ..

/usr/local/share/xml/schema:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2010-05-16 17:42 .
drwxrwsr-x 6 root staff 4.0K 2010-05-16 17:42 ..

/usr/local/src:
total 8.0K
drwxr-xr-x  2 root root 4.0K 2009-10-27 10:15 .
drwxr-xr-x 10 root root 4.0K 2009-10-27 10:15 ..
kevin@mythbigscreen:~$ 


backend machine

kevin@mythbackend:~$ mythpython --version
MythTV Python Bindings
  local versions
    bindings version:   0.24.0.0
    ttvdb version:      1.2.1
    tmdb version:       v0.2.5
  external versions
    lxml version:       2.2.4
    MySQLdb version:    1.2.2.final.0
  protocol versions
    backend:            63
    schema:             1264
    video schema:       1038
    music schema:       1017
    netvision schema:   1007
kevin@mythbackend:~$ ls -alhR /usr/local
/usr/local:
total 44K
drwxr-xr-x 11 root root 4.0K 2010-08-29 01:05 .
drwxr-xr-x 12 root root 4.0K 2010-11-06 17:57 ..
drwxr-xr-x  2 root root 4.0K 2010-04-05 19:52 bin
drwxr-xr-x  2 root root 4.0K 2010-04-05 19:52 etc
drwxr-xr-x  2 root root 4.0K 2010-04-05 19:52 games
drwxr-xr-x  2 root root 4.0K 2010-04-05 19:52 include
drwxr-xr-x  5 root root 4.0K 2010-04-05 19:52 lib
lrwxrwxrwx  1 root root    9 2010-04-13 23:33 man -> share/man
drwxr-xr-x  2 root root 4.0K 2010-04-05 19:52 sbin
drwxr-xr-x 13 root root 4.0K 2010-04-05 19:59 share
drwxr-xr-x  2 root root 4.0K 2010-04-05 19:52 src
drwxr-xr-x  3 root root 4.0K 2010-08-29 01:05 ZebraNetworkSystems

/usr/local/bin:
total 8.0K
drwxr-xr-x  2 root root 4.0K 2010-04-05 19:52 .
drwxr-xr-x 11 root root 4.0K 2010-08-29 01:05 ..

/usr/local/etc:
total 8.0K
drwxr-xr-x  2 root root 4.0K 2010-04-05 19:52 .
drwxr-xr-x 11 root root 4.0K 2010-08-29 01:05 ..

/usr/local/games:
total 8.0K
drwxr-xr-x  2 root root 4.0K 2010-04-05 19:52 .
drwxr-xr-x 11 root root 4.0K 2010-08-29 01:05 ..

/usr/local/include:
total 8.0K
drwxr-xr-x  2 root root 4.0K 2010-04-05 19:52 .
drwxr-xr-x 11 root root 4.0K 2010-08-29 01:05 ..

/usr/local/lib:
total 20K
drwxr-xr-x  5 root root  4.0K 2010-04-05 19:52 .
drwxr-xr-x 11 root root  4.0K 2010-08-29 01:05 ..
drwxrwsr-x  3 root staff 4.0K 2010-04-13 17:23 python2.4
drwxrwsr-x  3 root staff 4.0K 2010-04-13 17:23 python2.5
drwxrwsr-x  4 root staff 4.0K 2010-04-17 13:37 python2.6

/usr/local/lib/python2.4:
total 12K
drwxrwsr-x 3 root staff 4.0K 2010-04-13 17:23 .
drwxr-xr-x 5 root root  4.0K 2010-04-05 19:52 ..
drwxrwsr-x 2 root staff 4.0K 2010-04-13 17:23 site-packages

/usr/local/lib/python2.4/site-packages:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2010-04-13 17:23 .
drwxrwsr-x 3 root staff 4.0K 2010-04-13 17:23 ..

/usr/local/lib/python2.5:
total 12K
drwxrwsr-x 3 root staff 4.0K 2010-04-13 17:23 .
drwxr-xr-x 5 root root  4.0K 2010-04-05 19:52 ..
drwxrwsr-x 2 root staff 4.0K 2010-04-13 17:23 site-packages

/usr/local/lib/python2.5/site-packages:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2010-04-13 17:23 .
drwxrwsr-x 3 root staff 4.0K 2010-04-13 17:23 ..

/usr/local/lib/python2.6:
total 16K
drwxrwsr-x 4 root staff 4.0K 2010-04-17 13:37 .
drwxr-xr-x 5 root root  4.0K 2010-04-05 19:52 ..
drwxrwsr-x 2 root staff 4.0K 2010-04-05 19:52 dist-packages
drwxrwsr-x 2 root staff 4.0K 2010-04-17 13:37 site-packages

/usr/local/lib/python2.6/dist-packages:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2010-04-05 19:52 .
drwxrwsr-x 4 root staff 4.0K 2010-04-17 13:37 ..

/usr/local/lib/python2.6/site-packages:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2010-04-17 13:37 .
drwxrwsr-x 4 root staff 4.0K 2010-04-17 13:37 ..

/usr/local/sbin:
total 8.0K
drwxr-xr-x  2 root root 4.0K 2010-04-05 19:52 .
drwxr-xr-x 11 root root 4.0K 2010-08-29 01:05 ..

/usr/local/share:
total 52K
drwxr-xr-x 13 root root  4.0K 2010-04-05 19:59 .
drwxr-xr-x 11 root root  4.0K 2010-08-29 01:05 ..
drwxr-xr-x  2 root root  4.0K 2010-11-16 18:39 applications
drwxrwsr-x  2 root staff 4.0K 2010-04-05 19:53 ca-certificates
drwxr-xr-x  2 root root  4.0K 2009-04-20 08:23 desktop-directories
drwxrwsr-x  2 root staff 4.0K 2010-04-05 19:57 fonts
drwxr-xr-x  3 root root  4.0K 2010-04-05 19:59 games
drwxr-xr-x  3 root root  4.0K 2009-04-20 08:23 icons
drwxr-xr-x  2 root root  4.0K 2010-04-05 19:52 man
drwxr-xr-x  3 root root  4.0K 2009-04-20 08:23 mime
drwxrwsr-x  2 root staff 4.0K 2010-04-13 23:10 ppd
drwxrwsr-x  7 root staff 4.0K 2010-04-05 19:54 sgml
drwxrwsr-x  6 root staff 4.0K 2010-04-05 19:54 xml

/usr/local/share/applications:
total 12K
drwxr-xr-x  2 root root 4.0K 2010-11-16 18:39 .
drwxr-xr-x 13 root root 4.0K 2010-04-05 19:59 ..
-rw-r--r--  1 root root   13 2010-11-16 18:39 mimeinfo.cache

/usr/local/share/ca-certificates:
total 8.0K
drwxrwsr-x  2 root staff 4.0K 2010-04-05 19:53 .
drwxr-xr-x 13 root root  4.0K 2010-04-05 19:59 ..

/usr/local/share/desktop-directories:
total 8.0K
drwxr-xr-x  2 root root 4.0K 2009-04-20 08:23 .
drwxr-xr-x 13 root root 4.0K 2010-04-05 19:59 ..

/usr/local/share/fonts:
total 8.0K
drwxrwsr-x  2 root staff 4.0K 2010-04-05 19:57 .
drwxr-xr-x 13 root root  4.0K 2010-04-05 19:59 ..

/usr/local/share/games:
total 12K
drwxr-xr-x  3 root root 4.0K 2010-04-05 19:59 .
drwxr-xr-x 13 root root 4.0K 2010-04-05 19:59 ..
drwxr-xr-x  2 root root 4.0K 2010-04-05 19:59 fortunes

/usr/local/share/games/fortunes:
total 8.0K
drwxr-xr-x 2 root root 4.0K 2010-04-05 19:59 .
drwxr-xr-x 3 root root 4.0K 2010-04-05 19:59 ..

/usr/local/share/icons:
total 12K
drwxr-xr-x  3 root root 4.0K 2009-04-20 08:23 .
drwxr-xr-x 13 root root 4.0K 2010-04-05 19:59 ..
drwxr-xr-x  2 root root 4.0K 2009-04-20 08:23 hicolor

/usr/local/share/icons/hicolor:
total 8.0K
drwxr-xr-x 2 root root 4.0K 2009-04-20 08:23 .
drwxr-xr-x 3 root root 4.0K 2009-04-20 08:23 ..

/usr/local/share/man:
total 8.0K
drwxr-xr-x  2 root root 4.0K 2010-04-05 19:52 .
drwxr-xr-x 13 root root 4.0K 2010-04-05 19:59 ..

/usr/local/share/mime:
total 12K
drwxr-xr-x  3 root root 4.0K 2009-04-20 08:23 .
drwxr-xr-x 13 root root 4.0K 2010-04-05 19:59 ..
drwxr-xr-x  2 root root 4.0K 2009-04-20 08:23 packages

/usr/local/share/mime/packages:
total 8.0K
drwxr-xr-x 2 root root 4.0K 2009-04-20 08:23 .
drwxr-xr-x 3 root root 4.0K 2009-04-20 08:23 ..

/usr/local/share/ppd:
total 8.0K
drwxrwsr-x  2 root staff 4.0K 2010-04-13 23:10 .
drwxr-xr-x 13 root root  4.0K 2010-04-05 19:59 ..

/usr/local/share/sgml:
total 28K
drwxrwsr-x  7 root staff 4.0K 2010-04-05 19:54 .
drwxr-xr-x 13 root root  4.0K 2010-04-05 19:59 ..
drwxrwsr-x  2 root staff 4.0K 2010-04-05 19:54 declaration
drwxrwsr-x  2 root staff 4.0K 2010-04-05 19:54 dtd
drwxrwsr-x  2 root staff 4.0K 2010-04-05 19:54 entities
drwxrwsr-x  2 root staff 4.0K 2010-04-05 19:54 misc
drwxrwsr-x  2 root staff 4.0K 2010-04-05 19:54 stylesheet

/usr/local/share/sgml/declaration:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2010-04-05 19:54 .
drwxrwsr-x 7 root staff 4.0K 2010-04-05 19:54 ..

/usr/local/share/sgml/dtd:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2010-04-05 19:54 .
drwxrwsr-x 7 root staff 4.0K 2010-04-05 19:54 ..

/usr/local/share/sgml/entities:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2010-04-05 19:54 .
drwxrwsr-x 7 root staff 4.0K 2010-04-05 19:54 ..

/usr/local/share/sgml/misc:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2010-04-05 19:54 .
drwxrwsr-x 7 root staff 4.0K 2010-04-05 19:54 ..

/usr/local/share/sgml/stylesheet:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2010-04-05 19:54 .
drwxrwsr-x 7 root staff 4.0K 2010-04-05 19:54 ..

/usr/local/share/xml:
total 24K
drwxrwsr-x  6 root staff 4.0K 2010-04-05 19:54 .
drwxr-xr-x 13 root root  4.0K 2010-04-05 19:59 ..
drwxrwsr-x  2 root staff 4.0K 2010-04-05 19:54 declaration
drwxrwsr-x  2 root staff 4.0K 2010-04-05 19:54 entities
drwxrwsr-x  2 root staff 4.0K 2010-04-05 19:54 misc
drwxrwsr-x  2 root staff 4.0K 2010-04-05 19:54 schema

/usr/local/share/xml/declaration:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2010-04-05 19:54 .
drwxrwsr-x 6 root staff 4.0K 2010-04-05 19:54 ..

/usr/local/share/xml/entities:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2010-04-05 19:54 .
drwxrwsr-x 6 root staff 4.0K 2010-04-05 19:54 ..

/usr/local/share/xml/misc:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2010-04-05 19:54 .
drwxrwsr-x 6 root staff 4.0K 2010-04-05 19:54 ..

/usr/local/share/xml/schema:
total 8.0K
drwxrwsr-x 2 root staff 4.0K 2010-04-05 19:54 .
drwxrwsr-x 6 root staff 4.0K 2010-04-05 19:54 ..

/usr/local/src:
total 8.0K
drwxr-xr-x  2 root root 4.0K 2010-04-05 19:52 .
drwxr-xr-x 11 root root 4.0K 2010-08-29 01:05 ..

/usr/local/ZebraNetworkSystems:
total 12K
drwxr-xr-x  3 root root 4.0K 2010-08-29 01:05 .
drwxr-xr-x 11 root root 4.0K 2010-08-29 01:05 ..
drwxr-xr-x  2 root root 4.0K 2010-08-29 19:54 NeoRouter

/usr/local/ZebraNetworkSystems/NeoRouter:
total 44K
drwxr-xr-x 2 root root 4.0K 2010-08-29 19:54 .
drwxr-xr-x 3 root root 4.0K 2010-08-29 01:05 ..
-rw-r--r-- 1 root root  27K 2010-08-29 19:07 NeoRouter_0_0_1.db
-rw-r--r-- 1 root root 1.3K 2010-08-29 01:05 server.crt
-rw-r--r-- 1 root root  887 2010-08-29 01:05 server.key
kevin@mythbackend:~$

---

### Post by extasy on 2010-11-17
Hmm... my information, or lack of information..

henrik@mythtv:~$ mythpython --version
mythpython: command not found
henrik@mythtv:~$ sudo apt-get install mythpython
Läser paketlistor... Färdig
Bygger beroendeträd
Läser tillståndsinformation... Färdig
E: Kunde inte hitta paketet mythpython
henrik@mythtv:~$ ls -alhR /usr/local
/usr/local:
total 40K
drwxr-xr-x 10 root root 4,0K 2009-10-27 18:15 .
drwxr-xr-x 11 root root 4,0K 2009-10-27 18:18 ..
drwxr-xr-x  2 root root 4,0K 2010-07-31 13:12 bin
drwxr-xr-x  2 root root 4,0K 2009-10-27 18:15 etc
drwxr-xr-x  2 root root 4,0K 2009-10-27 18:15 games
drwxr-xr-x  2 root root 4,0K 2009-10-27 18:15 include
drwxr-xr-x  3 root root 4,0K 2009-10-27 18:15 lib
lrwxrwxrwx  1 root root    9 2009-11-27 20:16 man -> share/man
drwxr-xr-x  2 root root 4,0K 2009-10-27 18:15 sbin
drwxr-xr-x  9 root root 4,0K 2010-11-04 15:40 share
drwxr-xr-x  2 root root 4,0K 2009-10-27 18:15 src

/usr/local/bin:
total 8,0K
drwxr-xr-x  2 root root 4,0K 2010-07-31 13:12 .
drwxr-xr-x 10 root root 4,0K 2009-10-27 18:15 ..

/usr/local/etc:
total 8,0K
drwxr-xr-x  2 root root 4,0K 2009-10-27 18:15 .
drwxr-xr-x 10 root root 4,0K 2009-10-27 18:15 ..

/usr/local/games:
total 8,0K
drwxr-xr-x  2 root root 4,0K 2009-10-27 18:15 .
drwxr-xr-x 10 root root 4,0K 2009-10-27 18:15 ..

/usr/local/include:
total 8,0K
drwxr-xr-x  2 root root 4,0K 2009-10-27 18:15 .
drwxr-xr-x 10 root root 4,0K 2009-10-27 18:15 ..

/usr/local/lib:
total 12K
drwxr-xr-x  3 root root  4,0K 2009-10-27 18:15 .
drwxr-xr-x 10 root root  4,0K 2009-10-27 18:15 ..
drwxrwsr-x  4 root staff 4,0K 2010-11-04 15:42 python2.6

/usr/local/lib/python2.6:
total 16K
drwxrwsr-x 4 root staff 4,0K 2010-11-04 15:42 .
drwxr-xr-x 3 root root  4,0K 2009-10-27 18:15 ..
drwxrwsr-x 2 root staff 4,0K 2009-10-27 18:15 dist-packages
drwxrwsr-x 2 root staff 4,0K 2010-11-04 15:42 site-packages

/usr/local/lib/python2.6/dist-packages:
total 8,0K
drwxrwsr-x 2 root staff 4,0K 2009-10-27 18:15 .
drwxrwsr-x 4 root staff 4,0K 2010-11-04 15:42 ..

/usr/local/lib/python2.6/site-packages:
total 8,0K
drwxrwsr-x 2 root staff 4,0K 2010-11-04 15:42 .
drwxrwsr-x 4 root staff 4,0K 2010-11-04 15:42 ..

/usr/local/sbin:
total 8,0K
drwxr-xr-x  2 root root 4,0K 2009-10-27 18:15 .
drwxr-xr-x 10 root root 4,0K 2009-10-27 18:15 ..

/usr/local/share:
total 36K
drwxr-xr-x  9 root root  4,0K 2010-11-04 15:40 .
drwxr-xr-x 10 root root  4,0K 2009-10-27 18:15 ..
drwxr-xr-x  2 root root  4,0K 2010-11-17 14:45 applications
drwxrwsr-x  2 root staff 4,0K 2009-10-27 18:16 ca-certificates
drwxrwsr-x  2 root staff 4,0K 2009-10-27 18:23 fonts
drwxr-xr-x  3 root root  4,0K 2009-10-27 18:27 games
drwxr-xr-x  2 root root  4,0K 2009-10-27 18:15 man
drwxrwsr-x  7 root staff 4,0K 2009-10-27 18:16 sgml
drwxrwsr-x  6 root staff 4,0K 2010-11-04 15:11 xml

/usr/local/share/applications:
total 12K
drwxr-xr-x 2 root root 4,0K 2010-11-17 14:45 .
drwxr-xr-x 9 root root 4,0K 2010-11-04 15:40 ..
-rw-r--r-- 1 root root   13 2010-11-17 14:45 mimeinfo.cache

/usr/local/share/ca-certificates:
total 8,0K
drwxrwsr-x 2 root staff 4,0K 2009-10-27 18:16 .
drwxr-xr-x 9 root root  4,0K 2010-11-04 15:40 ..

/usr/local/share/fonts:
total 8,0K
drwxrwsr-x 2 root staff 4,0K 2009-10-27 18:23 .
drwxr-xr-x 9 root root  4,0K 2010-11-04 15:40 ..

/usr/local/share/games:
total 12K
drwxr-xr-x 3 root root 4,0K 2009-10-27 18:27 .
drwxr-xr-x 9 root root 4,0K 2010-11-04 15:40 ..
drwxr-xr-x 2 root root 4,0K 2009-10-27 18:27 fortunes

/usr/local/share/games/fortunes:
total 8,0K
drwxr-xr-x 2 root root 4,0K 2009-10-27 18:27 .
drwxr-xr-x 3 root root 4,0K 2009-10-27 18:27 ..

/usr/local/share/man:
total 8,0K
drwxr-xr-x 2 root root 4,0K 2009-10-27 18:15 .
drwxr-xr-x 9 root root 4,0K 2010-11-04 15:40 ..

/usr/local/share/sgml:
total 28K
drwxrwsr-x 7 root staff 4,0K 2009-10-27 18:16 .
drwxr-xr-x 9 root root  4,0K 2010-11-04 15:40 ..
drwxrwsr-x 2 root staff 4,0K 2009-10-27 18:16 declaration
drwxrwsr-x 2 root staff 4,0K 2009-10-27 18:16 dtd
drwxrwsr-x 2 root staff 4,0K 2009-10-27 18:16 entities
drwxrwsr-x 2 root staff 4,0K 2009-10-27 18:16 misc
drwxrwsr-x 2 root staff 4,0K 2009-10-27 18:16 stylesheet

/usr/local/share/sgml/declaration:
total 8,0K
drwxrwsr-x 2 root staff 4,0K 2009-10-27 18:16 .
drwxrwsr-x 7 root staff 4,0K 2009-10-27 18:16 ..

/usr/local/share/sgml/dtd:
total 8,0K
drwxrwsr-x 2 root staff 4,0K 2009-10-27 18:16 .
drwxrwsr-x 7 root staff 4,0K 2009-10-27 18:16 ..

/usr/local/share/sgml/entities:
total 8,0K
drwxrwsr-x 2 root staff 4,0K 2009-10-27 18:16 .
drwxrwsr-x 7 root staff 4,0K 2009-10-27 18:16 ..

/usr/local/share/sgml/misc:
total 8,0K
drwxrwsr-x 2 root staff 4,0K 2009-10-27 18:16 .
drwxrwsr-x 7 root staff 4,0K 2009-10-27 18:16 ..

/usr/local/share/sgml/stylesheet:
total 8,0K
drwxrwsr-x 2 root staff 4,0K 2009-10-27 18:16 .
drwxrwsr-x 7 root staff 4,0K 2009-10-27 18:16 ..

/usr/local/share/xml:
total 24K
drwxrwsr-x 6 root staff 4,0K 2010-11-04 15:11 .
drwxr-xr-x 9 root root  4,0K 2010-11-04 15:40 ..
drwxrwsr-x 2 root staff 4,0K 2010-11-04 15:11 declaration
drwxrwsr-x 2 root staff 4,0K 2010-11-04 15:11 entities
drwxrwsr-x 2 root staff 4,0K 2010-11-04 15:11 misc
drwxrwsr-x 2 root staff 4,0K 2010-11-04 15:11 schema

/usr/local/share/xml/declaration:
total 8,0K
drwxrwsr-x 2 root staff 4,0K 2010-11-04 15:11 .
drwxrwsr-x 6 root staff 4,0K 2010-11-04 15:11 ..

/usr/local/share/xml/entities:
total 8,0K
drwxrwsr-x 2 root staff 4,0K 2010-11-04 15:11 .
drwxrwsr-x 6 root staff 4,0K 2010-11-04 15:11 ..

/usr/local/share/xml/misc:
total 8,0K
drwxrwsr-x 2 root staff 4,0K 2010-11-04 15:11 .
drwxrwsr-x 6 root staff 4,0K 2010-11-04 15:11 ..

/usr/local/share/xml/schema:
total 8,0K
drwxrwsr-x 2 root staff 4,0K 2010-11-04 15:11 .
drwxrwsr-x 6 root staff 4,0K 2010-11-04 15:11 ..

/usr/local/src:
total 8,0K
drwxr-xr-x  2 root root 4,0K 2009-10-27 18:15 .
drwxr-xr-x 10 root root 4,0K 2009-10-27 18:15 ..

---

### Post by tgm4883 on 2010-11-17
extasy, you forgot this

```
dpkg -S /usr/share/mythtv/metadata/Movie/tmdb.py
dpkg -l libmyth-python libmythtv-perl mythtv-frontend mythtv-backend mythtv-common mythvideo
```


iitywygms, whats the output of

```
which mythpython
```

---

### Post by extasy on 2010-11-17
henrik@mythtv:~$ dpkg -S /usr/share/mythtv/metadata/Movie/tmdb.py
mythtv-backend: /usr/share/mythtv/metadata/Movie/tmdb.py
henrik@mythtv:~$ dpkg -l libmyth-python libmythtv-perl mythtv-frontend mythtv-backend mythtv-common mythvideo
Önskat=Okänd(U)/Installera(I)/Radera(R)/Rensa(P)/Håll(H)
| Status=Ej(N)/Inst.(I)/Konf.(C)/Uppack.(U)/Missl.(F)/Delvis(H)/Vänt.utl(W)/Föres.utl(T)
|/ Fel?Inget(=)/Ominstallera(R)/Båda(X) (Status,Fel: versaler=illa)
||/ Namn                                 Version                              Beskrivning
+++-====================================-====================================-========================================================================================
ii  libmyth-python                       2:0.23.1+fixes26231-0ubuntu2         A python library to access some MythTV features
ii  libmythtv-perl                       1:0.24.0+fixes27251-0ubuntu0+mythbun A PERL library to access some MythTV features
ii  mythtv-backend                       1:0.24.0+fixes27251-0ubuntu0+mythbun A personal video recorder application (server)
ii  mythtv-common                        1:0.24.0+fixes27251-0ubuntu0+mythbun A personal video recorder application (common data)
ii  mythtv-frontend                      1:0.24.0+fixes27251-0ubuntu0+mythbun A personal video recorder application (client)
ii  mythvideo                            1:0.24.0+fixes27251-0ubuntu0+mythbun A generic video player frontend module for MythTV

---

### Post by extasy on 2010-11-17
Hmm..

Did some changes purged the old libmyth-python and then reinstalled it..


ii  libmyth-python                       1:0.24.0+fixes27251-0ubuntu0+mythbun A python library to access some MythTV features
ii  libmythtv-perl                       1:0.24.0+fixes27251-0ubuntu0+mythbun A PERL library to access some MythTV features
ii  mythtv-backend                       1:0.24.0+fixes27251-0ubuntu0+mythbun A personal video recorder application (server)
ii  mythtv-common                        1:0.24.0+fixes27251-0ubuntu0+mythbun A personal video recorder application (common data)
ii  mythtv-frontend                      1:0.24.0+fixes27251-0ubuntu0+mythbun A personal video recorder application (client)
ii  mythvideo                            1:0.24.0+fixes27251-0ubuntu0+mythbun A generic video player frontend module for MythTV

---

### Post by extasy on 2010-11-17
And it worked!!!!

Perfect!! Thank you!

---

### Post by tgm4883 on 2010-11-17
> **extasy said:**
> henrik@mythtv:~$ dpkg -S /usr/share/mythtv/metadata/Movie/tmdb.py
mythtv-backend: /usr/share/mythtv/metadata/Movie/tmdb.py
henrik@mythtv:~$ dpkg -l libmyth-python libmythtv-perl mythtv-frontend mythtv-backend mythtv-common mythvideo
Önskat=Okänd(U)/Installera(I)/Radera(R)/Rensa(P)/Håll(H)
| Status=Ej(N)/Inst.(I)/Konf.(C)/Uppack.(U)/Missl.(F)/Delvis(H)/Vänt.utl(W)/Föres.utl(T)
|/ Fel?Inget(=)/Ominstallera(R)/Båda(X) (Status,Fel: versaler=illa)
||/ Namn                                 Version                              Beskrivning
+++-====================================-====================================-========================================================================================
ii  libmyth-python                       2:0.23.1+fixes26231-0ubuntu2         A python library to access some MythTV features
ii  libmythtv-perl                       1:0.24.0+fixes27251-0ubuntu0+mythbun A PERL library to access some MythTV features
ii  mythtv-backend                       1:0.24.0+fixes27251-0ubuntu0+mythbun A personal video recorder application (server)
ii  mythtv-common                        1:0.24.0+fixes27251-0ubuntu0+mythbun A personal video recorder application (common data)
ii  mythtv-frontend                      1:0.24.0+fixes27251-0ubuntu0+mythbun A personal video recorder application (client)
ii  mythvideo                            1:0.24.0+fixes27251-0ubuntu0+mythbun A generic video player frontend module for MythTV

You don't have the 0.24 bindings installed (libmyth-python). It didn't upgrade because you were using JYA's repos and his version numbering is different. You need to manually remove libmyth-python then reinstall it

---

### Post by tgm4883 on 2010-11-17
iitywygms, I was talking with the developer of tmdb.py

```
please run tmdb.py -v and tell me what the <version>0.21</version> tags says
```

---

### Post by iitywygms on 2010-11-17
Frontend

kevin@mythbigscreen:~$ which mythpython

/usr/bin/mythpython


Backend

kevin@mythbackend:/usr/share/mythtv/metadata/Movie$ ./tmdb.py -v<grabber>

  <name>TheMovieDB.org</name>

  <author>R.D.Vaughan</author>

  <thumbnail>tmdb.png</thumbnail>

  <command>tmdb.py</command>

  <type>movie</type>

  <description>Search and metadata downloads for themoviedb.org</description>

  <version>0.21</version>

</grabber>


kevin@mythbackend:/usr/share/mythtv/metadata/Movie$ which mythpython

/usr/bin/mythpython

---

### Post by iitywygms on 2010-11-17
more info.

I read on the mailing list this may be a clue.

kevin@mythbackend:~$ sudo mythbuntu-control-centre
CRITICAL: MythTV python bindings could not be imported, error(cannot import name MythDBBase)

WARNING: Error loading plugin <class 'mirobridgeconfig.MirobridgeconfigPlugin'>
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/MythbuntuControlCentre/plugin.py", line 75, in find_plugin_instances
    self._instances[plugin] = plugin()
  File "/usr/share/mythbuntu/plugins/python/mirobridgeconfig.py", line 88, in __init__
    self.mbfunctions = MirobridgeConfigFunctions(self.logger)
  File "/usr/share/mythbuntu/plugins/python/mirobridgeconfig.py", line 392, in __init__
    self.accessMythDB() # Test that this is a BE
  File "/usr/share/mythbuntu/plugins/python/mirobridgeconfig.py", line 468, in accessMythDB
    raise MirobridgeconfigPlugin_error(errormsg)
MirobridgeconfigPlugin_error: MythTV python bindings could not be imported, error(cannot import name MythDBBase)

Reading package lists... Done
Building dependency tree       
Reading state information... Done

---

### Post by tgm4883 on 2010-11-17
> **iitywygms said:**
> more info.

I read on the mailing list this may be a clue.

kevin@mythbackend:~$ sudo mythbuntu-control-centre
CRITICAL: MythTV python bindings could not be imported, error(cannot import name MythDBBase)

WARNING: Error loading plugin <class 'mirobridgeconfig.MirobridgeconfigPlugin'>
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/MythbuntuControlCentre/plugin.py", line 75, in find_plugin_instances
    self._instances[plugin] = plugin()
  File "/usr/share/mythbuntu/plugins/python/mirobridgeconfig.py", line 88, in __init__
    self.mbfunctions = MirobridgeConfigFunctions(self.logger)
  File "/usr/share/mythbuntu/plugins/python/mirobridgeconfig.py", line 392, in __init__
    self.accessMythDB() # Test that this is a BE
  File "/usr/share/mythbuntu/plugins/python/mirobridgeconfig.py", line 468, in accessMythDB
    raise MirobridgeconfigPlugin_error(errormsg)
MirobridgeconfigPlugin_error: MythTV python bindings could not be imported, error(cannot import name MythDBBase)

Reading package lists... Done
Building dependency tree       
Reading state information... Done

Nope, try updating to today's autobuilds. I got an error when upgrading here due to the file being in two packages but doing the upgrade twice allowed me to upgrade. Once you upgrade, check if the issue still exists

---

### Post by RDV on 2010-11-17
iitywygms,

This message does not have anything to do with the tmdb.py issue you are having "sudo mythbuntu-control-centre
CRITICAL: MythTV python bindings could not be imported, error(cannot import name MythDBBase)".

That error is from the jamu and mirobridge MCC (Mythbuntu Control Centre) plugins. I am currently working to resolve that issue. The actual jamu.py and mirobridge.py scripts do work but the ancillary MCC plugins do not.

Now for the tmdb.py issue you are having, it does appear you have the correct 0.24 MythTV version of tmdb.py installed. From a terminal please run and post the results from:
> /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M "The Matrix"

I once had a user that used a proxy server which had to be reset before the grabber scripts would work. Do you have a proxy that needs to be restarted?

You can also try the TV series grabber as a cross reference and post its results:
> /usr/share/mythtv/metadata/Television/ttvdb.py -l en -M "The Event"

We will see if those tests give us any better clues of what is going on.

---

### Post by iitywygms on 2010-11-17
Cannot thank you all enough.  The hard work and effort you developers do is awesome.
In other words, today's update fixed it. :) :popcorn:
Thanks again.

If it matters.  Today's update required two tries, the second attempt needing the -f option.

---

### Post by iitywygms on 2010-11-17
One other note.  This update also fixed the issue of mythnetvision not update site maps. :P
I will update that thread as well.

---

### Post by RDV on 2010-11-17
If it is fixed then please change the thread title to [SOLVED] .....

Glad to hear your grabbers are working.

---

### Post by iitywygms on 2010-11-17
> **RDV said:**
> If it is fixed then please change the thread title to [SOLVED] .....

Glad to hear your grabbers are working.

I would but not my thread. 
Thanks again!

---

### Post by iitywygms on 2010-11-22
Would you believe it is back?
But it is.
Here is the error log.

2010-11-21 22:42:24.943 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@mythbackend/D2/share/videos/)
2010-11-21 22:42:25.019 Hash e0917852e003a53c already exists in the database, updating record 423 with new filename Search-All/player-uri=mgidcmsmvideocom$
2010-11-21 22:42:25.028 Hash e0917852e003a53c already exists in the database, updating record 423 with new filename Search-All/player-uri=mgidcmsmvideocom$
2010-11-21 22:42:25.050 Adding :  : The_Martix.avi : 939691ae11e60e02
2010-11-21 22:42:25.076 Adding :  : The_Matrix_Reloaded.avi : ae39f930d2b1c6b2
2010-11-21 22:42:25.098 Adding :  : The_Matrix_Revolutions.avi : d73d11e1359019ff
2010-11-21 22:42:25.371 Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M The Matrix Revolutions
2010-11-21 22:42:25.390 Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M The Matrix Reloaded
2010-11-21 22:42:25.421 Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M The Martix
2010-11-21 22:42:25.570 No results found for The Matrix Revolutions 0 0
2010-11-21 22:42:25.576 No results found for The Matrix Reloaded 0 0
2010-11-21 22:42:25.581 No results found for The Martix 0 0

---

### Post by tgm4883 on 2010-11-22
> **iitywygms said:**
> Would you believe it is back?
But it is.
Here is the error log.

2010-11-21 22:42:24.943 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@mythbackend/D2/share/videos/)
2010-11-21 22:42:25.019 Hash e0917852e003a53c already exists in the database, updating record 423 with new filename Search-All/player-uri=mgidcmsmvideocom$
2010-11-21 22:42:25.028 Hash e0917852e003a53c already exists in the database, updating record 423 with new filename Search-All/player-uri=mgidcmsmvideocom$
2010-11-21 22:42:25.050 Adding :  : The_Martix.avi : 939691ae11e60e02
2010-11-21 22:42:25.076 Adding :  : The_Matrix_Reloaded.avi : ae39f930d2b1c6b2
2010-11-21 22:42:25.098 Adding :  : The_Matrix_Revolutions.avi : d73d11e1359019ff
2010-11-21 22:42:25.371 Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M The Matrix Revolutions
2010-11-21 22:42:25.390 Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M The Matrix Reloaded
2010-11-21 22:42:25.421 Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M The Martix
2010-11-21 22:42:25.570 No results found for The Matrix Revolutions 0 0
2010-11-21 22:42:25.576 No results found for The Matrix Reloaded 0 0
2010-11-21 22:42:25.581 No results found for The Martix 0 0

Does /usr/share/mythtv/metadata/Movie/tmdb.py exist on the frontend?

---

### Post by iitywygms on 2010-11-22
no it does not. should it?
i thought this ran off the backend machine.
I do not recall it ever being on the frontend machine.

---

### Post by tgm4883 on 2010-11-22
> **iitywygms said:**
> no it does not. should it?
i thought this ran off the backend machine.
I do not recall it ever being on the frontend machine.

Yep it should be on the frontend. Can you post the output of 

> dpkg -l mythtv-frontend
dpkg -l mythtv-common
dpkg -l libmyth-python


---

### Post by iitywygms on 2010-11-22
Okay will do when I get home. I am working now, lol.
Anyway, it should be the same as what I posted on #14 of this thread.
How in the *&^% did it work if I never had it installed on the frontend before????????
I must be losing it.
I should add that I switched to the JY Avenard repos.  Trying to fix a audio issue.

---

### Post by tgm4883 on 2010-11-22
> **iitywygms said:**
> Okay will do when I get home. I am working now, lol.
Anyway, it should be the same as what I posted on #14 of this thread.
How in the *&^% did it work if I never had it installed on the frontend before????????
I must be losing it.
I should add that I switched to the JY Avenard repos.  Trying to fix a audio issue.

If you switched to the JYA repos, then all bets are off. I don't deal with that packaging so I'm unsure if there is an issue with it. I'll ping him about it, but you should answer the questions I asked anyway.

---

### Post by iitywygms on 2010-11-22
Okay, I understand.  I thought they were basically all the same.
If i may ask, where should one post with questions if using the JYA repos?
The mythtv mailing list?
Thanks for the info.

---

### Post by tgm4883 on 2010-11-22
> **iitywygms said:**
> Okay, I understand.  I thought they were basically all the same.
If i may ask, where should one post with questions if using the JYA repos?
The mythtv mailing list?
Thanks for the info.

likely the mythtv-users mailing list

---

### Post by iitywygms on 2010-11-22
What packages would I need to install on the frontend for tmdb.py to be present?

---

### Post by nickrout on 2010-11-22
> **iitywygms said:**
> What packages would I need to install on the frontend for tmdb.py to be present?

[http://packages.ubuntu.com/search?searchon=contents&keywords=tmdb.py&mode=exactfilename&suite=maverick&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=tmdb.py&mode=exactfilename&suite=maverick&arch=any)

---

### Post by tgm4883 on 2010-11-22
> **nickrout said:**
> [http://packages.ubuntu.com/search?searchon=contents&keywords=tmdb.py&mode=exactfilename&suite=maverick&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=tmdb.py&mode=exactfilename&suite=maverick&arch=any)

The issue with that is that it doesn't search neither the mythtv-updates repository nor JYA's repository.

Those were moved to mythtv-common in the mythtv-updates repository, but I'm not sure about JYA's

---

### Post by nickrout on 2010-11-22
so the packaging in mythbuntu repos is different to the ubuntu packaging?

*sigh* - wonders never cease.

---

### Post by iitywygms on 2010-11-22
> **tgm4883 said:**
> Yep it should be on the frontend. Can you post the output of

kevin@mythbigscreen:/var/log/mythtv$ dpkg -l mythtv-frontend
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                 Version              Description
+++-====================-====================-========================================================
ii  mythtv-frontend      2:0.24.0+fixes27305- A personal video recorder application (client)
kevin@mythbigscreen:/var/log/mythtv$ dpkg -l mythtv-common
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                 Version              Description
+++-====================-====================-========================================================
ii  mythtv-common        2:0.24.0+fixes27305- A personal video recorder application (common data)
kevin@mythbigscreen:/var/log/mythtv$ dpkg -l libmyth-python 
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                 Version              Description
+++-====================-====================-========================================================
ii  libmyth-python       2:0.24.0+fixes27305- A python library to access some MythTV features
kevin@mythbigscreen:/var/log/mythtv$ 

I tried reinstalling mythvideo on my frontend and it did not install tmdb.py.
I am confused.

---

### Post by nickrout on 2010-11-22
have you tried ```
locate tmdb.py
```

---

### Post by iitywygms on 2010-11-22
Backend finds

/usr/share/mythtv/metadata/Movie/tmdb.py

Frontend finds nothing.

Why is this installed on the backend machine if the frontend machine uses it?

I am really confused as to why it worked a week ago, but not now.
Yes, I switched to JYA repos.  But that should not remove anything right?
And why is it not getting installed now?  was it removed?  Was it ever installed on the frontend?

I guess I need to learn a lesson from this and not jack with things when they are working okay.  I moved from .23.1 fixes to .24, and have regretted it the whole way.  I guess switching sources is a bad idea to.

---

### Post by iitywygms on 2010-11-22
Okay, I "fixed" it by copying all the stuff from the metadata directory on the backend to the frontend machine.
Works fine now.
So, when I update, will it all get blown away again?

---

### Post by tgm4883 on 2010-11-22
> **nickrout said:**
> so the packaging in mythbuntu repos is different to the ubuntu packaging?

*sigh* - wonders never cease.

:roll:  Yea the packaging is different. Do you happen to care why? 

You see, when we did the packaging for Ubuntu (we do all the mythtv packages for Ubuntu), it was great. Then 0.24 got released and a few things happened.

1) we found that there were different circumstances that the files were needed (new features and all). 

2) the scripts were moved upstream

I suppose we could be set in our ways and never fix packaging bugs either but I find that users tend to like bug fixes.

---

### Post by tgm4883 on 2010-11-22
> **iitywygms said:**
> Okay, I "fixed" it by copying all the stuff from the metadata directory on the backend to the frontend machine.
Works fine now.
So, when I update, will it all get blown away again?

Nope, but if the packaging gets fixed and it does try to put files there it might have issues installing it

---

### Post by iitywygms on 2010-11-22
I am sure you have better things to do than answer my novice questions.  but if it (grabbing metadata) was working last week, it had to of been installed on the frontend machine right?  If that is true, how the heck did it get removed?

---

### Post by nickrout on 2010-11-22
> **tgm4883 said:**
> :roll:  Yea the packaging is different. Do you happen to care why? 

You see, when we did the packaging for Ubuntu (we do all the mythtv packages for Ubuntu), it was great. Then 0.24 got released and a few things happened.

1) we found that there were different circumstances that the files were needed (new features and all). 

2) the scripts were moved upstream

I suppose we could be set in our ways and never fix packaging bugs either but I find that users tend to like bug fixes.

So the difference is actually betyween 0.23.1 and 0.24.

I can accept that:)

No criticism of that at all.

What I really hate (and what seems to cause a LOT of hassles) is that *buntu seems to come out around the time myth is in release candidate, meaning the particular iteration of *buntu doesn't have an upgrade path to the next version, unless you know about the repos.

---

### Post by tgm4883 on 2010-11-22
> **iitywygms said:**
> I am sure you have better things to do than answer my novice questions.  but if it (grabbing metadata) was working last week, it had to of been installed on the frontend machine right?  If that is true, how the heck did it get removed?

No worries. It may be a little easier to think of it like this.

A package just contains a bunch of files to be installed. When a package is upgraded, it removes the currently installed files and replaces it with the files in the upgraded package. If the new package doesn't contain all of the files in the previous package, they aren't installed (because they don't exist in the new package). So likely the files aren't in JYA's packages due to a packaging bug.

---

### Post by tgm4883 on 2010-11-22
> **nickrout said:**
> So the difference is actually betyween 0.23.1 and 0.24.

I can accept that:)

No criticism of that at all.

What I really hate (and what seems to cause a LOT of hassles) is that *buntu seems to come out around the time myth is in release candidate, meaning the particular iteration of *buntu doesn't have an upgrade path to the next version, unless you know about the repos.

Yea the dev cycle for mythtv is suppose to be about 8 months so that does seem to happen alot. The Mythbuntu team does recommend using the mythbuntu-repos package to keep up to date with fixes. Unfortunatly we are unable to activate that by default

---

### Post by iitywygms on 2010-11-22
Thank you.  The package must be missing on "frontend only" installs.  I keep the backend and the frontend on the same builds.  My backend always has the tmdb.py installed.
I guess I should report this on the mailing list.
Thank you so much for your time.

---

### Post by extasy on 2010-11-30
Yesterady after the latest daily the metada died on me.


 dpkg -l libmyth-python libmythtv-perl mythtv-frontend mythtv-backend mythtv-common mythvideo
Önskat=Okänd(U)/Installera(I)/Radera(R)/Rensa(P)/Håll(H)
| Status=Ej(N)/Inst.(I)/Konf.(C)/Uppack.(U)/Missl.(F)/Delvis(H)/Vänt.utl(W)/Föres.utl(T)
|/ Fel?Inget(=)/Ominstallera(R)/Båda(X) (Status,Fel: versaler=illa)
||/ Namn                                     Version                                  Beskrivning
+++-========================================-========================================-================================================================================================
ii  libmyth-python                           1:0.24.0+fixes27364-0ubuntu0+mythbuntu1  A python library to access some MythTV features
ii  libmythtv-perl                           1:0.24.0+fixes27364-0ubuntu0+mythbuntu1  A PERL library to access some MythTV features
ii  mythtv-backend                           1:0.24.0+fixes27364-0ubuntu0+mythbuntu1  A personal video recorder application (server)
ii  mythtv-common                            1:0.24.0+fixes27364-0ubuntu0+mythbuntu1  A personal video recorder application (common data)
ii  mythtv-frontend                          1:0.24.0+fixes27364-0ubuntu0+mythbuntu1  A personal video recorder application (client)
ii  mythvideo                                1:0.24.0+fixes27364-0ubuntu0+mythbuntu1  A generic video player frontend module for MythTV

dpkg -S /usr/share/mythtv/metadata/Movie/tmdb.py
mythtv-common: /usr/share/mythtv/metadata/Movie/tmdb.py


Any Ideas?

---

### Post by extasy on 2010-11-30
Never mind, updated to the most resent version of daily and the problem was fixed. It now grabs art as it should.

---

