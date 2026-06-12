---
title: "Core dumps after upgrade to Ubuntu 8.04 and MythTv 0.21"
date: 2008-06-15
forum: Mythbuntu
---

### Post by eclisse on 2008-06-15
Hello all (especially superm1 who kindly helped me in the past).

I had to upgrade to 8.04 and in the process my MythTV got upgraded to 0.21

But now when I launch either mythbackend or mythtv-setup I get a core dump.

I thought it may be the outdated DB so I deleted it (after backing it up) and let mythtv-setup recreate it.
But nothing. I still get core dump.

Here is an output from
mythtv-setup.real -v all
```

2008-06-15 10:18:06.207 Using runtime prefix = /usr, libdir = /usr/lib
2008-06-15 10:18:06.349 XScreenSaver support enabled
2008-06-15 10:18:06.351 DPMS is active.
2008-06-15 10:18:06.354 Empty LocalHostName.
2008-06-15 10:18:06.354 Using localhost value of trash
2008-06-15 10:18:06.361 MCP::DefaultUPnP() - No default UPnP backend
2008-06-15 10:18:06.447 New DB connection, total: 1
2008-06-15 10:18:06.488 Connected to database 'mythconverg' at host: localhost
2008-06-15 10:18:06.493 Closing DB connection named 'DBManager0'
2008-06-15 10:18:06.495 Clearing Settings Cache.
2008-06-15 10:18:06.501 Primary screen 0.
2008-06-15 10:18:06.503 Connected to database 'mythconverg' at host: localhost
2008-06-15 10:18:06.509 MSqlQuery: SELECT data FROM settings WHERE value = 'RunFrontendInWindow' AND hostname = 'trash' ;
2008-06-15 10:18:06.511 MSqlQuery: SELECT data FROM settings WHERE value = 'RunFrontendInWindow' AND hostname IS NULL;
2008-06-15 10:18:06.512 Using screen 0, 720x576 at 0,0
2008-06-15 10:18:06.515 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetX' AND hostname = 'trash' ;
2008-06-15 10:18:06.517 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetX' AND hostname IS NULL;
2008-06-15 10:18:06.524 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetY' AND hostname = 'trash' ;
2008-06-15 10:18:06.526 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetY' AND hostname IS NULL;
2008-06-15 10:18:06.528 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiResolution' AND hostname = 'trash' ;
2008-06-15 10:18:06.529 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiResolution' AND hostname IS NULL;
2008-06-15 10:18:06.532 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiWidth' AND hostname = 'trash' ;
2008-06-15 10:18:06.533 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiWidth' AND hostname IS NULL;
2008-06-15 10:18:06.535 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiHeight' AND hostname = 'trash' ;
2008-06-15 10:18:06.536 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiHeight' AND hostname IS NULL;
2008-06-15 10:18:06.572 Enabling Settings Cache.
2008-06-15 10:18:06.573 Clearing Settings Cache.
2008-06-15 10:18:06.574 MSqlQuery: CREATE TABLE IF NOT EXISTS schemalock ( schemalock int(1));
2008-06-15 10:18:06.576 MSqlQuery: LOCK TABLE schemalock WRITE;
2008-06-15 10:18:06.580 New DB connection, total: 2
2008-06-15 10:18:06.583 Connected to database 'mythconverg' at host: localhost
2008-06-15 10:18:06.586 MSqlQuery: SELECT data FROM settings WHERE value = 'DBSchemaVer' AND hostname = 'trash' ;
2008-06-15 10:18:06.587 MSqlQuery: SELECT data FROM settings WHERE value = 'DBSchemaVer' AND hostname IS NULL;
2008-06-15 10:18:06.590 MSqlQuery: UNLOCK TABLES;
2008-06-15 10:18:06.590 Current Schema Version: 1214
2008-06-15 10:18:06.593 MSqlQuery: SELECT data FROM settings WHERE value = 'MythFillFixProgramIDsHasRunOnce' AND hostname = 'trash' ;
2008-06-15 10:18:06.594 MSqlQuery: SELECT data FROM settings WHERE value = 'DBMSVersionOverride' AND hostname = 'trash' ;
2008-06-15 10:18:06.596 MSqlQuery: SELECT data FROM settings WHERE value = 'DBMSVersionOverride' AND hostname IS NULL;
2008-06-15 10:18:06.597 MSqlQuery: SELECT VERSION();
2008-06-15 10:18:06.600 Clearing Settings Cache.
2008-06-15 10:18:06.602 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeResolution' AND hostname = 'trash' ;
2008-06-15 10:18:06.603 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeResolution' AND hostname IS NULL;
2008-06-15 10:18:06.606 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeWidth' AND hostname = 'trash' ;
2008-06-15 10:18:06.607 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeWidth' AND hostname IS NULL;
2008-06-15 10:18:06.610 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeHeight' AND hostname = 'trash' ;
2008-06-15 10:18:06.612 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiVidModeHeight' AND hostname IS NULL;
2008-06-15 10:18:06.618 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeResolution' AND hostname = 'trash' ;
2008-06-15 10:18:06.621 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeResolution' AND hostname IS NULL;
2008-06-15 10:18:06.623 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeWidth' AND hostname = 'trash' ;
2008-06-15 10:18:06.625 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeWidth' AND hostname IS NULL;
2008-06-15 10:18:06.627 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeHeight' AND hostname = 'trash' ;
2008-06-15 10:18:06.628 MSqlQuery: SELECT data FROM settings WHERE value = 'DisplaySizeHeight' AND hostname IS NULL;

```
After this it just coredumps.

