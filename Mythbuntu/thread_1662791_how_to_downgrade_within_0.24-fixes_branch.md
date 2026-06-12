---
title: "how to downgrade within 0.24-fixes branch?"
date: 2011-01-08
forum: Mythbuntu
---

### Post by ZedThou on 2011-01-08
After an update yesterday, playback of recordings is doing odd things, like jumping around at random within the program. So I was wondering if there is an easy way to go back to the versions of packages that were installed before the update. Thanks for any suggestions!

```

$ dpkg -l | grep mythtv
ii  libmythtv-perl                       2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu2 A PERL library to access some MythTV features
ii  mythtv                               2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu2 A personal video recorder application (client and server)
ii  mythtv-backend                       2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu2 A personal video recorder application (server)
ii  mythtv-backend-master                2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu2 Metapackage to setup and configure a "Master Backend" profile of MythTV.
ii  mythtv-common                        2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu2 A personal video recorder application (common data)
ii  mythtv-database                      2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu2 A personal video recorder application (database)
ii  mythtv-dbg                           2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu2 Debug symbols for mythtv packages
ii  mythtv-frontend                      2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu2 A personal video recorder application (client)
ii  mythtv-theme-arclight                2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu2 The arclight MythTV Theme
ii  mythtv-theme-blootube-osd            1:0.23.1+fixes26863-0ubuntu0+mythbuntu3            The blootube-osd MythTV Theme
ii  mythtv-theme-blueosd                 1:0.23.1+fixes26863-0ubuntu0+mythbuntu3            The blueosd MythTV Theme
ii  mythtv-theme-childish                2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu2 The childish MythTV Theme
ii  mythtv-theme-graphite                2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu2 The graphite MythTV Theme
ii  mythtv-theme-iulius-osd              1:0.23.1+fixes26863-0ubuntu0+mythbuntu3            The iulius-osd MythTV Theme
ii  mythtv-theme-metallurgy              2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu2 The metallurgy MythTV Theme
ii  mythtv-theme-mono-osd                1:0.23.1+fixes26863-0ubuntu0+mythbuntu3            The mono-osd MythTV Theme
ii  mythtv-theme-mythbuntu               2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu2 The mythbuntu MythTV Theme
ii  mythtv-theme-projectgrayhem-osd      1:0.23.1+fixes26863-0ubuntu0+mythbuntu3            The projectgrayhem-osd MythTV Theme
ii  mythtv-theme-retro-osd               1:0.23.1+fixes26863-0ubuntu0+mythbuntu3            The retro-osd MythTV Theme
ii  mythtv-theme-titivillus-osd          1:0.23.1+fixes26863-0ubuntu0+mythbuntu3            The titivillus-osd MythTV Theme
ii  mythtv-themes                        2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu2 Themes for MythTV
ii  mythtv-transcode-utils               2:0.24.0+fixes.20110106.c6c50df-0ubuntu0mythbuntu2 Utilities used for transcoding MythTV tasks

```

---

### Post by ZedThou on 2011-01-08
I noticed some database errors in the backend log, and after running the database repair/optimize options from mythweb, playback of new recordings is working normally again. So I'll mark this one as solved, although it would still be nice to know how to roll back the package versions in case it's ever needed in the future.

---

### Post by superm1 on 2011-01-10
The only way to downgrade is to use the cached packages in /var/cache/apt/archives from previous installs.  They're removed from the PPA  on a fairly regular basis since the PPA has a size limit.

---

