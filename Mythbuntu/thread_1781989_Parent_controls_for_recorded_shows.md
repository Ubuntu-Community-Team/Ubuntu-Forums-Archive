---
title: "Parent controls for recorded shows ?"
date: 2011-06-14
forum: Mythbuntu
---

### Post by declanmullen on 2011-06-14
I have young kids and some of the TV shows I record are not appropriate for them, so I would like to be able to restrict their ability to watch those recordings.

I've read about Recording Groups and the Mythtv doco suggests to me that I should be able to achieve the above restrictions by creating a Recording Group, giving it a password and then storing the recordings that I don't want my kids to be able to view within it.

However it's not working out as I anticipated :

To set a password on a single Recording Group; in the Mythtv Frontend I entered the "Watch Recordings" screen, selected the specific Recording Group I want the password on (ie one I created earlier eg "Adult", definately not "All Programmes"), I hit 'M' and then used the "Change Group Password" menu item to set the password. However now when I attempt to re-enter Watch Recordings, I first get prompted for the "Password for group 'All Programs':". 

It seems to me that the password has been set on the "All Programmes" group rather than the one I selected, or maybe the password has been set for the entire "Watch Recordings" screen ?  Either way it isn't what I want, ie what I want is to stop my kids watching any of the recordings in my "Adult" Recording Group by password protecting them.  

Is it a bug or am I doing some thing wrong or do I need to use a completely different technique ?
 
I'm using Mythbuntu 10.10 x86 32bit and have upgraded to its Mythtv 0.24 repository, which I believe also includes the 0.24.1 updates: 
```
deb http://ppa.launchpad.net/mythbuntu/0.24/ubuntu maverick main

```
```
# dpkg -l | grep -i myth
rc  libmyth-0.23-0                       0.23.1+fixes26437-0ubuntu1                         Common library code for MythTV and add-on modules (runtime)
ii  libmyth-0.24-0                       2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 Common library code for MythTV and add-on modules (runtime)
ii  libmyth-python                       2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 A python library to access some MythTV features
ii  libmythtv-perl                       2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 A PERL library to access some MythTV features
ii  mytharchive                          2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 create and burn DVD's from MythTV - binary file
ii  mythbrowser                          2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 A web browser for MythTV
ii  mythbuntu-common                     0.54-0ubuntu2                                      Mythbuntu application support functions
ii  mythbuntu-control-centre             0.62-0ubuntu1                                      Mythbuntu Configuration Application
ii  mythbuntu-default-settings           0.97-0ubuntu1                                      default settings for Mythbuntu
ii  mythbuntu-desktop                    0.62                                               The Mythbuntu standalone system
ii  mythbuntu-gdm-theme                  0.6-0ubuntu1                                       Mythbuntu GDM theme
ii  mythbuntu-lirc-generator             0.25-0ubuntu1                                      Mythbuntu Lirc Configuration Generator
ii  mythbuntu-log-grabber                0.8-0ubuntu1                                       Mythbuntu diagnostic utility
ii  mythbuntu-repos                      9.2-0ubuntu0+mythbuntu~auto20110516001222          Mythbuntu repository installer
ii  mythgallery                          2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 Image gallery/slideshow add-on module for MythTV
ii  mythgame                             2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 Emulator & PC Game frontend module for MythTV
ii  mythmusic                            2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 Music add-on module for MythTV
ii  mythnetvision                        2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 A Internet Video Player plugin for MythTV
ii  mythnews                             2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 An RSS feed news reader module for MythTV
ii  mythtv                               2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 A personal video recorder application (client and server)
ii  mythtv-backend                       2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 A personal video recorder application (server)
ii  mythtv-backend-master                2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 Metapackage to setup and configure a "Master Backend" profile of MythTV.
ii  mythtv-common                        2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 A personal video recorder application (common data)
ii  mythtv-database                      2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 A personal video recorder application (database)
ii  mythtv-frontend                      2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 A personal video recorder application (client)
ii  mythtv-theme-arclight                2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 The arclight MythTV Theme
ii  mythtv-theme-blootube-osd            1:0.23.0+fixes23872-0ubuntu1                       The blootube-osd MythTV Theme
ii  mythtv-theme-blueosd                 1:0.23.0+fixes23872-0ubuntu1                       The blueosd MythTV Theme
ii  mythtv-theme-childish                2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 The childish MythTV Theme
ii  mythtv-theme-graphite                2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 The graphite MythTV Theme
ii  mythtv-theme-iulius-osd              1:0.23.0+fixes23872-0ubuntu1                       The iulius-osd MythTV Theme
ii  mythtv-theme-metallurgy              2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 The metallurgy MythTV Theme
ii  mythtv-theme-mono-osd                1:0.23.0+fixes23872-0ubuntu1                       The mono-osd MythTV Theme
ii  mythtv-theme-mythbuntu               2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 The mythbuntu MythTV Theme
ii  mythtv-theme-projectgrayhem-osd      1:0.23.0+fixes23872-0ubuntu1                       The projectgrayhem-osd MythTV Theme
ii  mythtv-theme-retro-osd               1:0.23.0+fixes23872-0ubuntu1                       The retro-osd MythTV Theme
ii  mythtv-theme-titivillus-osd          1:0.23.0+fixes23872-0ubuntu1                       The titivillus-osd MythTV Theme
ii  mythtv-themes                        2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 Themes for MythTV
ii  mythtv-transcode-utils               2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 Utilities used for transcoding MythTV tasks
ii  mythvideo                            2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 A generic video player frontend module for MythTV
ii  mythweather                          2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 Weather add-on module for MythTV
ii  mythweb                              2:0.24.1+fixes.20110612.40a3124-0ubuntu0mythbuntu2 Web interface add-on module for MythTV
```

---

### Post by larsolav on 2011-06-14
I have not played with these settings before, but it would make sense that "all programs" would be password protected, so that the kids would not have access to all the programs. How about adding a group called "Kids" and not have that password protected? That way all programs (including your adult shows)are password protected, but what you let the kids watch is not? Would that work?

---

### Post by declanmullen on 2011-06-15
Thanks for the suggestion, however I do have Kids defined and it doesn't have a password assigned. But when I'm prompted for the password for All Programs (on entry to the Watch Recordings screen), if I don't supply the expected password, then the Watch Recordings screen is empty of all recordings and all groups. It does'nt even have the All Programmes group.`

---

### Post by declanmullen on 2011-07-16
Issue resolved. The problem was that I didn't understand the Recording Group password functionality and what it is suppose to do. I had thought that the password was associated directly with a Recording Group as seen on the left hand side of the "Watch Recordings" screen. However it isn't. The password is associate with a "Recording Group Filter". Once I understood that, it became obvious that the feature was working as intended. With this correct understanding I've since been able to configure it to achieve what I want.

Correct usage: 
From the "Watch Recordings" screen access the menu and activate the desired Recording Group Filter. Then access the menu again to activate the password for the currently active Filter. Whenever that filter is activated, you will now be prompted to provide its password.

You can within the Frontend's setup, specify which Recording Group Filter should be initially activated when you first enter the "Watch Recordings" screen. 

To achieve what I want, I now have two recording groups; Default and Adult. I've put a password on recording group filters "All Programmes" and "Adult". There is no password on the Default recording group filter. I've configured the frontend to use the "Default" recording group filter on first entry to the Watch Recordings screen. For the recordings that I don't want my kids to be able to view, I ensure the recordings have their Storage Recording Group option set to the Adult recording group. For the recordings that I am happy for my kids to view, I ensure those recordings have their Storage recording group option set to the Default recording group.

---

