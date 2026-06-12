---
title: "No Text or graphics on trunk install"
date: 2009-06-08
forum: Mythbuntu
---

### Post by mitchell2345 on 2009-06-08
Hi,

I just moved from CentOS/ATrpms trunk build to ubuntu weekly builds.

I successfully imported my database and got .22 up and running.  

the issue is when I run the frontend i see no text or graphics unless i am running G.A.N.T.

Here are the packages I have installed:
```
mitchell@mythtv:~$ dpkg -l |grep myth
ii  gtk2-engines-mythbuntu                     0.4-0ubuntu2                          Mythbuntu GTK+ 2.x Theme
rc  libmyth-0.21-0                             0.21.0+fixes19961-0ubuntu8            Common library code for MythTV and add-on mo
ii  libmyth-0.22-0                             0.21.0+trunk20650-0ubuntu0+mythbuntu3 Common library code for MythTV and add-on mo
ii  libmyth-perl                               0.21.0+trunk20650-0ubuntu0+mythbuntu3 A PERL library to access some MythTV feature
ii  libmyth-python                             0.21.0+trunk20650-0ubuntu0+mythbuntu3 A python library to access some MythTV featu
ii  mytharchive-data                           0.21.0+trunk20650-0ubuntu0+mythbuntu3 create and burn DVD's from MythTV - data fil
rc  mythbuntu-apple-trailers                   0.2-0ubuntu1                          Plugin providing Apple.com Movie Trailers fo
ii  mythbuntu-artwork-usplash                  0.8-0ubuntu2                          mythbuntu artwork for usplash
ii  mythbuntu-common                           0.26-0ubuntu1                         Mythbuntu application support functions
ii  mythbuntu-control-centre                   0.37-0ubuntu1                         Mythbuntu Configuration Application
ii  mythbuntu-default-settings                 0.78-0ubuntu1                         default settings for Mythbuntu
ii  mythbuntu-diskless-server                  0.9-0ubuntu1                          Basic Mythbuntu-diskless server environment
ii  mythbuntu-diskless-server-standalone       0.9-0ubuntu1                          Mythbuntu-diskless server environment with D
ii  mythbuntu-gdm-theme                        0.3-0ubuntu2                          mythbuntu gdm greeter theme
ii  mythbuntu-lirc-generator                   0.21-0ubuntu1                         Mythbuntu Lirc Configuration Generator
ii  mythbuntu-log-grabber                      0.3-0ubuntu1                          Tool to gather diagnostic data for Mythbuntu
ii  mythbuntu-repos                            1-0ubuntu0+mythbuntu8                 Mythbuntu repos installer
ii  mythtv                                     0.21.0+trunk20650-0ubuntu0+mythbuntu3 A personal video recorder application (clien
ii  mythtv-backend                             0.21.0+trunk20650-0ubuntu0+mythbuntu3 A personal video recorder application (serve
ii  mythtv-backend-master                      0.21.0+trunk20650-0ubuntu0+mythbuntu3 Metapackage to setup and configure a "Master
ii  mythtv-common                              0.21.0+trunk20650-0ubuntu0+mythbuntu3 A personal video recorder application (commo
ii  mythtv-database                            0.21.0+trunk20650-0ubuntu0+mythbuntu3 A personal video recorder application (datab
ii  mythtv-doc                                 0.21.0+trunk20650-0ubuntu0+mythbuntu3 A personal video recorder application (docum
ii  mythtv-frontend                            0.21.0+trunk20650-0ubuntu0+mythbuntu3 A personal video recorder application (clien
ii  mythtv-theme-blootube-osd                  1:0.21.0-0ubuntu2                     The Blootube MythTV OSD
ii  mythtv-theme-blootube-wide                 1:0.21.0-0ubuntu1                     The Blootube MythTV theme (widescreen)
rc  mythtv-theme-mythbuntu                     0.20080421                            default MythTV theme used in Mythbuntu
ii  mythtv-themes                              0.21.0+trunk20650-0ubuntu0+mythbuntu3 Additional themes metapackage for MythTV
ii  mythtv-transcode-utils                     0.21.0+trunk20650-0ubuntu0+mythbuntu3 Utilities used for transcoding MythTV tasks
ii  mythtvfs                                   0.5.2-2build1                         userspace filesystem client for MythTV
ii  mythweb                                    0.21.0+trunk20650-0ubuntu0+mythbuntu3 Web interface add-on module for MythTV

```

I see no clues in the logs either.

using a Nvidia 8400GS with restricted driver installed.

Any ideas?

Thanks,
Mitchell

---

### Post by mitchell2345 on 2009-06-08
Ok it seems to be something wrong with the packages. I downloaded straight from the upstream dev site and it works fine

svn co [http://svn.mythtv.org/svn/trunk/themes/blootube-wide](http://svn.mythtv.org/svn/trunk/themes/blootube-wide)
mv blootube-wide /usr/share/mythtv/themes/

I get pics and text.  there must be an issue with the debs.

Can this get corrected so others dont have to fight with it?

Thanks,
Mitchell

---

