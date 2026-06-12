---
title: "Error: MythTV database has a newer TV schema (1264) than expected (1254)"
date: 2010-12-02
forum: Mythbuntu
---

### Post by GooKing on 2010-12-02
Excuse the cross-posting if any of you visit mythtvtalk, but it seems busier here...

I've upgraded to MythTv 0.24 (from 0.23) on Ubuntu 10.10, but I am getting an error saying the database schema is a version newer than expected.

The full error message appears when trying to run MythTV backend setuo, and is:

"Error: MythTV database has a newer TV schema (1264) than expected (1254)"

This is all on a local machine that runs both back and frontend. 

I'm very new to ubuntu and mythtv, so what I cant figure out is how to get the update. So far I have:

Installed mythbuntu control center
Checked control center is set to repository 0.24 PPA repository
Run all updates in both ubuntu update manager and synaptic package manager
Rebooted
Downloaded and run the .deb update file listed in another thread and run updates
Rebooted again

However, running mythbackend --version still shows that i'm running 0.23, although Synaptic shows version 0.24

Is there something I have missed?


As an experiment, I dropped the database, re-installed backend to recreate it.

When entering control panel, it automatically requested I update the database to the 0.24 schema, which I allowed, and then I had the same situation - backend says the database schema is newer than expected.

So, part of the system thinks it is on 0.24, but at least some is still set to 0.23, even after a reinstall and scan for updates.

Any suggestions? If not, I might just drop the db again, and prevent it updating.

---

### Post by tgm4883 on 2010-12-02
> **GooKing said:**
> Excuse the cross-posting if any of you visit mythtvtalk, but it seems busier here...

I've upgraded to MythTv 0.24 (from 0.23) on Ubuntu 10.10, but I am getting an error saying the database schema is a version newer than expected.

The full error message appears when trying to run MythTV backend setuo, and is:

"Error: MythTV database has a newer TV schema (1264) than expected (1254)"

This is all on a local machine that runs both back and frontend. 

I'm very new to ubuntu and mythtv, so what I cant figure out is how to get the update. So far I have:

Installed mythbuntu control center
Checked control center is set to repository 0.24 PPA repository
Run all updates in both ubuntu update manager and synaptic package manager
Rebooted
**Downloaded and run the .deb update file listed in another thread and run updates**
Rebooted again

However, running mythbackend --version still shows that i'm running 0.23, although Synaptic shows version 0.24

Is there something I have missed?


As an experiment, I dropped the database, re-installed backend to recreate it.

When entering control panel, it automatically requested I update the database to the 0.24 schema, which I allowed, and then I had the same situation - backend says the database schema is newer than expected.

So, part of the system thinks it is on 0.24, but at least some is still set to 0.23, even after a reinstall and scan for updates.

Any suggestions? If not, I might just drop the db again, and prevent it updating.

What is this magic you speak of?

:EDIT:

For clarification, you said you downloaded a deb to update, but don't say what that is. It's kinda hard to help if you don't tell us what you did.

On a similar note, what is the output of

```
dpkg -l myth*
```

---

### Post by jyavenard on 2010-12-02
> **GooKing said:**
> Excuse the cross-posting if any of you visit mythtvtalk, but it seems busier here...

I've upgraded to MythTv 0.24 (from 0.23) on Ubuntu 10.10, but I am getting an error saying the database schema is a version newer than expected.

The full error message appears when trying to run MythTV backend setuo, and is:

"Error: MythTV database has a newer TV schema (1264) than expected (1254)"
.

you have to run mythtv-setup or restart the backend before starting the frontend (which is what displays such message)

---

### Post by GooKing on 2010-12-03
hi tgm!

I am beginning to encounter the the magic of ubuntu: speaking arcane words (well, typing them) in a language not known to mortal man, with the hope of gaining power, but the effect of breaking stuff...

