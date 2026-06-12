---
title: "Latest update broke my system."
date: 2011-05-10
forum: Mythbuntu
---

### Post by extasy on 2011-05-10
After doing a update with the 0.24 fixes Mythfrontend wont start. get this error:


2011-05-10 20:21:29.145 Using Frameless Window
2011-05-10 20:21:29.145 Using Full Screen Window
2011-05-10 20:21:29.150 Using the Qt painter
2011-05-10 20:21:29.486 This application is not compatible with the installed MythTV libraries. Please recompile after a make distclean
2011-05-10 20:21:29.486 Failed to init MythContext, exiting.
2011-05-10 20:21:29.486 Deleting UPnP client...
2011-05-10 20:21:29.486 This application is not compatible with the installed MythTV libraries. Please recompile after a make distclean


I'm on a 9.10 ubuntu base system.

---

### Post by ian dobson on 2011-05-10
Hi,

What do you see when you do a dpkg -l | grep myth

It looks as if the mythlib was not updated.

Regards
Ian Dobson

---

### Post by extasy on 2011-05-10
this is what I get:


henrik@mythtv:/var/log/mythtv$ dpkg -l | grep myth
ii  libmyth-0.22-0                       2:0.22.0-fixes24035-0ubuntu6                       Common library code for MythTV and add-on modules (runtime)
rc  libmyth-0.23-0                       2:0.23.1+fixes26231-0ubuntu2                       Common library code for MythTV and add-on modules (runtime)
ii  libmyth-0.24-0                       2:0.24.0+fixes.20110510.5461754-0ubuntu0mythbuntu1 Common library code for MythTV and add-on modules (runtime)
ii  libmyth-dev                          2:0.24.0+fixes.20110510.5461754-0ubuntu0mythbuntu1 Common library code for MythTV and add-on modules (development)
ii  libmyth-python                       2:0.24.0+fixes.20110510.5461754-0ubuntu0mythbuntu1 A python library to access some MythTV features
ii  libmythtv-perl                       2:0.24.0+fixes.20110510.5461754-0ubuntu0mythbuntu1 A PERL library to access some MythTV features
ii  mytharchive                          2:0.24.0+fixes.20110206.1a69c92-0ubuntu0mythbuntu1 create and burn DVD's from MythTV - binary file
ii  mythbuntu-common                     0.50-0ubuntu1                                      Mythbuntu application support functions
ii  mythbuntu-control-centre             0.62-0ubuntu1                                      Mythbuntu Configuration Application
ii  mythbuntu-default-settings           0.96-0ubuntu1                                      default settings for Mythbuntu
ii  mythbuntu-gdm-theme                  0.6-0ubuntu1                                       Mythbuntu GDM theme
ii  mythbuntu-lirc-generator             0.25-0ubuntu1~ppa1                                 Mythbuntu Lirc Configuration Generator
ii  mythbuntu-log-grabber                0.7-0ubuntu2                                       Mythbuntu repos installer
ii  mythbuntu-repos                      9.2-0ubuntu0+mythbuntu~auto20110509004159          Mythbuntu repository installer
ii  mythgallery                          2:0.24.0+fixes.20110206.1a69c92-0ubuntu0mythbuntu1 Image gallery/slideshow add-on module for MythTV
ii  mythmovies                           1:0.24.0+fixes27204-0ubuntu0+mythbuntu1            Find nearby movies and cinema listings
ii  mythmusic                            2:0.24.0+fixes.20110206.1a69c92-0ubuntu0mythbuntu1 Music add-on module for MythTV
ii  mythtv                               2:0.24.0+fixes.20110510.5461754-0ubuntu0mythbuntu1 A personal video recorder application (client and server)
ii  mythtv-backend                       2:0.24.0+fixes.20110510.5461754-0ubuntu0mythbuntu1 A personal video recorder application (server)
ii  mythtv-backend-master                2:0.24.0+fixes.20110510.5461754-0ubuntu0mythbuntu1 Metapackage to setup and configure a "Master Backend" profile of
ii  mythtv-common                        2:0.24.0+fixes.20110510.5461754-0ubuntu0mythbuntu1 A personal video recorder application (common data)
ii  mythtv-database                      2:0.24.0+fixes.20110510.5461754-0ubuntu0mythbuntu1 A personal video recorder application (database)
ii  mythtv-doc                           2:0.24.0+fixes.20110510.5461754-0ubuntu0mythbuntu1 A personal video recorder application (documentation)
ii  mythtv-frontend                      2:0.24.0+fixes.20110206.1a69c92-0ubuntu0mythbuntu1 A personal video recorder application (client)
ii  mythtv-status                        0.9.2-3                                            Show the status of a MythTV backend
ii  mythtv-theme-arclight                2:0.24.0+fixes.20110510.5461754-0ubuntu0mythbuntu1 The arclight MythTV Theme
ii  mythtv-theme-blootube-osd            1:0.23.0+fixes23872-0ubuntu1                       The blootube-osd MythTV Theme
ii  mythtv-theme-blueosd                 1:0.23.0+fixes23872-0ubuntu1                       The blueosd MythTV Theme
ii  mythtv-theme-childish                2:0.24.0+fixes.20110510.5461754-0ubuntu0mythbuntu1 The childish MythTV Theme
ii  mythtv-theme-graphite                2:0.24.0+fixes.20110510.5461754-0ubuntu0mythbuntu1 The graphite MythTV Theme
ii  mythtv-theme-iulius-osd              1:0.23.0+fixes23872-0ubuntu1                       The iulius-osd MythTV Theme
ii  mythtv-theme-metallurgy              2:0.24.0+fixes.20110510.5461754-0ubuntu0mythbuntu1 The metallurgy MythTV Theme
ii  mythtv-theme-mono-osd                1:0.23.0+fixes23872-0ubuntu1                       The mono-osd MythTV Theme
ii  mythtv-theme-mythbuntu               2:0.24.0+fixes.20110510.5461754-0ubuntu0mythbuntu1 The mythbuntu MythTV Theme
ii  mythtv-theme-projectgrayhem-osd      1:0.23.0+fixes23872-0ubuntu1                       The projectgrayhem-osd MythTV Theme
ii  mythtv-theme-retro-osd               1:0.23.0+fixes23872-0ubuntu1                       The retro-osd MythTV Theme
ii  mythtv-theme-titivillus-osd          1:0.23.0+fixes23872-0ubuntu1                       The titivillus-osd MythTV Theme
ii  mythtv-themes                        2:0.24.0+fixes.20110510.5461754-0ubuntu0mythbuntu1 Themes for MythTV
ii  mythtv-transcode-utils               2:0.24.0+fixes.20110510.5461754-0ubuntu0mythbuntu1 Utilities used for transcoding MythTV tasks
ii  mythtvfs                             0.6.1-1                                            userspace filesystem client for MythTV
ii  mythvideo                            2:0.24.0+fixes.20110206.1a69c92-0ubuntu0mythbuntu1 A generic video player frontend module for MythTV
ii  mythweb                              2:0.24.0+fixes.20110510.5461754-0ubuntu0mythbuntu1 Web interface add-on module for MythTV

