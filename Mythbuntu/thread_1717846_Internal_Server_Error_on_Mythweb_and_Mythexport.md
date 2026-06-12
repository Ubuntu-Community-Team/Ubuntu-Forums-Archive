---
title: "Internal Server Error on Mythweb and Mythexport"
date: 2011-03-30
forum: Mythbuntu
---

### Post by rbeer on 2011-03-30
I am getting the following error when I click on certain links within mythweb and whenever I try to access any page of mythexport.

```
Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.

Apache/2.2.14 (Ubuntu) Server at 192.168.0.17 Port 80
```

When I look in the apache logs it's coming up with this error:

```
[Wed Mar 30 19:37:44 2011] [error] [client 192.168.0.101] Database schema 1254 not supported.
[Wed Mar 30 19:37:44 2011] [error] [client 192.168.0.101] Bindings support schema version 1264
[Wed Mar 30 19:37:44 2011] [error] [client 192.168.0.101] Premature end of script headers: file.cgi

```

Can't work out why the mythweb schema would claim a different database when all came from the mythbuntu repos (23.1). Have tried purging and reinstalling mythweb and mythexport.

---

### Post by rhpot1991 on 2011-03-30
Have you run a frontend connected to your backend?  That will update the schema then.

---

### Post by rbeer on 2011-03-31
All frontends connect without issue (hence my confusion as to why mythweb is having problems). When frontend first ran it did ask and updated the schema. Mythweb may have been working properly before this but can't be entirely sure.

---

### Post by rhpot1991 on 2011-03-31
I would try to repair and optimize your tables, hopefully you can access this section of mythweb.  If not then there should be some wiki entries on how to do it command line.

---

### Post by rbeer on 2011-03-31
No luck - same error message

```
rmbeer@mythtv:/usr/share/doc/mythtv-doc/examples/maintenance$ ./optimize_mythdb.pl
Database schema 1254 not supported.
Bindings support schema version 1264

```

---

### Post by rbeer on 2011-04-04
Perhaps if anyone knows how I can revert the database schema from 1264 to 1254?

---

### Post by lingenfr on 2011-05-07
I have the same problem. I can flag commercials, but I can't export via mythexport. You can see I have similar errors.

linghome@MYTHBUNTU-BKEND:/var/log/mythtv$ tail mythexport.log
May  7 15:21:52 MYTHBUNTU-BKEND /usr/bin/mythexport-daemon[1171]: Can't connect to MythTV: Database schema 1254 not supported.
Bindings support schema version 1264
 at line 88 in /usr/bin/mythexport-daemon
May  7 15:21:57 MYTHBUNTU-BKEND /usr/bin/mythexport-daemon[1171]: Can't connect to MythTV: Database schema 1254 not supported.
Bindings support schema version 1264
 at line 88 in /usr/bin/mythexport-daemon
May  7 15:22:02 MYTHBUNTU-BKEND /usr/bin/mythexport-daemon[1171]: Can't connect to MythTV: Database schema 1254 not supported.
Bindings support schema version 1264
 at line 88 in /usr/bin/mythexport-daemon
Couldn't connect to MythTV. at /usr/bin/mythexport-daemon line 94.

I can connect with a frontend. Any other ideas than those show above? It doesn't look like the OP ever solved the problem either.

---

### Post by metol on 2011-07-26
I just had the same issue and the problem for me was that the password in _**/etc/mythtv/config.xml**_ was incorrect.  I put in the correct password and restarted the daemon with:

```
sudo /etc/init.d/mythexport restart
```

After that, it was fine.

---

### Post by &lt;mike&gt; on 2011-08-06
Hmmm... didn't work for me.

The issue seems to be that mythweb is using a newer version of some bindings than mythv. When I go into the database, I can see the version of the database schema is correct:

```
 select value, trim(data) as data from settings where value = 'DBSchemaVer';
+-------------+-------+
| value       | data  |
+-------------+-------+
| DBSchemaVer | 1254  |
+-------------+-------+
1 row in set (0.00 sec)

```

When I run

```
$ dpkg -l *myth*
```

