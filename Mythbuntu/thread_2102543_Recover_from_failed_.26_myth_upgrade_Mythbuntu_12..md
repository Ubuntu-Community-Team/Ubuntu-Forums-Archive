---
title: "Recover from failed .26 myth upgrade Mythbuntu 12.04"
date: 2013-01-07
forum: Mythbuntu
---

### Post by frego on 2013-01-07
I have a working Mythbuntu 12.04, 64bit install I was running successfully with Myth .25.  I enabled the .26 repos in MCC and the upgrade failed.  I reverted to .25 repos and now my apt-get upgrade also fails.  I've tried apt-get -f and autoclean, but no luck.  

Here is the error I receive:


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  mythbrowser mythgallery mythmusic mythnews mythtv-backend mythtv-common
  mythtv-frontend mythtv-transcode-utils mythweather mythweb
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up mythtv-database (2:0.26.0+fixes.20130104.72bca07-0ubuntu0mythbuntu2) ...
ERROR 1046 (3D000) at line 22: No database selected
dpkg: error processing mythtv-database (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database; however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend-master:
 mythtv-backend-master depends on mythtv-database; however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv-backend-master (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 mythtv-database
 mythtv
 mythtv-backend-master
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any ideas on how to recover my system?

---

### Post by Lester_Burnham on 2013-01-07
Hi,

Looks similar to my problems.
Have a look here [http://www.pcmediacenter.com.au/forum/topic/46990-mythbuntu-1204-upgrade-mythtv-025-to-026/#entry332628](http://www.pcmediacenter.com.au/forum/topic/46990-mythbuntu-1204-upgrade-mythtv-025-to-026/#entry332628)

I also noticed the 0.25 repo still ticked in repositories and there was a mythtv-common or libmythtv for 0.25.3 still installed.

Lester

---

### Post by frego on 2013-01-07
Good post, Lester!  Editing mythtv-database.postinstall with the relevant connection info got me past that broken package management hurdle.  Also, looked at this thread that I shall include to help others that may stumble on this:  [http://www.gossamer-threads.com/lists/mythtv/users/529396](http://www.gossamer-threads.com/lists/mythtv/users/529396)

---