---

### Post by ian dobson on 2011-05-10
Hi,

That looks like your problem, you still have the libmyth from 0.22 installed, can you try deinstalling it with apt-get remove libmyth-0.22-0 and maybe reinstall libmyth-0.24-0.

```
ii libmyth-0.22-0 2:0.22.0-fixes24035-0ubuntu6 Common library code for MythTV and add-on modules (runtime)
rc libmyth-0.23-0 2:0.23.1+fixes26231-0ubuntu2 Common library code for MythTV and add-on modules (runtime)
ii libmyth-0.24-0 2:0.24.0+fixes.20110510.5461754-0ubuntu0mythbuntu1 Common library code for MythTV and add-on modules (runtime)
```

Regards
Ian Dobson

---

### Post by Nikas on 2011-05-10
You could ask me. ;)

I had to update my kernel on my FE when my playback broke with the last update..

---

### Post by extasy on 2011-05-11
> **ian dobson said:**
> Hi,

That looks like your problem, you still have the libmyth from 0.22 installed, can you try deinstalling it with apt-get remove libmyth-0.22-0 and maybe reinstall libmyth-0.24-0.

```
ii libmyth-0.22-0 2:0.22.0-fixes24035-0ubuntu6 Common library code for MythTV and add-on modules (runtime)
rc libmyth-0.23-0 2:0.23.1+fixes26231-0ubuntu2 Common library code for MythTV and add-on modules (runtime)
ii libmyth-0.24-0 2:0.24.0+fixes.20110510.5461754-0ubuntu0mythbuntu1 Common library code for MythTV and add-on modules (runtime)
```

Regards
Ian Dobson

Thank you that did solve the problem!

---

### Post by ian dobson on 2011-05-11
> **extasy said:**
> Thank you that did solve the problem!


No Problems, glad that I could help.

It's much easier to fix problems in Linux than in Windows. Just do a google search for DLL hell.

Regards
Ian Dobson

---

### Post by tgm4883 on 2011-05-11
Please mark your thread as solved (I believe it's under Thread Tools)

Also, I'd point out that you are on a no longer supported version (9.10) and somehow got 0.24 installed on there (The Mythbuntu team didn't provide 0.24 builds for 9.10). Please let me know if you were somehow offered 0.24 on 9.10 using mythbuntu-repos (or Mythbuntu control centre), otherwise I would suggest a more accurate title in the future (something along the lines of "I forced an update and broke my system)

---