I get

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                 Version                              Description
+++-====================================-====================================-========================================================================================
ii  gtk2-engines-mythbuntu               0.4-0ubuntu2                         Mythbuntu GTK+ 2.x Theme
rc  libmyth-0.21-0                       0.21.0+fixes19961-0ubuntu8           Common library code for MythTV and add-on modules (runtime)
rc  libmyth-0.22-0                       0.22.0+fixes22594-0ubuntu1           Common library code for MythTV and add-on modules (runtime)
ii  libmyth-0.23-0                       0.23.1+fixes26863-0ubuntu0+mythbuntu Common library code for MythTV and add-on modules (runtime)
rc  libmyth-0.24-0                       2:0.24.0+fixes.20101209.ee57332-0ubu Common library code for MythTV and add-on modules (runtime)
un  libmyth-perl                         <none>                               (no description available)
ii  libmyth-python                       2:0.24.0+fixes.20101209.ee57332-0ubu A python library to access some MythTV features
ii  libmythtv-perl                       2:0.24.0+fixes.20101209.ee57332-0ubu A PERL library to access some MythTV features
un  mythappearance                       <none>                               (no description available)
ii  mytharchive                          0.23.1+fixes26863-0ubuntu0+mythbuntu create and burn DVD's from MythTV - binary file
un  mytharchive-data                     <none>                               (no description available)
un  mythbrowser                          <none>                               (no description available)
un  mythbuntu-artwork-usplash            <none>                               (no description available)
ii  mythbuntu-common                     0.50-0ubuntu1                        Mythbuntu application support functions
ii  mythbuntu-control-centre             0.62-0ubuntu1                        Mythbuntu Configuration Application
ii  mythbuntu-default-settings           0.96-0ubuntu1                        default settings for Mythbuntu
ii  mythbuntu-desktop                    0.59                                 The Mythbuntu standalone system
ii  mythbuntu-gdm-theme                  0.6-0ubuntu1                         Mythbuntu GDM theme
ii  mythbuntu-lirc-generator             0.25-0ubuntu1~ppa1                   Mythbuntu Lirc Configuration Generator
un  mythbuntu-live                       <none>                               (no description available)
un  mythbuntu-live-autostart             <none>                               (no description available)
ii  mythbuntu-log-grabber                0.7-0ubuntu2                         Mythbuntu repos installer
ii  mythbuntu-repos                      9.3-0ubuntu0+mythbuntu~auto201107030 Mythbuntu repository installer
un  mythbuntu-testing                    <none>                               (no description available)
un  mythbuntu-weekly                     <none>                               (no description available)
un  mythcontrols                         <none>                               (no description available)
un  mythdvd                              <none>                               (no description available)
rc  mythexport                           2.1.3-0ubuntu1                       Export MythTV recording to portable media players
un  mythflix                             <none>                               (no description available)
ii  mythgallery                          0.23.1+fixes26863-0ubuntu0+mythbuntu Image gallery/slideshow add-on module for MythTV
un  mythgame                             <none>                               (no description available)
ii  mythmovies                           0.23.1+fixes26863-0ubuntu0+mythbuntu Find nearby movies and cinema listings
ii  mythmusic                            0.23.1+fixes26863-0ubuntu0+mythbuntu Music add-on module for MythTV
un  mythnetvision                        <none>                               (no description available)
un  mythnews                             <none>                               (no description available)
un  mythphone                            <none>                               (no description available)
un  mythplugins                          <none>                               (no description available)
un  mythstream                           <none>                               (no description available)
ii  mythtv                               0.23.1+fixes26863-0ubuntu0+mythbuntu A personal video recorder application (client and server)
ii  mythtv-backend                       0.23.1+fixes26863-0ubuntu0+mythbuntu A personal video recorder application (server)
ii  mythtv-backend-master                0.23.1+fixes26863-0ubuntu0+mythbuntu Metapackage to setup and configure a "Master Backend" profile of MythTV.
ii  mythtv-common                        0.23.1+fixes26863-0ubuntu0+mythbuntu A personal video recorder application (common data)
ii  mythtv-database                      0.23.1+fixes26863-0ubuntu0+mythbuntu A personal video recorder application (database)
un  mythtv-doc                           <none>                               (no description available)
ii  mythtv-frontend                      0.23.1+fixes26863-0ubuntu0+mythbuntu A personal video recorder application (client)
ii  mythtv-theme-arclight                1:0.23.1+fixes26863-0ubuntu0+mythbun The arclight MythTV Theme
un  mythtv-theme-blootube                <none>                               (no description available)
ii  mythtv-theme-blootube-osd            1:0.23.1+fixes26863-0ubuntu0+mythbun The blootube-osd MythTV Theme
un  mythtv-theme-blootube-wide           <none>                               (no description available)
un  mythtv-theme-blootubelite-wide       <none>                               (no description available)
ii  mythtv-theme-blueosd                 1:0.23.1+fixes26863-0ubuntu0+mythbun The blueosd MythTV Theme
ii  mythtv-theme-childish                1:0.23.1+fixes26863-0ubuntu0+mythbun The childish MythTV Theme
un  mythtv-theme-glass-wide              <none>                               (no description available)
ii  mythtv-theme-graphite                1:0.23.1+fixes26863-0ubuntu0+mythbun The graphite MythTV Theme
un  mythtv-theme-gray-osd                <none>                               (no description available)
un  mythtv-theme-isthmus                 <none>                               (no description available)
un  mythtv-theme-iulius                  <none>                               (no description available)
ii  mythtv-theme-iulius-osd              1:0.23.1+fixes26863-0ubuntu0+mythbun The iulius-osd MythTV Theme
ii  mythtv-theme-metallurgy              1:0.23.1+fixes26863-0ubuntu0+mythbun The metallurgy MythTV Theme
un  mythtv-theme-metallurgy-osd          <none>                               (no description available)
un  mythtv-theme-metallurgy-wide         <none>                               (no description available)
un  mythtv-theme-minimalist-wide         <none>                               (no description available)
ii  mythtv-theme-mono-osd                1:0.23.1+fixes26863-0ubuntu0+mythbun The mono-osd MythTV Theme
ii  mythtv-theme-mythbuntu               1:0.23.1+fixes26863-0ubuntu0+mythbun The mythbuntu MythTV Theme
un  mythtv-theme-mythcenter              <none>                               (no description available)
un  mythtv-theme-mythcenter-wide         <none>                               (no description available)
un  mythtv-theme-neon-wide               <none>                               (no description available)
un  mythtv-theme-proejctgrayhem-wide     <none>                               (no description available)
un  mythtv-theme-projectgrayhem          <none>                               (no description available)
ii  mythtv-theme-projectgrayhem-osd      1:0.23.1+fixes26863-0ubuntu0+mythbun The projectgrayhem-osd MythTV Theme
un  mythtv-theme-projectgrayhem-wide     <none>                               (no description available)
un  mythtv-theme-retro                   <none>                               (no description available)
ii  mythtv-theme-retro-osd               1:0.23.1+fixes26863-0ubuntu0+mythbun The retro-osd MythTV Theme
un  mythtv-theme-titivillus              <none>                               (no description available)
ii  mythtv-theme-titivillus-osd          1:0.23.1+fixes26863-0ubuntu0+mythbun The titivillus-osd MythTV Theme
ii  mythtv-themes                        1:0.23.1+fixes26863-0ubuntu0+mythbun Themes for MythTV
ii  mythtv-transcode-utils               0.23.1+fixes26863-0ubuntu0+mythbuntu Utilities used for transcoding MythTV tasks
ii  mythvideo                            0.23.1+fixes26863-0ubuntu0+mythbuntu A generic video player frontend module for MythTV
un  mythweather                          <none>                               (no description available)
ii  mythweb                              0.23.1+fixes26863-0ubuntu0+mythbuntu Web interface add-on module for MythTV
un  ubiquity-frontend-mythbuntu          <none>                               (no description available)

