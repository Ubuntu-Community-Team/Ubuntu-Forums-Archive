---
title: "Mythtv database will not upgrade"
date: 2012-02-06
forum: Mythbuntu
---

### Post by 404wanderer on 2012-02-06
Hello all,

I'm having trouble because my mythtv database will not upgrade from 1290. This prevents the frontend from starting.
> 
2012-02-07 13:39:58.012602 I [13800/13800] CoreContext schemawizard.cpp:118 (Compare) - Current MythTV Schema Version (DBSchemaVer): 1290
2012-02-07 13:39:58.012621 C [13800/13800] CoreContext schemawizard.cpp:136 (CompareAndWait) - MythTV database schema is old. Waiting to see if DB is being upgraded.
2012-02-07 13:39:58.611034 I [13800/13814] RAOPDevice bonjourregister.cpp:100 (BonjourCallback) - Bonjour: Service registration complete: name '4d344b352829@MythTV on telly' type '_raop._tcp.' domain: 'local.'
2012-02-07 13:39:59.013083 I [13800/13800] CoreContext mythdbcon.cpp:75 (MSqlDatabase) - Database connection created: DBManager4
2012-02-07 13:39:59.013103 I [13800/13800] CoreContext mythdbcon.cpp:298 (popConnection) - New DB connection, total: 4
2012-02-07 13:39:59.013415 I [13800/13800] CoreContext mythdbcon.cpp:179 (OpenDatabase) - Connected to database 'mythconverg' at host: localhost
2012-02-07 13:39:59.014787 I [13800/13800] CoreContext schemawizard.cpp:118 (Compare) - Current MythTV Schema Version (DBSchemaVer): 1290
2012-02-07 13:40:00.016216 I [13800/13800] CoreContext schemawizard.cpp:118 (Compare) - Current MythTV Schema Version (DBSchemaVer): 1290
2012-02-07 13:40:01.017767 I [13800/13800] CoreContext schemawizard.cpp:118 (Compare) - Current MythTV Schema Version (DBSchemaVer): 1290
2012-02-07 13:40:02.019372 I [13800/13800] CoreContext schemawizard.cpp:118 (Compare) - Current MythTV Schema Version (DBSchemaVer): 1290
2012-02-07 13:40:03.020872 I [13800/13800] CoreContext schemawizard.cpp:118 (Compare) - Current MythTV Schema Version (DBSchemaVer): 1290
2012-02-07 13:40:03.020932 C [13800/13800] CoreContext schemawizard.cpp:180 (CompareAndWait) - Timed out waiting.
2012-02-07 13:40:03.020964 E [13800/13800] CoreContext dbcheck.cpp:470 (UpgradeTVDatabaseSchema) - Not allowed to upgrade the database.
2012-02-07 13:40:03.023945 E [13800/13800] CoreContext main.cpp:1610 (main) - Couldn't upgrade database to new schema, exiting.
2012-02-07 13:40:03.023966 I [13800/13800] CoreContext mythraopdevice.cpp:57 (Cleanup) - RAOP Device: Cleaning up.
2012-02-07 13:40:03.023996 I [13800/13800] CoreContext bonjourregister.cpp:26 (~BonjourRegister) - Bonjour: De-registering service '_raop._tcp.' on '4d344b352829@MythTV on telly'
2012-02-07 13:40:03.024368 I [13800/13800] CoreContext mythairplayserver.cpp:266 (Cleanup) - AirPay: Cleaning up.
2012-02-07 13:40:03.024389 I [13800/13800] CoreContext main.cpp:242 (cleanup) - Deleting UPnP client...
2012-02-07 13:40:03.786419 I [13800/13818] Socket mythdbcon.cpp:479 (CloseDatabases) - Closing DB connection named 'DBManager3'
2012-02-07 13:40:03.786929 I [13800/13803] DBLogger mythdbcon.cpp:479 (CloseDatabases) - Closing DB connection named 'DBManager2'
2012-02-07 13:40:10.367511 I [13800/13800] CoreContext mythdbcon.cpp:479 (CloseDatabases) - Closing DB connection named 'DBManager4'
2012-02-07 13:40:10.367664 I [13800/13800] CoreContext mythdbcon.cpp:479 (CloseDatabases) - Closing DB connection named 'DBManager1'
2012-02-07 13:40:10.370629 E [13800/13800] CoreContext mythrender_opengl.cpp:171 (doneCurrent) - OpenGL: Mis-matched calls to makeCurrent()


Running backend setup prompts me to upgrade the database but it never suceeds.

