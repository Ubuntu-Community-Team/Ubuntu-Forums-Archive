---
title: "Unsure of installation"
date: 2008-08-13
forum: Multimedia Software
---

### Post by Garratt on 2008-08-13
I have been having dvd playback(not working at all in totem) and audio problems (sound really quiet), so i followed the above guide to installation of "Essential Packages" thread.

It's late at night so i wasn't paying attention to closely, but now after looking at the script i realise I uninstalled most packages. I'm wondering how the install command in X works, does it uninstall then reinstall over the top? or if packages are found to be installed does it just remove them?


After looking at the command in the tutorial it does say to **remove** the programs but does not say to reinstall, so im confused ><

sudo apt-get **remove** gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

why exactly i would want to remove all the java and plugins etc is beyond me so can anyone shed some light on that?


here is the code, im missing a coupld of java things like netbeans etc... but no big deal i can replace them easy enough, im just wondering if i need to repeat the process or not?::


```
garratt@ubuntu:~$ sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
[sudo] password for garratt: 
--23:25:49--  http://www.medibuntu.org/sources.list.d/hardy.list
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving www.medibuntu.org... 87.98.242.110
Connecting to www.medibuntu.org|87.98.242.110|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

100%[====================================>] 226           --.--K/s             

23:25:50 (38.49 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [226/226]

garratt@ubuntu:~$ wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
OK
Get:1 http://packages.medibuntu.org hardy Release.gpg [189B]                   
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_AU               
Get:2 http://security.ubuntu.com hardy-security Release.gpg [189B]             
Ign http://security.ubuntu.com hardy-security/main Translation-en_AU           
Hit http://au.archive.ubuntu.com hardy Release.gpg                             
Ign http://au.archive.ubuntu.com hardy/main Translation-en_AU                  
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_AU    
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_AU                      
Ign http://packages.medibuntu.org hardy/free Translation-en_AU                 
Ign http://packages.medibuntu.org hardy/non-free Translation-en_AU             
Hit http://archive.canonical.com hardy Release                                 
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_AU     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_AU       
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_AU     
Ign http://repoubuntusoftware.info harty Release.gpg                           
Ign http://repoubuntusoftware.info harty/all Translation-en_AU                 
Ign http://au.archive.ubuntu.com hardy/restricted Translation-en_AU            
Ign http://au.archive.ubuntu.com hardy/universe Translation-en_AU              
Ign http://au.archive.ubuntu.com hardy/multiverse Translation-en_AU            
Hit http://au.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://au.archive.ubuntu.com hardy-updates/main Translation-en_AU          
Ign http://au.archive.ubuntu.com hardy-updates/restricted Translation-en_AU    
Ign http://au.archive.ubuntu.com hardy-updates/universe Translation-en_AU      
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_AU            
Hit http://us.archive.ubuntu.com hardy-updates Release                         
Hit http://packages.medibuntu.org hardy Release                                
Get:3 http://ppa.launchpad.net hardy Release [27.6kB]                          
Ign http://repoubuntusoftware.info harty Release                               
Hit http://archive.canonical.com hardy/partner Sources                         
Get:4 http://security.ubuntu.com hardy-security Release [58.5kB]               
Ign http://au.archive.ubuntu.com hardy-updates/multiverse Translation-en_AU    
Hit http://au.archive.ubuntu.com hardy Release                                 
Hit http://au.archive.ubuntu.com hardy-updates Release                         
Ign http://repoubuntusoftware.info harty/all Packages                          
Hit http://us.archive.ubuntu.com hardy Release                                 
Ign http://ppa.launchpad.net hardy/main Packages                               
Hit http://packages.medibuntu.org hardy/free Packages                          
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://repoubuntusoftware.info harty/all Packages                          
Hit http://au.archive.ubuntu.com hardy/main Packages                           
Hit http://au.archive.ubuntu.com hardy/restricted Packages                     
Hit http://au.archive.ubuntu.com hardy/main Sources                            
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources              
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages             
Ign http://ppa.launchpad.net hardy/main Sources                                
Hit http://packages.medibuntu.org hardy/non-free Packages                      
Hit http://au.archive.ubuntu.com hardy/restricted Sources                      
Hit http://au.archive.ubuntu.com hardy/universe Packages                       
Hit http://au.archive.ubuntu.com hardy/universe Sources                        
Hit http://au.archive.ubuntu.com hardy/multiverse Packages                     
Hit http://au.archive.ubuntu.com hardy/multiverse Sources                      
Hit http://us.archive.ubuntu.com hardy/multiverse Sources                      
Hit http://us.archive.ubuntu.com hardy/multiverse Packages                     
Hit http://au.archive.ubuntu.com hardy-updates/main Packages                   
Hit http://au.archive.ubuntu.com hardy-updates/restricted Packages          
Hit http://au.archive.ubuntu.com hardy-updates/main Sources                 
Hit http://ppa.launchpad.net hardy/main Packages                            
Hit http://au.archive.ubuntu.com hardy-updates/restricted Sources           
Hit http://au.archive.ubuntu.com hardy-updates/universe Packages
Hit http://au.archive.ubuntu.com hardy-updates/universe Sources
Hit http://au.archive.ubuntu.com hardy-updates/multiverse Packages          
Hit http://au.archive.ubuntu.com hardy-updates/multiverse Sources           
Hit http://ppa.launchpad.net hardy/main Sources                             
Get:5 http://security.ubuntu.com hardy-security/main Packages [53.8kB]
Get:6 http://security.ubuntu.com hardy-security/restricted Packages [6636B]
Get:7 http://security.ubuntu.com hardy-security/main Sources [12.3kB]
Get:8 http://security.ubuntu.com hardy-security/restricted Sources [908B]
Get:9 http://security.ubuntu.com hardy-security/universe Packages [27.8kB]
Get:10 http://security.ubuntu.com hardy-security/universe Sources [4387B]
Get:11 http://security.ubuntu.com hardy-security/multiverse Packages [8222B]
Get:12 http://security.ubuntu.com hardy-security/multiverse Sources [14B]
Fetched 173kB in 4s (34.7kB/s)
Reading package lists... Done
W: Duplicate sources.list entry http://repoubuntusoftware.info harty/all Packages (/var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
garratt@ubuntu:~$ gksudo gedit /etc/apt/sources.list
garratt@ubuntu:~$ sudo apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package icedtea-gcjwebplugin is not installed, so not removed
Package libflash-mozplugin is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libswing-layout-java libfreemarker-java javahelp2 xserver-xorg-video-psb
  subversion liblucene2-java libnb-platform7-devel-java libdb4.5-java
  libjtidy-java libnb-platform7-java libxml-commons-resolver1.1-java
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libappframework-java libbeansbinding-java libini4j-java
  libnb-apisupport1-java libnb-ide8-java libnb-java1-java
  libnb-javaparser-java libnb-svnclientadapter-java libswingworker-java
  netbeans openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib
0 upgraded, 0 newly installed, 13 to remove and 1 not upgraded.
After this operation, 131MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 209387 files and directories currently installed.)
Removing netbeans ...
Removing libnb-apisupport1-java ...
Removing libnb-java1-java ...
Removing libappframework-java ...
Removing libbeansbinding-java ...
Removing libnb-ide8-java ...
Removing libini4j-java ...
Removing libnb-javaparser-java ...
Removing libnb-svnclientadapter-java ...
Removing libswingworker-java ...
Removing openjdk-6-jre ...
Removing openjdk-6-jre-headless ...
Removing openjdk-6-jre-lib ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-oss is already the newest version.
faac is already the newest version.
faad is already the newest version.
flashplugin-nonfree is already the newest version.
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-bad-multiverse is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
gstreamer0.10-pitfdll is already the newest version.
liblame0 is already the newest version.
liblame0 set to manually installed.
sun-java6-jre is already the newest version.
sun-java6-plugin is already the newest version.
unrar is already the newest version.
The following packages were automatically installed and are no longer required:
  libswing-layout-java libfreemarker-java javahelp2 xserver-xorg-video-psb
  subversion libaccess-bridge-java liblucene2-java tzdata-java
  libnb-platform7-devel-java libdb4.5-java libjtidy-java
  libnb-platform7-java libxml-commons-resolver1.1-java
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  non-free-codecs sun-java6-fonts
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 3716B of archives.
After this operation, 147kB of additional disk space will be used.
Get:1 http://au.archive.ubuntu.com hardy/multiverse sun-java6-fonts 6-06-0ubuntu1 [1816B]
Get:2 http://packages.medibuntu.org hardy/non-free non-free-codecs 1.1 [1900B]
Fetched 3716B in 0s (4273B/s)         
Selecting previously deselected package sun-java6-fonts.
(Reading database ... 208067 files and directories currently installed.)
Unpacking sun-java6-fonts (from .../sun-java6-fonts_6-06-0ubuntu1_all.deb) ...
Selecting previously deselected package non-free-codecs.
Unpacking non-free-codecs (from .../non-free-codecs_1.1_i386.deb) ...
Setting up sun-java6-fonts (6-06-0ubuntu1) ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-lucida
No CIDSupplement specified for Taza-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for Penheulim-Regular, defaulting to 0.
No CIDSupplement specified for Pilgi-Regular, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for Graphic-Bold, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Graphic-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for JamoDotum-Regular, defaulting to 0.
No CIDSupplement specified for Yetgul-Regular, defaulting to 0.
No CIDSupplement specified for Pilgi-Bold, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for JamoSora-Regular, defaulting to 0.
No CIDSupplement specified for JamoNovel-Regular, defaulting to 0.
No CIDSupplement specified for Shinmun-Regular, defaulting to 0.
No CIDSupplement specified for Pen-Regular, defaulting to 0.
No CIDSupplement specified for JamoBatang-Regular, defaulting to 0.
No CIDSupplement specified for ZenKai-Medium, defaulting to 0.
No CIDSupplement specified for Bom-Regular, defaulting to 0.
No CIDSupplement specified for Gungseo-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.

Setting up non-free-codecs (1.1) ...
garratt@ubuntu:~$ sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kaffeine-mozilla is not installed, so not removed
Package mozilla-helix-player is not installed, so not removed
Package mozilla-plugin-vlc is not installed, so not removed
Package totem-mozilla is not installed, so not removed
Package xine-plugin is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libswing-layout-java libfreemarker-java javahelp2 xserver-xorg-video-psb
  subversion libaccess-bridge-java liblucene2-java tzdata-java
  libnb-platform7-devel-java libdb4.5-java libjtidy-java
  libnb-platform7-java libxml-commons-resolver1.1-java
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mozilla-mplayer
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 1839kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 208084 files and directories currently installed.)
Removing mozilla-mplayer ...
garratt@ubuntu:~$ sudo apt-get install mplayer mozilla-mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mplayer is already the newest version.
The following packages were automatically installed and are no longer required:
  libswing-layout-java libfreemarker-java javahelp2 xserver-xorg-video-psb
  subversion libaccess-bridge-java liblucene2-java tzdata-java
  libnb-platform7-devel-java libdb4.5-java libjtidy-java
  libnb-platform7-java libxml-commons-resolver1.1-java
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  mozilla-mplayer
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/506kB of archives.
After this operation, 1839kB of additional disk space will be used.
Selecting previously deselected package mozilla-mplayer.
(Reading database ... 208007 files and directories currently installed.)
Unpacking mozilla-mplayer (from .../mozilla-mplayer_3.50-1ubuntu2.1_i386.deb) ...
Setting up mozilla-mplayer (3.50-1ubuntu2.1) ...
garratt@ubuntu:~$ gedit $HOME/.mplayer/mplayerplug-in.conf
garratt@ubuntu:~$ gedit $HOME/.mplayer/mplayerplug-in.conf
garratt@ubuntu:~$ gksudo gedit /etc/apt/sources.list 
garratt@ubuntu:~$ sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread3 is already the newest version.
libdvdnav4 is already the newest version.
The following packages were automatically installed and are no longer required:
  libswing-layout-java libfreemarker-java javahelp2 xserver-xorg-video-psb
  subversion libaccess-bridge-java liblucene2-java tzdata-java
  libnb-platform7-devel-java libdb4.5-java libjtidy-java
  libnb-platform7-java libxml-commons-resolver1.1-java
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libdvbpsi4 libebml0 libmatroska0 libtar libvlc0 libwxbase2.6-0
  libwxgtk2.6-0 libxosd2 vlc-nox vlc-plugin-pulse
Suggested packages:
  regionset xfonts-base-transcoded mozilla-plugin-vlc
Recommended packages:
  videolan-doc
The following NEW packages will be installed:
  libdvbpsi4 libdvdcss2 libebml0 libmatroska0 libtar libvlc0 libwxbase2.6-0
  libwxgtk2.6-0 libxosd2 vlc vlc-nox vlc-plugin-pulse
0 upgraded, 12 newly installed, 0 to remove and 1 not upgraded.
Need to get 10.5MB of archives.
After this operation, 29.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://au.archive.ubuntu.com hardy/universe libdvbpsi4 0.1.5-3 [32.2kB]
Get:2 http://packages.medibuntu.org hardy/free libdvdcss2 1.2.9-2medibuntu4 [36.3kB]
Get:3 http://security.ubuntu.com hardy-security/multiverse libvlc0 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1 [826kB]
Get:4 http://au.archive.ubuntu.com hardy/universe libebml0 0.7.7-3.1 [63.7kB]
Get:5 http://au.archive.ubuntu.com hardy/universe libmatroska0 0.8.1-1 [190kB]
Get:6 http://au.archive.ubuntu.com hardy/universe libtar 1.2.11-4 [19.0kB]
Get:7 http://au.archive.ubuntu.com hardy/universe libwxbase2.6-0 2.6.3.2.2-2ubuntu4 [556kB]
Get:8 http://au.archive.ubuntu.com hardy/universe libwxgtk2.6-0 2.6.3.2.2-2ubuntu4 [2837kB]
Get:9 http://security.ubuntu.com hardy-security/multiverse vlc-nox 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1 [4746kB]
Get:10 http://au.archive.ubuntu.com hardy/universe libxosd2 2.2.14-1.4 [25.1kB]
Get:11 http://security.ubuntu.com hardy-security/multiverse vlc-plugin-pulse 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1 [6954B]
Get:12 http://security.ubuntu.com hardy-security/multiverse vlc 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1 [1140kB]
Fetched 10.5MB in 1min38s (106kB/s)                                          
Selecting previously deselected package libdvbpsi4.
(Reading database ... 208085 files and directories currently installed.)
Unpacking libdvbpsi4 (from .../libdvbpsi4_0.1.5-3_i386.deb) ...
Selecting previously deselected package libdvdcss2.
Unpacking libdvdcss2 (from .../libdvdcss2_1.2.9-2medibuntu4_i386.deb) ...
Selecting previously deselected package libebml0.
Unpacking libebml0 (from .../libebml0_0.7.7-3.1_i386.deb) ...
Selecting previously deselected package libmatroska0.
Unpacking libmatroska0 (from .../libmatroska0_0.8.1-1_i386.deb) ...
Selecting previously deselected package libtar.
Unpacking libtar (from .../libtar_1.2.11-4_i386.deb) ...
Selecting previously deselected package libvlc0.
Unpacking libvlc0 (from .../libvlc0_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1_i386.deb) ...
Selecting previously deselected package libwxbase2.6-0.
Unpacking libwxbase2.6-0 (from .../libwxbase2.6-0_2.6.3.2.2-2ubuntu4_i386.deb) ...
Selecting previously deselected package libwxgtk2.6-0.
Unpacking libwxgtk2.6-0 (from .../libwxgtk2.6-0_2.6.3.2.2-2ubuntu4_i386.deb) ...

Selecting previously deselected package libxosd2.
Unpacking libxosd2 (from .../libxosd2_2.2.14-1.4_i386.deb) ...
Selecting previously deselected package vlc-nox.
Unpacking vlc-nox (from .../vlc-nox_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1_i386.deb) ...
Selecting previously deselected package vlc-plugin-pulse.
Unpacking vlc-plugin-pulse (from .../vlc-plugin-pulse_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1_i386.deb) ...
Selecting previously deselected package vlc.
Unpacking vlc (from .../vlc_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1_i386.deb) ...
Setting up libdvbpsi4 (0.1.5-3) ...

Setting up libdvdcss2 (1.2.9-2medibuntu4) ...

Setting up libebml0 (0.7.7-3.1) ...

Setting up libmatroska0 (0.8.1-1) ...

Setting up libtar (1.2.11-4) ...

Setting up libvlc0 (0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1) ...

Setting up libwxbase2.6-0 (2.6.3.2.2-2ubuntu4) ...

Setting up libwxgtk2.6-0 (2.6.3.2.2-2ubuntu4) ...

Setting up libxosd2 (2.2.14-1.4) ...

Setting up vlc-nox (0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1) ...
Setting up vlc-plugin-pulse (0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1) ...
Setting up vlc (0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
garratt@ubuntu:~$ gksudo gedit /etc/gnome/defaults.list
garratt@ubuntu:~$ 


```

Additionaly, dvd playback is working now, but audio is still very quite in some applications such as mplayer totem, etc. volume on full, both system, mplayer, and speakers... and its at a normal volume level when it should pretty much be blowing my eardrums out.

---

### Post by pmlxuser on 2008-08-13
sometimes other programs are uninstalled because you are installing a program they depend on "dependency" because the library they use is based on the program you are trying to uninstall.

so before executing a commang you should carefully read the message that is displayed about dependecy (if you use synaptic this is very transparent) if you use command prompt you find the text are many and the windows tendecy of saying OK chips in.

for the sound thing did you restart your computer?? just incase ;))

---

### Post by Garratt on 2008-08-13
but reading thru the code, you command to UNINSTALL all the java stuff... but i can't see where or if at all it reinstalls them.

so do i need to redo that command supplementing sudo apt-get REMOVE with sudo apt get install

and if so why the hell doesn't it state that in the tutorial?

---

### Post by Garratt on 2008-08-13
bump

---