Repository file was from [http://www.mythbuntu.org/files/mythbuntu-repos.deb](http://www.mythbuntu.org/files/mythbuntu-repos.deb)

but i think the mythbuntu repository overwrote it.

dpkg -l myth* gives "No packages found matching mythtv-0-24."

The system has been restarted numerous times, so hopefully restarts are not the issue  I have tried to find out how to restart services in ubuntu - there does not seem to be a GUI method, and the multiple different command line versions give different error messages, such as 'service not found'.

Jonathan

---

### Post by tgm4883 on 2010-12-03
> **GooKing said:**
> hi tgm!

I am beginning to encounter the the magic of ubuntu: speaking arcane words (well, typing them) in a language not known to mortal man, with the hope of gaining power, but the effect of breaking stuff...

Repository file was from [http://www.mythbuntu.org/files/mythbuntu-repos.deb](http://www.mythbuntu.org/files/mythbuntu-repos.deb)

but i think the mythbuntu repository overwrote it.

dpkg -l myth* gives "No packages found matching mythtv-0-24."

The system has been restarted numerous times, so hopefully restarts are not the issue  I have tried to find out how to restart services in ubuntu - there does not seem to be a GUI method, and the multiple different command line versions give different error messages, such as 'service not found'.

Jonathan

You have a file or folder in that directory called mythtv-0-24. Get into another directory and run the command.

---

### Post by GooKing on 2010-12-03
Ahhh...folder name. Here's the output

>  ii  mythbrowser    1:0.24.0+fixes A web browser for MythTV
ii  mythbuntu-comm 0.54-0ubuntu1  Mythbuntu application support functions
ii  mythbuntu-cont 0.62-0ubuntu1  Mythbuntu Configuration Application
ii  mythbuntu-lirc 0.25-0ubuntu1  Mythbuntu Lirc Configuration Generator
ii  mythbuntu-repo 8.8-0ubuntu0+m Mythbuntu repository installer
un  mythbuntu-test <none>         (no description available)
un  mythbuntu-week <none>         (no description available)
un  mythcontrols   <none>         (no description available)
un  mythdvd        <none>         (no description available)
un  mythflix       <none>         (no description available)
ii  mythgallery    1:0.24.0+fixes Image gallery/slideshow add-on module for My
ii  mythgame       1:0.24.0+fixes Emulator & PC Game frontend module for MythT
un  mythmovies     <none>         (no description available)
ii  mythmusic      1:0.24.0+fixes Music add-on module for MythTV
ii  mythnetvision  1:0.24.0+fixes A Internet Video Player plugin for MythTV
ii  mythnews       1:0.24.0+fixes An RSS feed news reader module for MythTV
ii  mythplugins    1:0.24.0+fixes Metapackage package for MythTV plugins
un  mythstream     <none>         (no description available)
ii  mythtv         1:0.24.0+fixes A personal video recorder application (clien
ii  mythtv-backend 1:0.24.0+fixes A personal video recorder application (serve
ii  mythtv-backend 1:0.24.0+fixes Metapackage to setup and configure a "Master
ii  mythtv-common  1:0.24.0+fixes A personal video recorder application (commo
ii  mythtv-databas 1:0.24.0+fixes A personal video recorder application (datab
ii  mythtv-doc     1:0.24.0+fixes A personal video recorder application (docum
ii  mythtv-fronten 1:0.24.0+fixes A personal video recorder application (clien
ii  mythtv-theme-a 1:0.24.0+fixes The arclight MythTV Theme

---

### Post by tgm4883 on 2010-12-03
> **GooKing said:**
> Ahhh...folder name. Here's the output

Did you go into mythtv-setup and upgrade the db?

---

### Post by GooKing on 2010-12-04
Yes, tried to run mythtv-setup. Its at that point the GUI shows the error. 
"Error: MythTV database has a newer TV schema (1264) than expected (1254)"



I did save the output from the program this time, and did get some errors:
> 
2010-12-04 09:49:28.626 XMLParseBase, Error: Unable to load window 'backgroundwindow' from base
2010-12-04 09:49:28.627 Removing stale cache dir: /home/jonathan/.mythtv/themecache/Terra.1280.1024
2010-12-04 09:49:28.709 New DB connection, total: 2
2010-12-04 09:49:28.710 Connected to database 'mythconverg' at host: localhost
2010-12-04 09:49:28.712 Current MythTV Schema Version (DBSchemaVer): 1264
2010-12-04 09:49:28.767 New DB connection, total: 3
2010-12-04 09:49:28.769 Connected to database 'mythconverg' at host: localhost
2010-12-04 09:49:37.155 Couldn't upgrade database to new schema.
Error in my_thread_global_end(): 1 threads didn't exit

---

### Post by tgm4883 on 2010-12-04
Moving to it's own thread for more exposure.

---

### Post by jms-ubuntu-en on 2010-12-05
> **GooKing said:**
> Yes, tried to run mythtv-setup. Its at that point the GUI shows the error. 
"Error: MythTV database has a newer TV schema (1264) than expected (1254)"

I did save the output from the program this time, and did get some errors:

So it seems that every piece related is not in sync for some reason, "dpkg -l" shows right versions (without fixes's old svn changeset number though) and DBSchemaVer is as it should be in 0.24.0+fixes. What is the output of "mythbackend --version"?

---

### Post by GooKing on 2010-12-05
/mythbackend still thinks it's 0.23.

> MythTV Version   : 26945
MythTV Branch    : branches/release-0-23-fixes
Network Protocol : 23056
Library API      : 0.23.1.201000710-1
QT Version       : 4.7.0
Options compiled in:
 linux release using_oss using_alsa using_pulse using_jack using_pulseoutput using_backend using_dvb using_firewire using_frontend using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmc_vld using_xvmcw using_bindings_perl using_bindings_python using_opengl using_vdpau using_ffmpeg_threads using_libavc_5_3 using_live using_mheg

---

### Post by jms-ubuntu-en on 2010-12-06
> **GooKing said:**
> /mythbackend still thinks it's 0.23.
I don't know how mythbuntu control center configures repository for 0.24 PPA or if it interferes with mythbuntu-repos package which you do have also installed. I don't have mythbuntu control center installed on my backend, repository is configured using mythbuntu-repos.
Although your previous post including output of "dpkg -l myth*" has stripped some of the version information away (btw. it's better use CODE tags for such listings), I would do following in your case:

1. download the latest mythbuntu-repos package and install it:

[http://www.mythbuntu.org/files/mythbuntu-repos.deb]("http://www.mythbuntu.org/files/mythbuntu-repos.deb")

Installation should ask you questions about the configuration, but if it does not you must run reconfiguration for mythbuntu repos:
```
sudo dpkg-reconfigure mythbuntu-repos
```
2. Answer the questions:
```
Would you like to activate the MythTV Updates repository?
->Yes
Which version of MythTV would you like to update to?
->0.24
Which repo would you like to use?
->PPA
Would you like to activate the Mythbuntu Updates PPA?
->Yes
```
After that you should have file /etc/apt/sources.list.d/mythbuntu-repos.list with following contents:
```
deb http://ppa.launchpad.net/mythbuntu/repos/ubuntu maverick main
deb http://ppa.launchpad.net/mythbuntu/0.24/ubuntu maverick main
deb-src http://ppa.launchpad.net/mythbuntu/0.24/ubuntu maverick main
deb http://ppa.launchpad.net/mythbuntu/testing/ubuntu maverick main
deb-src http://ppa.launchpad.net/mythbuntu/testing/ubuntu maverick main
```

3. Clean your apt-cache and update apt package index
```
sudo apt-get clean
sudo apt-get update
sudo apt-get -u upgrade
```

Afterwards you should have up to date packages of myth* installed:

```
ii  libmyth-0.24-0                                    1:0.24.0+fixes27419-0ubuntu0+mythbuntu2           Common library code for MythTV and add-on modules (runtime)
ii  libmyth-python                                    1:0.24.0+fixes27419-0ubuntu0+mythbuntu2           A python library to access some MythTV features
ii  libmythtv-perl                                    1:0.24.0+fixes27419-0ubuntu0+mythbuntu2           A PERL library to access some MythTV features
ii  mythbrowser                                       1:0.24.0+fixes27419-0ubuntu0+mythbuntu2           A web browser for MythTV
ii  mythbuntu-common                                  0.54-0ubuntu1                                     Mythbuntu application support functions
ii  mythbuntu-control-centre                          0.62-0ubuntu1                                     Mythbuntu Configuration Application
ii  mythbuntu-repos                                   8.8-0ubuntu0+mythbuntu~auto20101122003015         Mythbuntu repository installer
ii  mythmusic                                         1:0.24.0+fixes27419-0ubuntu0+mythbuntu2           Music add-on module for MythTV
ii  mythnetvision                                     1:0.24.0+fixes27419-0ubuntu0+mythbuntu2           A Internet Video Player plugin for MythTV
ii  mythtv                                            1:0.24.0+fixes27419-0ubuntu0+mythbuntu2           A personal video recorder application (client and server)
ii  mythtv-backend                                    1:0.24.0+fixes27419-0ubuntu0+mythbuntu2           A personal video recorder application (server)
ii  mythtv-common                                     1:0.24.0+fixes27419-0ubuntu0+mythbuntu2           A personal video recorder application (common data)
ii  mythtv-database                                   1:0.24.0+fixes27419-0ubuntu0+mythbuntu2           A personal video recorder application (database)
ii  mythtv-doc                                        1:0.24.0+fixes27419-0ubuntu0+mythbuntu2           A personal video recorder application (documentation)
ii  mythtv-frontend                                   1:0.24.0+fixes27419-0ubuntu0+mythbuntu2           A personal video recorder application (client)
ii  mythtv-status                                     0.9.3-1                                           Show the status of a MythTV backend
ii  mythtv-theme-arclight                             1:0.24.0+fixes27419-0ubuntu0+mythbuntu2           The arclight MythTV Theme
ii  mythtv-theme-childish                             1:0.24.0+fixes27419-0ubuntu0+mythbuntu2           The childish MythTV Theme
ii  mythtv-theme-graphite                             1:0.24.0+fixes27419-0ubuntu0+mythbuntu2           The graphite MythTV Theme
ii  mythtv-theme-metallurgy                           1:0.24.0+fixes27419-0ubuntu0+mythbuntu2           The metallurgy MythTV Theme
ii  mythtv-theme-mythbuntu                            1:0.24.0+fixes27419-0ubuntu0+mythbuntu2           The mythbuntu MythTV Theme
ii  mythtv-themes                                     1:0.24.0+fixes27419-0ubuntu0+mythbuntu2           Themes for MythTV
ii  mythtv-transcode-utils                            1:0.24.0+fixes27419-0ubuntu0+mythbuntu2           Utilities used for transcoding MythTV tasks
ii  mythvideo                                         1:0.24.0+fixes27419-0ubuntu0+mythbuntu2           A generic video player frontend module for MythTV
ii  mythweather                                       1:0.24.0+fixes27419-0ubuntu0+mythbuntu2           Weather add-on module for MythTV
ii  mythweb                                           1:0.24.0+fixes27419-0ubuntu0+mythbuntu2           Web interface add-on module for MythTV
```

...and "mythbackend --version" should give (with current version):

```
Please attach all output as a file in bug reports.
MythTV Version   : 27419
MythTV Branch    : branches/release-0-24-fixes
Network Protocol : 63
Library API      : 0.24.20101129-1
QT Version       : 4.7.0
Options compiled in:
 linux debug using_alsa using_jack using_oss using_pulse using_pulseoutput using_backend using_bindings_perl using_bindings_python using_dvb using_firewire using_frontend using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_bindings_perl using_bindings_python using_mythtranscode using_opengl using_vdpau using_ffmpeg_threads using_live using_mheg
```

---

### Post by tgm4883 on 2010-12-06
The ability to configure the repos via mythbuntu control centre is given by installing the mythbuntu-repos package. The mythbuntu-repos package is what adds that functionality to mythbuntu control centre (it's a plugin)

---

### Post by tgm4883 on 2010-12-06
Out of curiosity, what is the output of

```
which mythbackend
```

---

### Post by GooKing on 2010-12-06
Seems I must have broken something serious...

download new repository failed as I already had a newer version.

/etc/apt/sources.list.d/mythbuntu-repos.list already had the exact lines as you gave. No other relevant repositories found

Ran the clean and update, which updated a couple of other packages, but not any myth components.

the results are still the same, with --version showing the old version, but dpkg showing the new one

which mythbackend reports "/usr/local/bin/mythbackend"

As there is nothing else on the system, i'm going to wipe and do a clean install of mythbuntu, and get a fresh start. In theory it should only take an hour!

Thanks for  all your help with  this.

---

### Post by tgm4883 on 2010-12-06
> **GooKing said:**
> Seems I must have broken something serious...

download new repository failed as I already had a newer version.

/etc/apt/sources.list.d/mythbuntu-repos.list already had the exact lines as you gave. No other relevant repositories found

Ran the clean and update, which updated a couple of other packages, but not any myth components.

the results are still the same, with --version showing the old version, but dpkg showing the new one

which mythbackend reports "/usr/local/bin/mythbackend"

As there is nothing else on the system, i'm going to wipe and do a clean install of mythbuntu, and get a fresh start. In theory it should only take an hour!

Thanks for  all your help with  this.

Did you try to compile mythtv yourself at some point or load someone elses packages? We don't install to /usr/local/bin/mythbackend, we install to /usr/bin/mythbackend

---

### Post by GooKing on 2010-12-06
The initial install of Myth was based on a guide found that recommended using a version downloaded and them compiled with make install, etc.

As this system is not really for anything else I'll install mythbuntu to get a simpler set-up - just need to find and re-install lirc and hauppuge drivers. There's no recordings to save, and I suspect I can fix it much faster this way and get a 'standard' system for the future!

---

### Post by tgm4883 on 2010-12-06
> **GooKing said:**
> The initial install of Myth was based on a guide found that recommended using a version downloaded and them compiled with make install, etc.

As this system is not really for anything else I'll install mythbuntu to get a simpler set-up - just need to find and re-install lirc and hauppuge drivers. There's no recordings to save, and I suspect I can fix it much faster this way and get a 'standard' system for the future!

That much have been an old guide and was likely the issue then, you weren't using mythbackend provided by the packages from the mythbuntu repos, you were using mythbackend that you had compiled yourself.

---

### Post by GooKing on 2010-12-08
Now reloaded, reconfigured, and working.  Couple of issues with incorrect file permissions, but managed to locate the logs, which pointed me in the right direction.

Thanks to TGM and jms-ubuntu for their help and patience!

---

### Post by perevera on 2011-06-11
Well, I am having the exact very problem, although I could not solve it as indicated.

There is a mismatch between information from packages installed:

[I]$ dpkg -l | grep myth
rc  libmyth-0.23-0                        0.23.1+fixes26437-0ubuntu1                         Common library code for MythTV and add-on modules (runtime)
ii  libmyth-0.24-0                        2:0.24.1+fixes.20110609.4dec7cf-0ubuntu0mythbuntu3 Common library code for MythTV and add-on modules (runtime)
ii  libmyth-python                        2:0.24.1+fixes.20110609.4dec7cf-0ubuntu0mythbuntu3 A python library to access some MythTV features
ii  libmythes-1.2-0                       2:1.2.1-1                                          simple thesaurus library
ii  libmythtv-perl                        2:0.24.1+fixes.20110609.4dec7cf-0ubuntu0mythbuntu3 A PERL library to access some MythTV features
ii  mythbuntu-repos                       9.2-0ubuntu0+mythbuntu~auto20110516001227          Mythbuntu repository installer
ii  mythes-en-us                          1:3.3.0-2ubuntu2                                   English Thesaurus for LibreOffice/OpenOffice.org
ii  mythtv-backend                        2:0.24.1+fixes.20110609.4dec7cf-0ubuntu0mythbuntu3 A personal video recorder application (server)
ii  mythtv-common                         2:0.24.1+fixes.20110609.4dec7cf-0ubuntu0mythbuntu3 A personal video recorder application (common data)
ii  mythtv-database                       2:0.24.1+fixes.20110609.4dec7cf-0ubuntu0mythbuntu3 A personal video recorder application (database)
ii  mythtv-frontend                       2:0.24.1+fixes.20110609.4dec7cf-0ubuntu0mythbuntu3 A personal video recorder application (client)
ii  mythtv-theme-mythbuntu                2:0.24.1+fixes.20110609.4dec7cf-0ubuntu0mythbuntu3 The mythbuntu MythTV Theme
ii  mythtv-transcode-utils                2:0.24.1+fixes.20110609.4dec7cf-0ubuntu0mythbuntu3 Utilities used for transcoding MythTV tasks[/I]

and what the actual exe files are:

[I]$ mythbackend --version
Please attach all output as a file in bug reports.
MythTV Version   : 27053
MythTV Branch    : branches/release-0-23-fixes
Network Protocol : 23056
Library API      : 0.23.1.201000710-1
QT Version       : 4.6.2
Options compiled in:
 linux release using_oss using_alsa using_pulse using_jack using_pulseoutput using_backend using_dvb using_firewire using_frontend using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmc_vld using_xvmcw using_bindings_perl using_bindings_python using_opengl using_vdpau using_ffmpeg_threads using_libavc_5_3 using_live using_mheg[/I]

[I]$ mythfrontend --version
Please attach all output as a file in bug reports.
MythTV Version   : 27053
MythTV Branch    : branches/release-0-23-fixes
Network Protocol : 23056
Library API      : 0.23.1.201000710-1
QT Version       : 4.6.2
Options compiled in:
 linux release using_oss using_alsa using_pulse using_jack using_pulseoutput using_backend using_dvb using_firewire using_frontend using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmc_vld using_xvmcw using_bindings_perl using_bindings_python using_opengl using_vdpau using_ffmpeg_threads using_libavc_5_3 using_live using_mheg[/I]

So, 'dpkg' is telling me I have installed 0.24.1 version but when executing programs they say they are 0.23.1. As a consequence, I'm unable to run 'mythtv-setup' or 'mythfrontend' against the actual database, getting the known error message:

***Error: MythTV datbase has newer TV schema (1264) than expected (1254).***

Any suggestion?

---

### Post by tgm4883 on 2011-06-11
> **perevera said:**
> Well, I am having the exact very problem, although I could not solve it as indicated.

There is a mismatch between information from packages installed:

[I]$ dpkg -l | grep myth
rc  libmyth-0.23-0                        0.23.1+fixes26437-0ubuntu1                         Common library code for MythTV and add-on modules (runtime)
ii  libmyth-0.24-0                        2:0.24.1+fixes.20110609.4dec7cf-0ubuntu0mythbuntu3 Common library code for MythTV and add-on modules (runtime)
ii  libmyth-python                        2:0.24.1+fixes.20110609.4dec7cf-0ubuntu0mythbuntu3 A python library to access some MythTV features
ii  libmythes-1.2-0                       2:1.2.1-1                                          simple thesaurus library
ii  libmythtv-perl                        2:0.24.1+fixes.20110609.4dec7cf-0ubuntu0mythbuntu3 A PERL library to access some MythTV features
ii  mythbuntu-repos                       9.2-0ubuntu0+mythbuntu~auto20110516001227          Mythbuntu repository installer
ii  mythes-en-us                          1:3.3.0-2ubuntu2                                   English Thesaurus for LibreOffice/OpenOffice.org
ii  mythtv-backend                        2:0.24.1+fixes.20110609.4dec7cf-0ubuntu0mythbuntu3 A personal video recorder application (server)
ii  mythtv-common                         2:0.24.1+fixes.20110609.4dec7cf-0ubuntu0mythbuntu3 A personal video recorder application (common data)
ii  mythtv-database                       2:0.24.1+fixes.20110609.4dec7cf-0ubuntu0mythbuntu3 A personal video recorder application (database)
ii  mythtv-frontend                       2:0.24.1+fixes.20110609.4dec7cf-0ubuntu0mythbuntu3 A personal video recorder application (client)
ii  mythtv-theme-mythbuntu                2:0.24.1+fixes.20110609.4dec7cf-0ubuntu0mythbuntu3 The mythbuntu MythTV Theme
ii  mythtv-transcode-utils                2:0.24.1+fixes.20110609.4dec7cf-0ubuntu0mythbuntu3 Utilities used for transcoding MythTV tasks[/I]

and what the actual exe files are:

[I]$ mythbackend --version
Please attach all output as a file in bug reports.
MythTV Version   : 27053
MythTV Branch    : branches/release-0-23-fixes
Network Protocol : 23056
Library API      : 0.23.1.201000710-1
QT Version       : 4.6.2
Options compiled in:
 linux release using_oss using_alsa using_pulse using_jack using_pulseoutput using_backend using_dvb using_firewire using_frontend using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmc_vld using_xvmcw using_bindings_perl using_bindings_python using_opengl using_vdpau using_ffmpeg_threads using_libavc_5_3 using_live using_mheg[/I]

[I]$ mythfrontend --version
Please attach all output as a file in bug reports.
MythTV Version   : 27053
MythTV Branch    : branches/release-0-23-fixes
Network Protocol : 23056
Library API      : 0.23.1.201000710-1
QT Version       : 4.6.2
Options compiled in:
 linux release using_oss using_alsa using_pulse using_jack using_pulseoutput using_backend using_dvb using_firewire using_frontend using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmc_vld using_xvmcw using_bindings_perl using_bindings_python using_opengl using_vdpau using_ffmpeg_threads using_libavc_5_3 using_live using_mheg[/I]

So, 'dpkg' is telling me I have installed 0.24.1 version but when executing programs they say they are 0.23.1. As a consequence, I'm unable to run 'mythtv-setup' or 'mythfrontend' against the actual database, getting the known error message:

***Error: MythTV datbase has newer TV schema (1264) than expected (1254).***

Any suggestion?

Did you restart the backend?

---

### Post by perevera on 2011-06-12
Yes, tgm4883, it happens even after restarting the system.

Thanks for answering.

---

### Post by tgm4883 on 2011-06-12
> **perevera said:**
> Yes, tgm4883, it happens even after restarting the system.

Thanks for answering.

Verify that libmyth-0.23-0 is not installed

```
apt-get remove libmyth-0.23-0
```

---

### Post by perevera on 2011-06-12
> **tgm4883 said:**
> Verify that libmyth-0.23-0 is not installed

```
apt-get remove libmyth-0.23-0
```

Yes, indeed, this library is uninstalled:

$ dpkg -l | grep myth
***rc***  libmyth-0.23-0                        0.23.1+fixes26437-0ubuntu1                         Common library code for MythTV and add-on modules (runtime)
ii  libmyth-0.24-0                        2:0.24.1+fixes.20110609.4dec7cf-0ubuntu0mythbuntu3 Common library code for MythTV and add-on modules (runtime)

---

### Post by tgm4883 on 2011-06-12
> **perevera said:**
> Yes, indeed, this library is uninstalled:

$ dpkg -l | grep myth
***rc***  libmyth-0.23-0                        0.23.1+fixes26437-0ubuntu1                         Common library code for MythTV and add-on modules (runtime)
ii  libmyth-0.24-0                        2:0.24.1+fixes.20110609.4dec7cf-0ubuntu0mythbuntu3 Common library code for MythTV and add-on modules (runtime)

Yes thanks I did see that the first time. But please tell me how it is possible to be running 0.23.1 binaries after rebooting when you don't have 0.23.1 code on the machine.

Have you ever compiled from binary? What does this return

```
which mythfrontend
which mythbackend
```

---

### Post by perevera on 2011-06-16
> **tgm4883 said:**
> Yes thanks I did see that the first time. But please tell me how it is possible to be running 0.23.1 binaries after rebooting when you don't have 0.23.1 code on the machine.

Have you ever compiled from binary? What does this return

```
which mythfrontend
which mythbackend
```

Yes, tgm4883, you are completely right.

In the old times I was using a compiled version, so the path where it was finding the binaries was /usr/local/bin.

I have to get rid of this installation, though.

Sorry for my late reply.

---

### Post by tgm4883 on 2011-06-16
> **perevera said:**
> Yes, tgm4883, you are completely right.

In the old times I was using a compiled version, so the path where it was finding the binaries was /usr/local/bin.

I have to get rid of this installation, though.

Sorry for my late reply.

Sounds good, remove the old code and it should work fine. Don't forget to mark your thread as solved.

---