> ii  gtk2-engines-mythbuntu                     0.4-0ubuntu2                                         Mythbuntu GTK+ 2.x Theme
rc  libgmyth0                                  1:0.7.1-1.1                                          GObject based library for accessing MythTV backend (runtime files)
rc  libmyth-0.21-0                             0.21.0+fixes19961-0ubuntu8                           Common library code for MythTV and add-on modules (runtime)
rc  libmyth-0.22-0                             0.22.0+fixes22594-0ubuntu1                           Common library code for MythTV and add-on modules (runtime)
rc  libmyth-0.23-0                             0.23.1+fixes26863-0ubuntu0+mythbuntu2                Common library code for MythTV and add-on modules (runtime)
ii  libmyth-0.24-0                             2:0.25.0~master.20120206.6ca0ea5-0ubuntu0mythbuntu3  Common library code for MythTV and add-on modules (runtime)
ii  libmyth-python                             2:0.25.0~master.20120206.6ca0ea5-0ubuntu0mythbuntu3  A python library to access some MythTV features
ii  libmythtv-perl                             2:0.25.0~master.20120206.6ca0ea5-0ubuntu0mythbuntu3  A PERL library to access some MythTV features
ii  mytharchive                                2:0.25.0~master.20120206.6ca0ea5-0ubuntu0mythbuntu3  create and burn DVD's from MythTV - binary file
ii  mythbrowser                                2:0.25.0~master.20120206.6ca0ea5-0ubuntu0mythbuntu3  A web browser for MythTV
ii  mythbuntu-bare-client                      2.0                                                  Mythbuntu Bare Client
ii  mythbuntu-common                           0.63                                                 Mythbuntu application support functions
ii  mythbuntu-control-centre                   0.63-0ubuntu2                                        Mythbuntu Configuration Application
ii  mythbuntu-default-settings                 1.02                                                 default settings for Mythbuntu
ii  mythbuntu-desktop                          0.72                                                 The Mythbuntu standalone system
ii  mythbuntu-lightdm-theme                    0.9                                                  Mythbuntu LightDM setup
ii  mythbuntu-lirc-generator                   0.26-0ubuntu1                                        Mythbuntu Lirc Configuration Generator
ii  mythbuntu-log-grabber                      0.9-0ubuntu2                                         Mythbuntu diagnostic utility
ii  mythbuntu-repos                            9.3-0ubuntu0+mythbuntu~auto20110703002132            Mythbuntu repository installer
ii  mythgallery                                2:0.25.0~master.20120206.6ca0ea5-0ubuntu0mythbuntu3  Image gallery/slideshow add-on module for MythTV
ii  mythgame                                   2:0.25.0~master.20120206.6ca0ea5-0ubuntu0mythbuntu3  Emulator & PC Game frontend module for MythTV
ii  mythmusic                                  2:0.25.0~master.20120206.6ca0ea5-0ubuntu0mythbuntu3  Music add-on module for MythTV
ii  mythnetvision                              2:0.25.0~master.20120206.6ca0ea5-0ubuntu0mythbuntu3  A Internet Video Player plugin for MythTV
ii  mythnews                                   2:0.25.0~master.20120206.6ca0ea5-0ubuntu0mythbuntu3  An RSS feed news reader module for MythTV
ii  mythtv                                     2:0.25.0~master.20120206.6ca0ea5-0ubuntu0mythbuntu3  A personal video recorder application (client and server)
ii  mythtv-backend                             2:0.25.0~master.20120206.6ca0ea5-0ubuntu0mythbuntu3  A personal video recorder application (server)
ii  mythtv-backend-master                      2:0.25.0~master.20120206.6ca0ea5-0ubuntu0mythbuntu3  Metapackage to setup and configure a "Master Backend" profile of MythTV.
ii  mythtv-common                              2:0.25.0~master.20120206.6ca0ea5-0ubuntu0mythbuntu3  A personal video recorder application (common data)
ii  mythtv-database                            2:0.25.0~master.20120206.6ca0ea5-0ubuntu0mythbuntu3  A personal video recorder application (database)
ii  mythtv-frontend                            2:0.25.0~master.20120206.6ca0ea5-0ubuntu0mythbuntu3  A personal video recorder application (client)
ii  mythtv-status                              0.9.3-1                                              Show the status of a MythTV backend
ii  mythtv-theme-childish                      2:0.25.0~master.20120206.6ca0ea5-0ubuntu0mythbuntu3  The childish MythTV Theme
ii  mythtv-theme-graphite                      2:0.24.1+fixes.20111019.274470c-0ubuntu0mythbuntu4   The graphite MythTV Theme
ii  mythtv-theme-metallurgy                    2:0.25.0~master.20120129.67fa131-0ubuntu0mythbuntu3  The metallurgy MythTV Theme
ii  mythtv-theme-mythbuntu                     2:0.25.0~master.20120206.6ca0ea5-0ubuntu0mythbuntu3  The mythbuntu MythTV Theme
ii  mythtv-transcode-utils                     2:0.25.0~master.20120206.6ca0ea5-0ubuntu0mythbuntu3  Utilities used for transcoding MythTV tasks
rc  mythvideo                                  2:0.25.0~master.20110608.5241f65-0ubuntu0mythbuntu2  A generic video player frontend module for MythTV
ii  mythweather                                2:0.25.0~master.20120206.6ca0ea5-0ubuntu0mythbuntu3  Weather add-on module for MythTV
ii  mythweb                                    2:0.25.0~master.20120206.6ca0ea5-0ubuntu0mythbuntu3  Web interface add-on module for MythTV
ii  php-mythtv                                 2:0.25.0~master.20120206.6ca0ea5-0ubuntu0mythbuntu3  PHP Bindings for MythTV




Any help would be really appreciated as I'm at a loss.

---

### Post by nickrout on 2012-02-07
> **404wanderer said:**
> Hello all,

I'm having trouble because my mythtv database will not upgrade from 1290. This prevents the frontend from starting.


Running backend setup prompts me to upgrade the database but it never suceeds.





Any help would be really appreciated as I'm at a loss.

you are using unreleased beta (at best) code. post to the -dev mailing list.

---