My system runs on a Via Mini-ITX with Eden 600MHz CPU (I think it qualifies as a 586). Here is my mythtv package versions as suggested in the FAQ:
```

apt-cache policy mythtv-common
mythtv-common:
  Installato: 0.21.0+fixes16838-0ubuntu3.1
  Candidato: 0.21.0+fixes16838-0ubuntu3.1
  Tabella versione:
 *** 0.21.0+fixes16838-0ubuntu3.1 0
        500 http://archive.ubuntu.com hardy-proposed/multiverse Packages
        100 /var/lib/dpkg/status
     0.21.0+fixes16838-0ubuntu3 0
        500 http://archive.ubuntu.com hardy/multiverse Packages


```

Here is the list of installed packages
```

rc  libmyth-0.20                               0.20.2-0ubuntu10.1                          Common library code for MythTV and add-on mo
ii  libmyth-0.21-0                             0.21.0+fixes16838-0ubuntu3.1                Common library code for MythTV and add-on mo
ii  libmyth-perl                               0.21.0+fixes16838-0ubuntu3.1                A PERL library to access some MythTV feature
ii  libmyth-python                             0.21.0+fixes16838-0ubuntu3.1                A python library to access some MythTV featu
ii  mytharchive                                0.21.0+fixes16838-0ubuntu2.1                create and burn DVD's from MythTV - binary f
ii  mytharchive-data                           0.21.0+fixes16838-0ubuntu2.1                create and burn DVD's from MythTV - data fil
ii  mythbrowser                                0.21.0+fixes16838-0ubuntu2.1                A small web browser module for MythTV
ii  mythcontrols                               0.21.0+fixes16838-0ubuntu2.1                External controls for MythTV
ii  mythflix                                   0.21.0+fixes16838-0ubuntu2.1                netflix module for MythTV
ii  mythgallery                                0.21.0+fixes16838-0ubuntu2.1                Image gallery/slideshow add-on module for My
ii  mythgame                                   0.21.0+fixes16838-0ubuntu2.1                Emulator & PC Game frontend module for MythT
ii  mythmovies                                 0.21.0+fixes16838-0ubuntu2.1                Find nearby movies and cinema listings
ii  mythmusic                                  0.21.0+fixes16838-0ubuntu2.1                Music add-on module for MythTV
ii  mythnews                                   0.21.0+fixes16838-0ubuntu2.1                An RSS feed news reader module for MythTV
ii  mythphone                                  0.21.0+fixes16838-0ubuntu2.1                a phone and videophone module for MythTV
ii  mythplugins                                0.21.0+fixes16838-0ubuntu2.1                Wrapper package for MythTV plugins
ii  mythtv                                     0.21.0+fixes16838-0ubuntu3.1                A personal video recorder application (clien
ii  mythtv-backend                             0.21.0+fixes16838-0ubuntu3.1                A personal video recorder application (serve
ii  mythtv-common                              0.21.0+fixes16838-0ubuntu3.1                A personal video recorder application (commo
ii  mythtv-database                            0.21.0+fixes16838-0ubuntu3.1                A personal video recorder application (datab
ii  mythtv-doc                                 0.21.0+fixes16838-0ubuntu3.1                A personal video recorder application (docum
ii  mythtv-frontend                            0.21.0+fixes16838-0ubuntu3.1                A personal video recorder application (clien
ii  mythtv-theme-blootube                      1:0.21.0-0ubuntu1                           The Blootube MythTV theme
ii  mythtv-theme-blootube-osd                  1:0.21.0-0ubuntu2                           The Blootube MythTV OSD
ii  mythtv-theme-blootube-wide                 1:0.21.0-0ubuntu1                           The Blootube MythTV theme (widescreen)
ii  mythtv-theme-blootubelite-wide             1:0.21.0-0ubuntu1                           The Blootube Lite MythTV theme (widescreen)
ii  mythtv-theme-glass-wide                    0.20071107-0ubuntu1                         The Glass MythTV theme (widescreen)
ii  mythtv-theme-gray-osd                      0.21.0-0ubuntu2                             The Gray-OSD MythTV Theme
ii  mythtv-theme-isthmus                       0.21.0-0ubuntu2                             The Isthmus MythTV Theme
ii  mythtv-theme-iulius                        0.21.0-0ubuntu2                             The Iulius MythTV Theme
ii  mythtv-theme-iulius-osd                    0.21.0-0ubuntu2                             The Iulius-OSD MythTV Theme
ii  mythtv-theme-minimalist-wide               0.21.0-0ubuntu2                             The Minimalist Wide MythTV Theme
ii  mythtv-theme-mythbuntu                     0.20080421                                  default MythTV theme used in Mythbuntu
ii  mythtv-theme-mythcenter                    0.21.0-0ubuntu2                             The MythCenter MythTV Theme
ii  mythtv-theme-mythcenter-wide               0.21.0-0ubuntu2                             The MythCenter Wide MythTV Theme
ii  mythtv-theme-neon-wide                     1:0.21.0-0ubuntu1                           The Neon MythTV theme (widescreen)
ii  mythtv-theme-projectgrayhem                1:0.21.0-0ubuntu1                           The Project Grayhem MythTV theme
ii  mythtv-theme-projectgrayhem-osd            1:0.21.0-0ubuntu2                           The Project Grayhem MythTV OSD
ii  mythtv-theme-projectgrayhem-wide           1:0.21.0-0ubuntu1                           The Project Grayhem MythTV theme (widescreen
ii  mythtv-theme-retro                         0.21.0-0ubuntu2                             The Retro MythTV Theme
ii  mythtv-theme-retro-osd                     0.21.0-0ubuntu2                             The Retro-OSD MythTV Theme
ii  mythtv-theme-titivillus                    0.21.0-0ubuntu2                             The Titivillus MythTV Theme
ii  mythtv-theme-titivillus-osd                0.21.0-0ubuntu2                             The Titivillus-OSD MythTV Theme
ii  mythtv-themes                              0.21.0-0ubuntu2                             Additional themes metapackage for MythTV
ii  mythtv-transcode-utils                     0.21.0+fixes16838-0ubuntu3.1                Utilities used for transcoding MythTV tasks
ii  mythvideo                                  0.21.0+fixes16838-0ubuntu2.1                A generic video player frontend module for M
ii  mythweather                                0.21.0+fixes16838-0ubuntu2.1                Weather add-on module for MythTV
ii  mythweb                                    0.21.0+fixes16838-0ubuntu2.1                Web interface add-on module for MythTV

```


Any idea on how to at least debug this problem ?

Thank you in advance !

Paolo

---

### Post by eclisse on 2008-06-16
I've tried recompiling the package from the ubuntu repositories and I still get the same (domething like, the error is in Italian) "forbidded instruction" just after the reads from the database.

Please, could anyone give me some clue as to where to look for a solution ?

Thank you very much.

Best regards,
     Paolo

---

### Post by eclisse on 2008-06-17
Update: I've installed compiling the tarball from the website and it works...

Don't know what causes the error from the version on ubuntu...

---

### Post by GhettoYhetti on 2008-06-28
eclisse . . . 

What TV Card are you using?

---

### Post by eclisse on 2008-06-29
Hauppauge Nova-T USB stick (DVB-T)

---

### Post by superm1 on 2008-06-29
The version in 8.04 requires i686 CPUs.  You can recompile the packages for i586 (apt-get source mythtv).

Alternatively I heard someone put a PPA together with them already recompiled that you can probably use.

---