```

In which case I'm thinking that maybe I should remove libmyth-0.24-0 (EDIT: if it's installed... not sure what rc means...) and adjust libmyth-python and libmyth-perl, seeing as they don't agree with any of my other versions.

Any thoughts?

---

### Post by &lt;mike&gt; on 2011-08-07
Update: I have fixed my problem; this is how:

As above, I had a version discrepancy between my perl and python bindings and my mythtv. I'm using 0.23.1, and 
```
dpkg -l *myth*
```
lists the version as 0.23.1+fixes26863-0ubuntu0+mythbuntu2:
```
ii  mythtv                                         0.23.1+fixes26863-0ubuntu0+mythbuntu2              A personal video recorder application (clien
ii  mythtv-backend                                 0.23.1+fixes26863-0ubuntu0+mythbuntu2              A personal video recorder application (serve
ii  mythtv-backend-master                          0.23.1+fixes26863-0ubuntu0+mythbuntu2              Metapackage to setup and configure a "Master
ii  mythtv-common                                  0.23.1+fixes26863-0ubuntu0+mythbuntu2              A personal video recorder application (commo
ii  mythtv-database                                0.23.1+fixes26863-0ubuntu0+mythbuntu2              A personal video recorder application (datab
```
but lists my bindings as 2:0.24.0+fixes.20101209.ee57332-0ubuntu0mythbuntu1

So the solution is to downgrade the packages so the versions match:
```
 $ sudo apt-get install libmyth-python=0.23.1+fixes26863-0ubuntu0+mythbuntu2
  $ sudo apt-get install libmythtv-perl=0.23.1+fixes26863-0ubuntu0+mythbuntu2
  $ sudo /etc/init.d/apache2 restart
```

Thus far, mythtv itself seems to be working perfectly. I'll update if I notice any problems.

---

