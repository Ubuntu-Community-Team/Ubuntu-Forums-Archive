---
title: "Possible solution to problems with timidity install when switching to Ubuntu Studio"
date: 2008-02-22
forum: Multimedia Production
---

### Post by davidshere on 2008-02-22
I had a vanilla installation of Gutsy which I recently decided to upgrade/switch to Ubuntu Studio.  I issued this command:

```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

But I had a problem with the install of timidity:

```
Setting up timidity (2.13.2-15ubuntu1) ...
 * Starting timidity                                                                                                                             
 * Starting TiMidity++ ALSA midi emulation...                                                                                                   
 ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix.device'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
                                                                                                                                          [fail]
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
```

I tried running the install command again but got the same error.  Then did an su to root and ran this:

```
apt-get update && apt-get dist-upgrade && apt-get dist-upgrade
```

and everything installed correctly.  It appears that installing from the actual superuser account was more effective than doing it from a normal user using the "sudo" command.  Here is the entire shebang:

```
david@lancer:~$ sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
Get:1 http://packages.medibuntu.org feisty Release.gpg [189B]
Get:2 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]                                                 
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_US                                           
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_US                                         
Get:3 http://us.archive.ubuntu.com gutsy Release.gpg [191B]                                                      
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US                                                           
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US                        
Get:4 http://security.ubuntu.com gutsy-security Release.gpg [191B]                         
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US                       
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US                                       
Get:5 http://archive.canonical.com gutsy Release.gpg [191B]                                                      
Ign http://archive.canonical.com gutsy/partner Translation-en_US                                                 
Get:6 http://archive.ubuntu.com gutsy-security Release.gpg [191B]                                                
Ign http://archive.ubuntu.com gutsy-security/main Translation-en_US                                              
Ign http://archive.ubuntu.com gutsy-security/restricted Translation-en_US                                        
Ign http://archive.ubuntu.com gutsy-security/universe Translation-en_US                                          
Ign http://archive.ubuntu.com gutsy-security/multiverse Translation-en_US                                        
Hit http://archive.ubuntu.com gutsy-updates Release                                                              
Ign http://packages.medibuntu.org feisty/free Translation-en_US                                                  
Ign http://packages.medibuntu.org feisty/non-free Translation-en_US                                              
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US                                                
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
Get:7 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release
Get:8 http://us.archive.ubuntu.com gutsy-backports Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-backports/restricted Translation-en_US
Hit http://archive.canonical.com gutsy Release                                                                  
Hit http://packages.medibuntu.org feisty Release                                                               
Hit http://archive.ubuntu.com gutsy-security Release                                                           
Ign http://us.archive.ubuntu.com gutsy-backports/universe Translation-en_US                                    
Ign http://us.archive.ubuntu.com gutsy-backports/multiverse Translation-en_US              
Hit http://us.archive.ubuntu.com gutsy Release                                             
Hit http://us.archive.ubuntu.com gutsy-updates Release                                                           
Hit http://security.ubuntu.com gutsy-security/main Packages                                                                           
Hit http://archive.ubuntu.com gutsy-updates/universe Packages                                                                         
Hit http://archive.ubuntu.com gutsy-updates/multiverse Packages                                                  
Hit http://archive.canonical.com gutsy/partner Packages                                                          
Hit http://us.archive.ubuntu.com gutsy-backports Release                                   
Ign http://packages.medibuntu.org feisty/free Packages                                                                                
Hit http://security.ubuntu.com gutsy-security/restricted Packages                                                                     
Hit http://security.ubuntu.com gutsy-security/main Sources                                                       
Hit http://security.ubuntu.com gutsy-security/restricted Sources                                                 
Hit http://archive.ubuntu.com gutsy-security/main Packages                                                       
Hit http://archive.ubuntu.com gutsy-security/restricted Packages                                                 
Hit http://archive.ubuntu.com gutsy-security/universe Packages                                                   
Hit http://archive.ubuntu.com gutsy-security/multiverse Packages                                                 
Hit http://archive.canonical.com gutsy/partner Sources                                                           
Hit http://us.archive.ubuntu.com gutsy/main Packages                                       
Hit http://us.archive.ubuntu.com gutsy/restricted Packages           
Hit http://us.archive.ubuntu.com gutsy/main Sources                  
Hit http://us.archive.ubuntu.com gutsy/restricted Sources            
Hit http://us.archive.ubuntu.com gutsy/universe Packages             
Ign http://packages.medibuntu.org feisty/non-free Packages           
Hit http://security.ubuntu.com gutsy-security/universe Packages      
Hit http://security.ubuntu.com gutsy-security/universe Sources       
Hit http://security.ubuntu.com gutsy-security/multiverse Packages    
Hit http://security.ubuntu.com gutsy-security/multiverse Sources     
Hit http://us.archive.ubuntu.com gutsy/universe Sources              
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Ign http://packages.medibuntu.org feisty/free Sources
Ign http://packages.medibuntu.org feisty/non-free Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://packages.medibuntu.org feisty/free Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-backports/main Packages
Hit http://us.archive.ubuntu.com gutsy-backports/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-backports/universe Packages
Hit http://us.archive.ubuntu.com gutsy-backports/multiverse Packages
Hit http://packages.medibuntu.org feisty/non-free Packages
Hit http://packages.medibuntu.org feisty/free Sources
Hit http://us.archive.ubuntu.com gutsy-backports/main Sources
Hit http://us.archive.ubuntu.com gutsy-backports/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-backports/universe Sources
Hit http://us.archive.ubuntu.com gutsy-backports/multiverse Sources
Hit http://packages.medibuntu.org feisty/non-free Sources
Fetched 196B in 1s (112B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcompizconfig0 libdecoration0 libcompizconfig-backend-gconf compiz-plugins libaudacious5 libxine1-gnome compiz-fusion-plugins-extra compiz
  compiz-core compiz-fusion-plugins-main compiz-gnome
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  aconnectgui aeolus agave alsa-tools alsa-tools-gui ardour audacious-plugins-extra autopano-sift beast bitscope blender blop bristol caps
  cinepaint cinepaint-data cmt creox csound denemo dssi-example-plugins dssi-host-jack dssi-utils dvgrab enblend ffmpeg2theora fftw3
  fil-plugins fluidsynth fluidsynth-dssi fontforge freebirth freebirth-data freepats freqtweak gimp-gap gimp-ufraw gnome-raw-thumbnailer
  gnome-specimen gtick gtk2-engines-murrine guile-1.8 guile-1.8-libs hexter hugin hugin-bin hugin-data hugin-tools hydrogen inkscape jack-rack
  jack-tools jackbeat jackeq jamin jdelay khelpcenter kino ladcca2 ladspa-sdk libbinio1c2 libboost-thread1.34.1 libcinepaint0 libclalsadrv1
  libclthreads2 libclxclient3 libdv-bin libexiv2-0 libfltk1.1 libfluidsynth1 libgconfmm-2.6-1c2 libgdiplus libgig6 libglademm-2.4-1c2a
  libgnomecanvasmm-2.6-1c2a libgtkmm1.2-0c2a libjack0.100.0-0 liblash2 liblo0 liblrdf0 liblscp libmpeg3-1 libmxml1 libpano12-0 libpano12-bin
  libplot2c2 libportaudio2 libprojectm1 libprojectm1-data libqt4-core libqt4-gui libresid-builder0c2a libsidplay2 libsigc++-1.2-5c2
  libsigc++0c2 libsynfig0 libsynfigapp0 libuninameslist0 libxml++2.6c2a lilypond lilypond-data linux-image-2.6.22-14-rt linux-image-rt
  linux-restricted-modules-2.6.22-14-rt linux-restricted-modules-rt linux-ubuntu-modules-2.6.22-14-rt mcp-plugins meterbridge mixxx mixxx-data
  mpg321 muse nautilus-image-converter omins patchage pitivi puredata python-twisted python-twisted-bin python-twisted-conch
  python-twisted-core python-twisted-lore python-twisted-mail python-twisted-names python-twisted-news python-twisted-runner python-twisted-web
  python-twisted-words python-zopeinterface qamix qjackctl qsampler qsynth rosegarden rosegarden-data rosegarden4 scribus seq24 shaketracker
  sndfile-programs sooperlooper stopmotion stops swami swh-plugins synfigstudio tap-plugins tapiir terminatorx tetex-bin tex-common texinfo
  texlive texlive-base texlive-base-bin texlive-common texlive-doc-base texlive-fonts-recommended texlive-latex-base texlive-latex-recommended
  timemachine timidity tk707 ubuntustudio-default-settings ubuntustudio-gdm-theme ubuntustudio-icon-theme ubuntustudio-look ubuntustudio-menu
  ubuntustudio-screensaver ubuntustudio-sounds ubuntustudio-theme ubuntustudio-wallpapers usplash-theme-ubuntustudio vcf vkeybd wacom-tools
  xsynth-dssi yafray zynaddsubfx
Suggested packages:
  csound-doc fftw3-dev fontforge-doc potrace autotrace guile-1.8-doc dia dia-gnome libxml-xql-perl skencil htdig liblo0-dev liblrdf0-dev
  libpano12-dev linux-doc-2.6.22 linux-source-2.6.22 nvidia-glx nvidia-glx-legacy nvidia-glx-new avm-fritz-firmware-2.6.22-14 ams om
  python-twisted-bin-dbg python-profiler python-twisted-runner-dbg python-zopeinterface-dbg scribus-template scribus-doc fam ladspa-plugin
  texlive-generic-recommended texlive-doc-en pmidi
Recommended packages:
  bse-alsa libwmf-bin pstoedit perlmagick python-numpy exiv2 qt4-qtconfig lilypond-doc gem python-serial vgrabbj dvipdfmx lmodern perl-tk tipa
  prosper latex-beamer latex-xcolor
The following packages will be REMOVED:
  ubuntu-desktop ubuntu-sounds
The following NEW packages will be installed:
  aconnectgui aeolus agave alsa-tools alsa-tools-gui ardour audacious-plugins-extra autopano-sift beast bitscope blender blop bristol caps
  cinepaint cinepaint-data cmt creox csound denemo dssi-example-plugins dssi-host-jack dssi-utils dvgrab enblend ffmpeg2theora fftw3
  fil-plugins fluidsynth fluidsynth-dssi fontforge freebirth freebirth-data freepats freqtweak gimp-gap gimp-ufraw gnome-raw-thumbnailer
  gnome-specimen gtick gtk2-engines-murrine guile-1.8 guile-1.8-libs hexter hugin hugin-bin hugin-data hugin-tools hydrogen inkscape jack-rack
  jack-tools jackbeat jackeq jamin jdelay khelpcenter kino ladcca2 ladspa-sdk libbinio1c2 libboost-thread1.34.1 libcinepaint0 libclalsadrv1
  libclthreads2 libclxclient3 libdv-bin libexiv2-0 libfltk1.1 libfluidsynth1 libgconfmm-2.6-1c2 libgdiplus libgig6 libglademm-2.4-1c2a
  libgnomecanvasmm-2.6-1c2a libgtkmm1.2-0c2a libjack0.100.0-0 liblash2 liblo0 liblrdf0 liblscp libmpeg3-1 libmxml1 libpano12-0 libpano12-bin
  libplot2c2 libportaudio2 libprojectm1 libprojectm1-data libqt4-core libqt4-gui libresid-builder0c2a libsidplay2 libsigc++-1.2-5c2
  libsigc++0c2 libsynfig0 libsynfigapp0 libuninameslist0 libxml++2.6c2a lilypond lilypond-data linux-image-2.6.22-14-rt linux-image-rt
  linux-restricted-modules-2.6.22-14-rt linux-restricted-modules-rt linux-rt linux-ubuntu-modules-2.6.22-14-rt mcp-plugins meterbridge mixxx
  mixxx-data mpg321 muse nautilus-image-converter omins patchage pitivi puredata python-twisted python-twisted-bin python-twisted-conch
  python-twisted-core python-twisted-lore python-twisted-mail python-twisted-names python-twisted-news python-twisted-runner python-twisted-web
  python-twisted-words python-zopeinterface qamix qjackctl qsampler qsynth rosegarden rosegarden-data rosegarden4 scribus seq24 shaketracker
  sndfile-programs sooperlooper stopmotion stops swami swh-plugins synfigstudio tap-plugins tapiir terminatorx tetex-bin tex-common texinfo
  texlive texlive-base texlive-base-bin texlive-common texlive-doc-base texlive-fonts-recommended texlive-latex-base texlive-latex-recommended
  timemachine timidity tk707 ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-default-settings ubuntustudio-desktop
  ubuntustudio-gdm-theme ubuntustudio-graphics ubuntustudio-icon-theme ubuntustudio-look ubuntustudio-menu ubuntustudio-screensaver
  ubuntustudio-sounds ubuntustudio-theme ubuntustudio-video ubuntustudio-wallpapers usplash-theme-ubuntustudio vcf vkeybd wacom-tools
  xsynth-dssi yafray zynaddsubfx
0 upgraded, 185 newly installed, 2 to remove and 0 not upgraded.
Need to get 286MB of archives.
After unpacking 749MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://security.ubuntu.com gutsy-security/main libqt4-core 4.3.2-0ubuntu3.2 [1769kB]
Get:2 http://us.archive.ubuntu.com gutsy/universe libbinio1c2 1.4-6 [27.6kB]
Get:3 http://us.archive.ubuntu.com gutsy/universe ladcca2 0.4.0-6 [20.0kB]
Get:4 http://us.archive.ubuntu.com gutsy/universe libjack0.100.0-0 0.103.0-6ubuntu1 [12.7kB]
Get:5 http://us.archive.ubuntu.com gutsy/universe libfluidsynth1 1.0.7a-1 [156kB]
Get:6 http://us.archive.ubuntu.com gutsy-backports/main libprojectm1-data 1.01-3~gutsy1 [409kB]
Get:7 http://us.archive.ubuntu.com gutsy-backports/universe libprojectm1 1.01-3~gutsy1 [229kB]
Get:8 http://us.archive.ubuntu.com gutsy/universe libresid-builder0c2a 2.1.1-5 [35.7kB]
Get:9 http://us.archive.ubuntu.com gutsy/universe libsidplay2 2.1.1-5 [102kB]
Get:10 http://us.archive.ubuntu.com gutsy-backports/universe audacious-plugins-extra 1.4.4-1ubuntu1~gutsy1 [1158kB]
Get:11 http://security.ubuntu.com gutsy-security/main libqt4-gui 4.3.2-0ubuntu3.2 [4887kB]
Get:12 http://us.archive.ubuntu.com gutsy/main tex-common 1.9 [711kB]                                                                           
Get:13 http://us.archive.ubuntu.com gutsy/main texlive-common 2007-10 [72.8kB]                                                                  
Get:14 http://us.archive.ubuntu.com gutsy/main texlive-doc-base 2007-3 [750kB]                                                                  
Get:15 http://us.archive.ubuntu.com gutsy-updates/main texlive-base-bin 2007-12ubuntu3.1 [11.0MB]                                               
Get:16 http://us.archive.ubuntu.com gutsy/main texlive-base 2007-10 [6156kB]                                                                    
Get:17 http://us.archive.ubuntu.com gutsy/main texlive-fonts-recommended 2007-10 [9583kB]                                                       
Get:18 http://us.archive.ubuntu.com gutsy/main texlive-latex-base 2007-10 [27.1MB]                                                              
Get:19 http://us.archive.ubuntu.com gutsy/main texlive-latex-recommended 2007-10 [19.8MB]                                                       
Get:20 http://us.archive.ubuntu.com gutsy/main texlive 2007-10 [14.7kB]                                                                         
Get:21 http://us.archive.ubuntu.com gutsy/main tetex-bin 2007-10 [14.9kB]                                                                       
Get:22 http://us.archive.ubuntu.com gutsy/main texinfo 4.8.dfsg.1-6 [300kB]                                                                     
Get:23 http://us.archive.ubuntu.com gutsy/universe lilypond-data 2.10.25-0ubuntu1 [3637kB]                                                      
Get:24 http://us.archive.ubuntu.com gutsy-updates/universe linux-image-2.6.22-14-rt 2.6.22-14.52 [18.6MB]                                       
Get:25 http://us.archive.ubuntu.com gutsy/universe linux-ubuntu-modules-2.6.22-14-rt 2.6.22-14.37 [3077kB]                                      
Get:26 http://us.archive.ubuntu.com gutsy/main libfltk1.1 1.1.7-4ubuntu1 [399kB]                                                                
Get:27 http://us.archive.ubuntu.com gutsy/universe aconnectgui 0.9.0rc2-1-9 [25.5kB]                                                            
Get:28 http://us.archive.ubuntu.com gutsy/main libgconfmm-2.6-1c2 2.20.0-0ubuntu1 [33.6kB]                                                      
Get:29 http://us.archive.ubuntu.com gutsy/main libglademm-2.4-1c2a 2.6.5-0ubuntu1 [23.5kB]                                                      
Get:30 http://us.archive.ubuntu.com gutsy/universe agave 0.4.3-1 [367kB]                                                                        
Get:31 http://us.archive.ubuntu.com gutsy/universe liblo0 0.23-2.1build1 [25.7kB]                                                               
Get:32 http://us.archive.ubuntu.com gutsy/universe liblrdf0 0.4.0-1build1 [19.7kB]                                                              
Get:33 http://us.archive.ubuntu.com gutsy/main python-twisted-bin 2.5.0-2build1 [21.0kB]                                                        
Get:34 http://us.archive.ubuntu.com gutsy/main python-zopeinterface 3.3.1-3build2 [134kB]                                                       
Get:35 http://us.archive.ubuntu.com gutsy/main python-twisted-core 2.5.0-2build1 [753kB]                                                        
Get:36 http://us.archive.ubuntu.com gutsy/main python-twisted-conch 1:0.8.0-1 [173kB]                                                           
Get:37 http://us.archive.ubuntu.com gutsy/main python-twisted-mail 0.4.0-1 [164kB]                                                              
Get:38 http://us.archive.ubuntu.com gutsy/main python-twisted-web 0.7.0-1 [316kB]                                                               
Get:39 http://us.archive.ubuntu.com gutsy/main python-twisted-lore 0.3.0-1 [75.9kB]                                                             
Get:40 http://us.archive.ubuntu.com gutsy/main python-twisted-names 0.4.0-1 [46.7kB]                                                            
Get:41 http://us.archive.ubuntu.com gutsy/main python-twisted-news 0.3.0-1 [26.2kB]                                                             
Get:42 http://us.archive.ubuntu.com gutsy/main python-twisted-runner 0.2.0-2 [18.0kB]                                                           
Get:43 http://us.archive.ubuntu.com gutsy/main python-twisted-words 0.5.0-1.1 [197kB]                                                           
Get:44 http://us.archive.ubuntu.com gutsy/main python-twisted 2.5.0-2build1 [8958B]                                                             
Get:45 http://us.archive.ubuntu.com gutsy-backports/universe ardour 1:2.1-1~gutsy1 [6545kB]                                                     
Get:46 http://us.archive.ubuntu.com gutsy/main libgdiplus 1.2.4-2ubuntu1 [344kB]                                                                
Get:47 http://us.archive.ubuntu.com gutsy/universe autopano-sift 2.4-0ubuntu6 [151kB]                                                           
Get:48 http://us.archive.ubuntu.com gutsy/universe bitscope 1.1-6ubuntu2 [131kB]                                                                
Get:49 http://us.archive.ubuntu.com gutsy-backports/universe blender 2.45-1ubuntu2~gutsy1 [7304kB]                                              
Get:50 http://us.archive.ubuntu.com gutsy/universe blop 0.2.8-5 [933kB]                                                                         
Get:51 http://us.archive.ubuntu.com gutsy/universe bristol 0.9.1-13 [342kB]                                                                     
Get:52 http://us.archive.ubuntu.com gutsy/universe caps 0.3.0-3 [188kB]                                                                         
Get:53 http://us.archive.ubuntu.com gutsy/universe libcinepaint0 0.22-1-0ubuntu1 [166kB]                                                        
Get:54 http://us.archive.ubuntu.com gutsy/universe cinepaint-data 0.22-1-0ubuntu1 [2730kB]                                                      
Get:55 http://us.archive.ubuntu.com gutsy/universe cinepaint 0.22-1-0ubuntu1 [1971kB]                                                           
Get:56 http://us.archive.ubuntu.com gutsy/universe cmt 1.15-3.1 [59.0kB]                                                                        
Get:57 http://us.archive.ubuntu.com gutsy/universe creox 0.2.2rc2-3ubuntu3 [292kB]                                                              
Get:58 http://us.archive.ubuntu.com gutsy/universe csound 1:4.23f13-1.1 [3320kB]                                                                
Get:59 http://us.archive.ubuntu.com gutsy/main denemo 0.7.5-4ubuntu3 [986kB]                                                                    
Get:60 http://us.archive.ubuntu.com gutsy/universe dssi-example-plugins 0.9.1-2build1 [59.9kB]                                                  
Get:61 http://us.archive.ubuntu.com gutsy/universe dssi-host-jack 0.9.1-2build1 [19.9kB]                                                        
Get:62 http://us.archive.ubuntu.com gutsy/universe dssi-utils 0.9.1-2build1 [9726B]                                                             
Get:63 http://us.archive.ubuntu.com gutsy/universe ffmpeg2theora 0.19-1 [25.5kB]                                                                
Get:64 http://us.archive.ubuntu.com gutsy/main fftw3 3.1.2-2ubuntu2 [1030kB]                                                                    
Get:65 http://us.archive.ubuntu.com gutsy/universe fil-plugins 0.1.0-2 [7706B]                                                                  
Get:66 http://us.archive.ubuntu.com gutsy/universe fluidsynth 1.0.7a-1 [37.5kB]                                                                 
Get:67 http://us.archive.ubuntu.com gutsy/universe fluidsynth-dssi 0.9.1-3ubuntu1 [43.7kB]                                                      
Get:68 http://us.archive.ubuntu.com gutsy/main libuninameslist0 0.0.20060907-2 [449kB]                                                          
Get:69 http://us.archive.ubuntu.com gutsy/main fontforge 0.0.20070607-3 [3541kB]                                                                
Get:70 http://us.archive.ubuntu.com gutsy/universe freepats 20060219-1 [29.0MB]                                                                 
Get:71 http://us.archive.ubuntu.com gutsy/universe libsigc++-1.2-5c2 1.2.7-2 [21.1kB]                                                           
Get:72 http://us.archive.ubuntu.com gutsy/universe freqtweak 0.7.0~cvs20070510-0ubuntu1 [350kB]                                                 
Get:73 http://us.archive.ubuntu.com gutsy/universe libmpeg3-1 1.5.4-5 [76.7kB]                                                                  
Get:74 http://us.archive.ubuntu.com gutsy-backports/universe gimp-gap 2.2.2-1~gutsy1 [2466kB]                                                   
Get:75 http://us.archive.ubuntu.com gutsy/main libexiv2-0 0.15-1ubuntu2 [346kB]                                                                 
Get:76 http://us.archive.ubuntu.com gutsy/universe gimp-ufraw 0.11-2ubuntu3 [249kB]                                                             
Get:77 http://us.archive.ubuntu.com gutsy/universe gnome-raw-thumbnailer 2.0.1-0ubuntu5 [15.9kB]                                                
Get:78 http://us.archive.ubuntu.com gutsy/universe gnome-specimen 0.2-0ubuntu1 [60.2kB]                                                         
Get:79 http://us.archive.ubuntu.com gutsy/main gtk2-engines-murrine 0.53.1-0ubuntu2 [39.2kB]                                                    
Get:80 http://us.archive.ubuntu.com gutsy/universe guile-1.8-libs 1.8.1+1-5 [669kB]                                                             
Get:81 http://us.archive.ubuntu.com gutsy/universe guile-1.8 1.8.1+1-5 [7716B]                                                                  
Get:82 http://us.archive.ubuntu.com gutsy/universe hexter 0.6.1-2ubuntu1 [181kB]                                                                
Get:83 http://us.archive.ubuntu.com gutsy-updates/universe libboost-thread1.34.1 1.34.1-2ubuntu1.1 [37.0kB]                                     
Get:84 http://us.archive.ubuntu.com gutsy/universe libpano12-0 2.8.4-0build1 [190kB]                                                            
Get:85 http://us.archive.ubuntu.com gutsy-updates/universe hugin-data 0.7~beta4-0ubuntu3.1 [1039kB]                                             
Get:86 http://us.archive.ubuntu.com gutsy-updates/universe hugin-bin 0.7~beta4-0ubuntu3.1 [2575kB]                                              
Get:87 http://us.archive.ubuntu.com gutsy-updates/universe hugin-tools 0.7~beta4-0ubuntu3.1 [5051kB]                                            
Get:88 http://us.archive.ubuntu.com gutsy/universe libpano12-bin 2.8.4-0build1 [40.4kB]                                                         
Get:89 http://us.archive.ubuntu.com gutsy/universe libplot2c2 2.5-2 [874kB]                                                                     
Get:90 http://us.archive.ubuntu.com gutsy/universe enblend 3.0.dfsg.1-0ubuntu3 [852kB]                                                          
Get:91 http://us.archive.ubuntu.com gutsy-updates/universe hugin 0.7~beta4-0ubuntu3.1 [91.4kB]                                                  
Get:92 http://us.archive.ubuntu.com gutsy/universe hydrogen 0.9.3-4ubuntu2 [3354kB]                                                             
Get:93 http://us.archive.ubuntu.com gutsy/main inkscape 0.45.1-1ubuntu5 [10.7MB]                                                                
Get:94 http://us.archive.ubuntu.com gutsy/universe swh-plugins 0.4.15-0.1 [459kB]                                                               
Get:95 http://us.archive.ubuntu.com gutsy/universe jack-rack 1.4.4-3ubuntu1 [61.7kB]                                                            
Get:96 http://us.archive.ubuntu.com gutsy/universe jack-tools 0.0.2-4.1 [67.0kB]                                                                
Get:97 http://us.archive.ubuntu.com gutsy/universe jackbeat 0.6.1-1ubuntu1 [60.6kB]                                                             
Get:98 http://us.archive.ubuntu.com gutsy/universe jackeq 0.4.1-1ubuntu2 [164kB]                                                                
Get:99 http://us.archive.ubuntu.com gutsy/universe jamin 0.95.0-4 [582kB]                                                                       
Get:100 http://us.archive.ubuntu.com gutsy/universe jdelay 1.0-0ubuntu1 [6374B]                                                                 
Get:101 http://us.archive.ubuntu.com gutsy-updates/main khelpcenter 4:3.5.8-0ubuntu2.2 [2318kB]                                                 
Get:102 http://us.archive.ubuntu.com gutsy/universe ladspa-sdk 1.1-6 [39.6kB]                                                                   
Get:103 http://us.archive.ubuntu.com gutsy/universe libclalsadrv1 1.2.2-1ubuntu2 [12.1kB]                                                       
Get:104 http://us.archive.ubuntu.com gutsy/universe libgig6 3.1.1-0.1 [111kB]                                                                   
Get:105 http://us.archive.ubuntu.com gutsy/main libgnomecanvasmm-2.6-1c2a 2.20.0-0ubuntu1 [88.9kB]                                              
Get:106 http://us.archive.ubuntu.com gutsy/universe libsigc++0c2 1.0.4-9.1ubuntu2 [21.8kB]                                                      
Get:107 http://us.archive.ubuntu.com gutsy/universe libgtkmm1.2-0c2a 1.2.10-8ubuntu2 [418kB]                                                    
Get:108 http://us.archive.ubuntu.com gutsy/universe liblash2 0.5.3-1 [25.9kB]                                                                   
Get:109 http://us.archive.ubuntu.com gutsy/universe liblscp 0.3.1-1 [20.9kB]                                                                    
Get:110 http://us.archive.ubuntu.com gutsy/universe libmxml1 2.2-2 [21.4kB]                                                                     
Get:111 http://us.archive.ubuntu.com gutsy/universe libportaudio2 19+svn20070125-1ubuntu2 [53.7kB]                                              
Get:112 http://us.archive.ubuntu.com gutsy/main libxml++2.6c2a 2.20.0-0ubuntu1 [70.9kB]                                                         
Get:113 http://us.archive.ubuntu.com gutsy/universe lilypond 2.10.25-0ubuntu1 [1336kB]                                                          
Get:114 http://us.archive.ubuntu.com gutsy/universe linux-image-rt 2.6.22.14.21 [25.4kB]                                                        
Get:115 http://us.archive.ubuntu.com gutsy-updates/multiverse linux-restricted-modules-2.6.22-14-rt 2.6.22.4-14.10 [16.8MB]                     
Get:116 http://us.archive.ubuntu.com gutsy/multiverse linux-restricted-modules-rt 2.6.22.14.21 [25.4kB]                                         
Get:117 http://us.archive.ubuntu.com gutsy/multiverse linux-rt 2.6.22.14.21 [25.4kB]                                                            
Get:118 http://us.archive.ubuntu.com gutsy/universe mcp-plugins 0.3.0-4 [21.8kB]                                                                
Get:119 http://us.archive.ubuntu.com gutsy/universe meterbridge 0.9.2-6ubuntu2 [531kB]                                                          
Get:120 http://us.archive.ubuntu.com gutsy/universe mixxx-data 1.5.2svn~20070807dfsg-0ubuntu1 [2672kB]                                          
Get:121 http://us.archive.ubuntu.com gutsy/universe mixxx 1.5.2svn~20070807dfsg-0ubuntu1 [433kB]                                                
Get:122 http://us.archive.ubuntu.com gutsy/universe mpg321 0.2.10.3 [34.5kB]                                                                    
Get:123 http://us.archive.ubuntu.com gutsy/universe muse 0.8.1a-5 [5412kB]                                                                      
Get:124 http://us.archive.ubuntu.com gutsy/universe nautilus-image-converter 0.0.9-0ubuntu1 [19.6kB]                                            
Get:125 http://us.archive.ubuntu.com gutsy/universe omins 0.2.0-5 [27.3kB]                                                                      
Get:126 http://us.archive.ubuntu.com gutsy/universe patchage 0.2.3-2.1 [66.2kB]                                                                 
Get:127 http://us.archive.ubuntu.com gutsy/universe pitivi 0.10.3-1 [172kB]                                                                     
Get:128 http://us.archive.ubuntu.com gutsy/universe puredata 0.40.2-2 [1555kB]                                                                  
Get:129 http://us.archive.ubuntu.com gutsy/universe qamix 0.0.7e-0ubuntu2 [68.9kB]                                                              
Get:130 http://us.archive.ubuntu.com gutsy/universe qjackctl 0.2.22-2ubuntu1 [376kB]                                                            
Get:131 http://us.archive.ubuntu.com gutsy/universe qsampler 0.1.2-0ubuntu2 [177kB]                                                             
Get:132 http://us.archive.ubuntu.com gutsy/universe qsynth 0.2.5-2ubuntu1 [185kB]                                                               
Get:133 http://us.archive.ubuntu.com gutsy/universe rosegarden-data 1:1.5.1-3ubuntu1 [4687kB]                                                   
Get:134 http://us.archive.ubuntu.com gutsy/universe sndfile-programs 1.0.17-4 [72.9kB]                                                          
Get:135 http://us.archive.ubuntu.com gutsy/universe rosegarden 1:1.5.1-3ubuntu1 [3474kB]                                                        
Get:136 http://us.archive.ubuntu.com gutsy/universe rosegarden4 1:1.5.1-3ubuntu1 [7104B]                                                        
Get:137 http://us.archive.ubuntu.com gutsy-backports/main scribus 1.3.3.11.dfsg-1ubuntu3~gutsy1 [9440kB]                                        
Get:138 http://us.archive.ubuntu.com gutsy/universe seq24 0.8.7-1ubuntu1 [262kB]                                                                
Get:139 http://us.archive.ubuntu.com gutsy/universe shaketracker 0.4.6-5build1 [451kB]                                                          
Get:140 http://us.archive.ubuntu.com gutsy/universe sooperlooper 1.0.8c-2ubuntu2 [524kB]                                                        
Get:141 http://us.archive.ubuntu.com gutsy/universe stopmotion 0.6.0-1 [2299kB]                                                                 
Get:142 http://us.archive.ubuntu.com gutsy/universe swami 0.9.4-1 [458kB]                                                                       
Get:143 http://us.archive.ubuntu.com gutsy/universe tap-plugins 0.7.0-2 [602kB]                                                                 
Get:144 http://us.archive.ubuntu.com gutsy/universe tapiir 0.7.1-9 [172kB]                                                                      
Get:145 http://us.archive.ubuntu.com gutsy/universe terminatorx 3.82-7ubuntu2 [337kB]                                                           
Get:146 http://us.archive.ubuntu.com gutsy/universe timemachine 0.3.0-3ubuntu1 [84.0kB]                                                         
Get:147 http://us.archive.ubuntu.com gutsy/universe timidity 2.13.2-15ubuntu1 [555kB]                                                           
Get:148 http://us.archive.ubuntu.com gutsy/universe tk707 0.7.21-9 [141kB]                                                                      
Get:149 http://us.archive.ubuntu.com gutsy/universe alsa-tools 1.0.14-1ubuntu2 [82.7kB]                                                         
Get:150 http://us.archive.ubuntu.com gutsy/universe alsa-tools-gui 1.0.14-1ubuntu2 [260kB]                                                      
Get:151 http://us.archive.ubuntu.com gutsy/universe beast 0.6.6-9 [4199kB]                                                                      
Get:152 http://us.archive.ubuntu.com gutsy/universe freebirth-data 0.3.2-8 [2307kB]                                                             
Get:153 http://us.archive.ubuntu.com gutsy/universe freebirth 0.3.2-8 [110kB]                                                                   
Get:154 http://us.archive.ubuntu.com gutsy/universe gtick 0.3.15-1 [129kB]                                                                      
Get:155 http://us.archive.ubuntu.com gutsy/universe vkeybd 1:0.1.17b-1 [30.3kB]                                                                 
Get:156 http://us.archive.ubuntu.com gutsy/universe zynaddsubfx 2.2.1-4 [972kB]                                                                 
Get:157 http://us.archive.ubuntu.com gutsy/universe ubuntustudio-audio 0.11 [3512B]                                                             
Get:158 http://us.archive.ubuntu.com gutsy/universe libclthreads2 2.2.1-2 [12.1kB]                                                              
Get:159 http://us.archive.ubuntu.com gutsy/universe libclxclient3 3.3.2-1 [45.5kB]                                                              
Get:160 http://us.archive.ubuntu.com gutsy/universe stops 0.3.0-1 [39.3kB]                                                                      
Get:161 http://us.archive.ubuntu.com gutsy/universe aeolus 0.6.6+2-4 [111kB]                                                                    
Get:162 http://us.archive.ubuntu.com gutsy/universe vcf 0.0.5-5ubuntu1 [17.4kB]                                                                 
Get:163 http://us.archive.ubuntu.com gutsy/universe xsynth-dssi 0.9.0-2ubuntu1 [159kB]                                                          
Get:164 http://us.archive.ubuntu.com gutsy/universe ubuntustudio-audio-plugins 0.11 [3326B]                                                     
Get:165 http://us.archive.ubuntu.com gutsy/universe ubuntustudio-theme 0.14 [16.2kB]                                                            
Get:166 http://us.archive.ubuntu.com gutsy/universe ubuntustudio-wallpapers 0.14 [2671kB]                                                       
Get:167 http://us.archive.ubuntu.com gutsy/universe ubuntustudio-gdm-theme 0.14 [762kB]                                                         
Get:168 http://us.archive.ubuntu.com gutsy/universe ubuntustudio-icon-theme 0.4 [1518kB]                                                        
Get:169 http://us.archive.ubuntu.com gutsy/universe ubuntustudio-sounds 0.5 [4262kB]                                                            
Get:170 http://us.archive.ubuntu.com gutsy/universe ubuntustudio-look 0.14 [11.2kB]                                                             
Get:171 http://us.archive.ubuntu.com gutsy/universe ubuntustudio-default-settings 0.5 [16.7kB]                                                  
Get:172 http://us.archive.ubuntu.com gutsy/universe ubuntustudio-menu 0.5 [5276B]                                                               
Get:173 http://us.archive.ubuntu.com gutsy/universe ubuntustudio-screensaver 0.2 [18.6kB]                                                       
Get:174 http://us.archive.ubuntu.com gutsy/universe usplash-theme-ubuntustudio 0.15 [116kB]                                                     
Get:175 http://us.archive.ubuntu.com gutsy/universe ubuntustudio-desktop 0.11 [4266B]                                                           
Get:176 http://us.archive.ubuntu.com gutsy/universe libdv-bin 1.0.0-1ubuntu1 [50.2kB]                                                           
Get:177 http://us.archive.ubuntu.com gutsy/universe libsynfig0 0.61.06-2 [1137kB]                                                               
Get:178 http://us.archive.ubuntu.com gutsy/universe libsynfigapp0 0.61.06-1 [498kB]                                                             
Get:179 http://us.archive.ubuntu.com gutsy/universe synfigstudio 0.61.06-1 [2171kB]                                                             
Get:180 http://us.archive.ubuntu.com gutsy/main wacom-tools 1:0.7.7.7-0ubuntu2 [53.0kB]                                                         
Get:181 http://us.archive.ubuntu.com gutsy/universe yafray 0.0.9-2 [636kB]                                                                      
Get:182 http://us.archive.ubuntu.com gutsy/universe ubuntustudio-graphics 0.11 [3362B]                                                          
Get:183 http://us.archive.ubuntu.com gutsy/universe dvgrab 3.0-1 [124kB]                                                                        
Get:184 http://us.archive.ubuntu.com gutsy/main kino 1.1.0-3ubuntu2 [4354kB]                                                                    
Get:185 http://us.archive.ubuntu.com gutsy/universe ubuntustudio-video 0.11 [3268B]                                                             
Fetched 286MB in 13m1s (367kB/s)                                                                                                                
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 134773 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing ubuntu-sounds ...
Selecting previously deselected package libbinio1c2.
(Reading database ... 134749 files and directories currently installed.)
Unpacking libbinio1c2 (from .../libbinio1c2_1.4-6_i386.deb) ...
Selecting previously deselected package ladcca2.
Unpacking ladcca2 (from .../ladcca2_0.4.0-6_i386.deb) ...
Selecting previously deselected package libjack0.100.0-0.
Unpacking libjack0.100.0-0 (from .../libjack0.100.0-0_0.103.0-6ubuntu1_all.deb) ...
Selecting previously deselected package libfluidsynth1.
Unpacking libfluidsynth1 (from .../libfluidsynth1_1.0.7a-1_i386.deb) ...
Selecting previously deselected package libprojectm1-data.
Unpacking libprojectm1-data (from .../libprojectm1-data_1.01-3~gutsy1_all.deb) ...
Selecting previously deselected package libprojectm1.
Unpacking libprojectm1 (from .../libprojectm1_1.01-3~gutsy1_i386.deb) ...
Selecting previously deselected package libresid-builder0c2a.
Unpacking libresid-builder0c2a (from .../libresid-builder0c2a_2.1.1-5_i386.deb) ...
Selecting previously deselected package libsidplay2.
Unpacking libsidplay2 (from .../libsidplay2_2.1.1-5_i386.deb) ...
Selecting previously deselected package audacious-plugins-extra.
Unpacking audacious-plugins-extra (from .../audacious-plugins-extra_1.4.4-1ubuntu1~gutsy1_i386.deb) ...
Selecting previously deselected package tex-common.
Unpacking tex-common (from .../tex-common_1.9_all.deb) ...
Selecting previously deselected package texlive-common.
Unpacking texlive-common (from .../texlive-common_2007-10_all.deb) ...
Selecting previously deselected package texlive-doc-base.
Unpacking texlive-doc-base (from .../texlive-doc-base_2007-3_all.deb) ...
Selecting previously deselected package texlive-base-bin.
Unpacking texlive-base-bin (from .../texlive-base-bin_2007-12ubuntu3.1_i386.deb) ...
Selecting previously deselected package texlive-base.
Unpacking texlive-base (from .../texlive-base_2007-10_all.deb) ...
Selecting previously deselected package texlive-fonts-recommended.
Unpacking texlive-fonts-recommended (from .../texlive-fonts-recommended_2007-10_all.deb) ...
Selecting previously deselected package texlive-latex-base.
Unpacking texlive-latex-base (from .../texlive-latex-base_2007-10_all.deb) ...
Selecting previously deselected package texlive-latex-recommended.
Unpacking texlive-latex-recommended (from .../texlive-latex-recommended_2007-10_all.deb) ...
Selecting previously deselected package texlive.
Unpacking texlive (from .../texlive_2007-10_all.deb) ...
Selecting previously deselected package tetex-bin.
Unpacking tetex-bin (from .../tetex-bin_2007-10_all.deb) ...
Selecting previously deselected package texinfo.
Unpacking texinfo (from .../texinfo_4.8.dfsg.1-6_i386.deb) ...
Setting up tex-common (1.9) ...

Creating config file /etc/texmf/texmf.d/05TeXMF.cnf with new version

Creating config file /etc/texmf/texmf.d/15Plain.cnf with new version

Creating config file /etc/texmf/texmf.d/45TeXinputs.cnf with new version

Creating config file /etc/texmf/texmf.d/55Fonts.cnf with new version

Creating config file /etc/texmf/texmf.d/65BibTeX.cnf with new version

Creating config file /etc/texmf/texmf.d/75DviPS.cnf with new version

Creating config file /etc/texmf/texmf.d/85Misc.cnf with new version

Creating config file /etc/texmf/texmf.d/90TeXDoc.cnf with new version

Creating config file /etc/texmf/texmf.d/95NonPath.cnf with new version

Creating config file /etc/texmf/updmap.d/00updmap.cfg with new version

Creating config file /etc/texmf/texmf.cnf with new version

Setting up texlive-common (2007-10) ...

Setting up texlive-doc-base (2007-3) ...
Running mktexlsr. This may take some time... done.

Setting up texlive-base-bin (2007-12ubuntu3.1) ...
Running mktexlsr. This may take some time... done.
Building format(s) --all.
        This may take some time... done.

Setting up texlive-base (2007-10) ...
Running mktexlsr. This may take some time... done.
Building format(s) --all.
        This may take some time... done.
Running updmap-sys. This may take some time... done.

Setting up texlive-fonts-recommended (2007-10) ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... done.

Setting up texlive-latex-base (2007-10) ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... done.
Building format(s) --all --cnffile /etc/texmf/fmt.d/10texlive-latex-base.cnf.
        This may take some time... done.

Setting up texlive-latex-recommended (2007-10) ...
Running mktexlsr. This may take some time... done.

Setting up texlive (2007-10) ...
Setting up tetex-bin (2007-10) ...
Selecting previously deselected package lilypond-data.
(Reading database ... 144403 files and directories currently installed.)
Unpacking lilypond-data (from .../lilypond-data_2.10.25-0ubuntu1_all.deb) ...
Selecting previously deselected package linux-image-2.6.22-14-rt.
Unpacking linux-image-2.6.22-14-rt (from .../linux-image-2.6.22-14-rt_2.6.22-14.52_i386.deb) ...
Done.
Selecting previously deselected package linux-ubuntu-modules-2.6.22-14-rt.
Unpacking linux-ubuntu-modules-2.6.22-14-rt (from .../linux-ubuntu-modules-2.6.22-14-rt_2.6.22-14.37_i386.deb) ...
Selecting previously deselected package libfltk1.1.
Unpacking libfltk1.1 (from .../libfltk1.1_1.1.7-4ubuntu1_i386.deb) ...
Selecting previously deselected package aconnectgui.
Unpacking aconnectgui (from .../aconnectgui_0.9.0rc2-1-9_i386.deb) ...
Selecting previously deselected package libgconfmm-2.6-1c2.
Unpacking libgconfmm-2.6-1c2 (from .../libgconfmm-2.6-1c2_2.20.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package libglademm-2.4-1c2a.
Unpacking libglademm-2.4-1c2a (from .../libglademm-2.4-1c2a_2.6.5-0ubuntu1_i386.deb) ...
Selecting previously deselected package agave.
Unpacking agave (from .../agave_0.4.3-1_i386.deb) ...
Selecting previously deselected package liblo0.
Unpacking liblo0 (from .../liblo0_0.23-2.1build1_i386.deb) ...
Selecting previously deselected package liblrdf0.
Unpacking liblrdf0 (from .../liblrdf0_0.4.0-1build1_i386.deb) ...
Selecting previously deselected package python-twisted-bin.
Unpacking python-twisted-bin (from .../python-twisted-bin_2.5.0-2build1_i386.deb) ...
Selecting previously deselected package python-zopeinterface.
Unpacking python-zopeinterface (from .../python-zopeinterface_3.3.1-3build2_i386.deb) ...
Selecting previously deselected package python-twisted-core.
Unpacking python-twisted-core (from .../python-twisted-core_2.5.0-2build1_all.deb) ...
Selecting previously deselected package python-twisted-conch.
Unpacking python-twisted-conch (from .../python-twisted-conch_1%3a0.8.0-1_all.deb) ...
Selecting previously deselected package python-twisted-mail.
Unpacking python-twisted-mail (from .../python-twisted-mail_0.4.0-1_all.deb) ...
Selecting previously deselected package python-twisted-web.
Unpacking python-twisted-web (from .../python-twisted-web_0.7.0-1_all.deb) ...
Selecting previously deselected package python-twisted-lore.
Unpacking python-twisted-lore (from .../python-twisted-lore_0.3.0-1_all.deb) ...
Selecting previously deselected package python-twisted-names.
Unpacking python-twisted-names (from .../python-twisted-names_0.4.0-1_all.deb) ...
Selecting previously deselected package python-twisted-news.
Unpacking python-twisted-news (from .../python-twisted-news_0.3.0-1_all.deb) ...
Selecting previously deselected package python-twisted-runner.
Unpacking python-twisted-runner (from .../python-twisted-runner_0.2.0-2_i386.deb) ...
Selecting previously deselected package python-twisted-words.
Unpacking python-twisted-words (from .../python-twisted-words_0.5.0-1.1_all.deb) ...
Selecting previously deselected package python-twisted.
Unpacking python-twisted (from .../python-twisted_2.5.0-2build1_all.deb) ...
Selecting previously deselected package ardour.
Unpacking ardour (from .../ardour_1%3a2.1-1~gutsy1_i386.deb) ...
Selecting previously deselected package libgdiplus.
Unpacking libgdiplus (from .../libgdiplus_1.2.4-2ubuntu1_i386.deb) ...
Selecting previously deselected package autopano-sift.
Unpacking autopano-sift (from .../autopano-sift_2.4-0ubuntu6_all.deb) ...
Selecting previously deselected package bitscope.
Unpacking bitscope (from .../bitscope_1.1-6ubuntu2_i386.deb) ...
Selecting previously deselected package blender.
Unpacking blender (from .../blender_2.45-1ubuntu2~gutsy1_i386.deb) ...
Selecting previously deselected package blop.
Unpacking blop (from .../archives/blop_0.2.8-5_i386.deb) ...
Selecting previously deselected package bristol.
Unpacking bristol (from .../bristol_0.9.1-13_i386.deb) ...
Selecting previously deselected package caps.
Unpacking caps (from .../archives/caps_0.3.0-3_i386.deb) ...
Selecting previously deselected package libcinepaint0.
Unpacking libcinepaint0 (from .../libcinepaint0_0.22-1-0ubuntu1_i386.deb) ...
Selecting previously deselected package cinepaint-data.
Unpacking cinepaint-data (from .../cinepaint-data_0.22-1-0ubuntu1_all.deb) ...
Selecting previously deselected package cinepaint.
Unpacking cinepaint (from .../cinepaint_0.22-1-0ubuntu1_i386.deb) ...
Selecting previously deselected package cmt.
Unpacking cmt (from .../archives/cmt_1.15-3.1_i386.deb) ...
Selecting previously deselected package creox.
Unpacking creox (from .../creox_0.2.2rc2-3ubuntu3_i386.deb) ...
Selecting previously deselected package csound.
Unpacking csound (from .../csound_1%3a4.23f13-1.1_i386.deb) ...
Selecting previously deselected package denemo.
Unpacking denemo (from .../denemo_0.7.5-4ubuntu3_i386.deb) ...
Selecting previously deselected package dssi-example-plugins.
Unpacking dssi-example-plugins (from .../dssi-example-plugins_0.9.1-2build1_i386.deb) ...
Selecting previously deselected package dssi-host-jack.
Unpacking dssi-host-jack (from .../dssi-host-jack_0.9.1-2build1_i386.deb) ...
Selecting previously deselected package dssi-utils.
Unpacking dssi-utils (from .../dssi-utils_0.9.1-2build1_i386.deb) ...
Selecting previously deselected package ffmpeg2theora.
Unpacking ffmpeg2theora (from .../ffmpeg2theora_0.19-1_i386.deb) ...
Selecting previously deselected package fftw3.
Unpacking fftw3 (from .../fftw3_3.1.2-2ubuntu2_i386.deb) ...
Selecting previously deselected package fil-plugins.
Unpacking fil-plugins (from .../fil-plugins_0.1.0-2_i386.deb) ...
Selecting previously deselected package fluidsynth.
Unpacking fluidsynth (from .../fluidsynth_1.0.7a-1_i386.deb) ...
Selecting previously deselected package fluidsynth-dssi.
Unpacking fluidsynth-dssi (from .../fluidsynth-dssi_0.9.1-3ubuntu1_i386.deb) ...
Selecting previously deselected package libuninameslist0.
Unpacking libuninameslist0 (from .../libuninameslist0_0.0.20060907-2_i386.deb) ...
Selecting previously deselected package fontforge.
Unpacking fontforge (from .../fontforge_0.0.20070607-3_i386.deb) ...
Selecting previously deselected package freepats.
Unpacking freepats (from .../freepats_20060219-1_all.deb) ...
Selecting previously deselected package libsigc++-1.2-5c2.
Unpacking libsigc++-1.2-5c2 (from .../libsigc++-1.2-5c2_1.2.7-2_i386.deb) ...
Selecting previously deselected package freqtweak.
Unpacking freqtweak (from .../freqtweak_0.7.0~cvs20070510-0ubuntu1_i386.deb) ...
Selecting previously deselected package libmpeg3-1.
Unpacking libmpeg3-1 (from .../libmpeg3-1_1.5.4-5_i386.deb) ...
Selecting previously deselected package gimp-gap.
Unpacking gimp-gap (from .../gimp-gap_2.2.2-1~gutsy1_i386.deb) ...
Selecting previously deselected package libexiv2-0.
Unpacking libexiv2-0 (from .../libexiv2-0_0.15-1ubuntu2_i386.deb) ...
Selecting previously deselected package gimp-ufraw.
Unpacking gimp-ufraw (from .../gimp-ufraw_0.11-2ubuntu3_i386.deb) ...
Selecting previously deselected package gnome-raw-thumbnailer.
Unpacking gnome-raw-thumbnailer (from .../gnome-raw-thumbnailer_2.0.1-0ubuntu5_i386.deb) ...
Selecting previously deselected package gnome-specimen.
Unpacking gnome-specimen (from .../gnome-specimen_0.2-0ubuntu1_all.deb) ...
Selecting previously deselected package gtk2-engines-murrine.
Unpacking gtk2-engines-murrine (from .../gtk2-engines-murrine_0.53.1-0ubuntu2_i386.deb) ...
Selecting previously deselected package guile-1.8-libs.
Unpacking guile-1.8-libs (from .../guile-1.8-libs_1.8.1+1-5_i386.deb) ...
Selecting previously deselected package guile-1.8.
Unpacking guile-1.8 (from .../guile-1.8_1.8.1+1-5_i386.deb) ...
Selecting previously deselected package hexter.
Unpacking hexter (from .../hexter_0.6.1-2ubuntu1_i386.deb) ...
Selecting previously deselected package libboost-thread1.34.1.
Unpacking libboost-thread1.34.1 (from .../libboost-thread1.34.1_1.34.1-2ubuntu1.1_i386.deb) ...
Selecting previously deselected package libpano12-0.
Unpacking libpano12-0 (from .../libpano12-0_2.8.4-0build1_i386.deb) ...
Selecting previously deselected package hugin-data.
Unpacking hugin-data (from .../hugin-data_0.7~beta4-0ubuntu3.1_all.deb) ...
Selecting previously deselected package hugin-bin.
Unpacking hugin-bin (from .../hugin-bin_0.7~beta4-0ubuntu3.1_i386.deb) ...
Selecting previously deselected package hugin-tools.
Unpacking hugin-tools (from .../hugin-tools_0.7~beta4-0ubuntu3.1_i386.deb) ...
Selecting previously deselected package libpano12-bin.
Unpacking libpano12-bin (from .../libpano12-bin_2.8.4-0build1_i386.deb) ...
Selecting previously deselected package libplot2c2.
Unpacking libplot2c2 (from .../libplot2c2_2.5-2_i386.deb) ...
Selecting previously deselected package enblend.
Unpacking enblend (from .../enblend_3.0.dfsg.1-0ubuntu3_i386.deb) ...
Selecting previously deselected package hugin.
Unpacking hugin (from .../hugin_0.7~beta4-0ubuntu3.1_all.deb) ...
Selecting previously deselected package hydrogen.
Unpacking hydrogen (from .../hydrogen_0.9.3-4ubuntu2_i386.deb) ...
Selecting previously deselected package inkscape.
Unpacking inkscape (from .../inkscape_0.45.1-1ubuntu5_i386.deb) ...
Selecting previously deselected package swh-plugins.
Unpacking swh-plugins (from .../swh-plugins_0.4.15-0.1_i386.deb) ...
Selecting previously deselected package jack-rack.
Unpacking jack-rack (from .../jack-rack_1.4.4-3ubuntu1_i386.deb) ...
Selecting previously deselected package jack-tools.
Unpacking jack-tools (from .../jack-tools_0.0.2-4.1_i386.deb) ...
Selecting previously deselected package jackbeat.
Unpacking jackbeat (from .../jackbeat_0.6.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package jackeq.
Unpacking jackeq (from .../jackeq_0.4.1-1ubuntu2_i386.deb) ...
Selecting previously deselected package jamin.
Unpacking jamin (from .../jamin_0.95.0-4_i386.deb) ...
Selecting previously deselected package jdelay.
Unpacking jdelay (from .../jdelay_1.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package khelpcenter.
Unpacking khelpcenter (from .../khelpcenter_4%3a3.5.8-0ubuntu2.2_i386.deb) ...
Selecting previously deselected package ladspa-sdk.
Unpacking ladspa-sdk (from .../ladspa-sdk_1.1-6_i386.deb) ...
Selecting previously deselected package libclalsadrv1.
Unpacking libclalsadrv1 (from .../libclalsadrv1_1.2.2-1ubuntu2_i386.deb) ...
Selecting previously deselected package libgig6.
Unpacking libgig6 (from .../libgig6_3.1.1-0.1_i386.deb) ...
Selecting previously deselected package libgnomecanvasmm-2.6-1c2a.
Unpacking libgnomecanvasmm-2.6-1c2a (from .../libgnomecanvasmm-2.6-1c2a_2.20.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package libsigc++0c2.
Unpacking libsigc++0c2 (from .../libsigc++0c2_1.0.4-9.1ubuntu2_i386.deb) ...
Selecting previously deselected package libgtkmm1.2-0c2a.
Unpacking libgtkmm1.2-0c2a (from .../libgtkmm1.2-0c2a_1.2.10-8ubuntu2_i386.deb) ...
Selecting previously deselected package liblash2.
Unpacking liblash2 (from .../liblash2_0.5.3-1_i386.deb) ...
Selecting previously deselected package liblscp.
Unpacking liblscp (from .../liblscp_0.3.1-1_i386.deb) ...
Selecting previously deselected package libmxml1.
Unpacking libmxml1 (from .../libmxml1_2.2-2_i386.deb) ...
Selecting previously deselected package libportaudio2.
Unpacking libportaudio2 (from .../libportaudio2_19+svn20070125-1ubuntu2_i386.deb) ...
Selecting previously deselected package libqt4-core.
Unpacking libqt4-core (from .../libqt4-core_4.3.2-0ubuntu3.2_i386.deb) ...
Selecting previously deselected package libqt4-gui.
Unpacking libqt4-gui (from .../libqt4-gui_4.3.2-0ubuntu3.2_i386.deb) ...
Selecting previously deselected package libxml++2.6c2a.
Unpacking libxml++2.6c2a (from .../libxml++2.6c2a_2.20.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package lilypond.
Unpacking lilypond (from .../lilypond_2.10.25-0ubuntu1_i386.deb) ...
Selecting previously deselected package linux-image-rt.
Unpacking linux-image-rt (from .../linux-image-rt_2.6.22.14.21_i386.deb) ...
Selecting previously deselected package linux-restricted-modules-2.6.22-14-rt.
Unpacking linux-restricted-modules-2.6.22-14-rt (from .../linux-restricted-modules-2.6.22-14-rt_2.6.22.4-14.10_i386.deb) ...
Selecting previously deselected package linux-restricted-modules-rt.
Unpacking linux-restricted-modules-rt (from .../linux-restricted-modules-rt_2.6.22.14.21_i386.deb) ...
Selecting previously deselected package linux-rt.
Unpacking linux-rt (from .../linux-rt_2.6.22.14.21_i386.deb) ...
Selecting previously deselected package mcp-plugins.
Unpacking mcp-plugins (from .../mcp-plugins_0.3.0-4_i386.deb) ...
Selecting previously deselected package meterbridge.
Unpacking meterbridge (from .../meterbridge_0.9.2-6ubuntu2_i386.deb) ...
Selecting previously deselected package mixxx-data.
Unpacking mixxx-data (from .../mixxx-data_1.5.2svn~20070807dfsg-0ubuntu1_all.deb) ...
Selecting previously deselected package mixxx.
Unpacking mixxx (from .../mixxx_1.5.2svn~20070807dfsg-0ubuntu1_i386.deb) ...
Selecting previously deselected package mpg321.
Unpacking mpg321 (from .../mpg321_0.2.10.3_i386.deb) ...
Selecting previously deselected package muse.
Unpacking muse (from .../muse_0.8.1a-5_i386.deb) ...
Selecting previously deselected package nautilus-image-converter.
Unpacking nautilus-image-converter (from .../nautilus-image-converter_0.0.9-0ubuntu1_i386.deb) ...
Selecting previously deselected package omins.
Unpacking omins (from .../omins_0.2.0-5_i386.deb) ...
Selecting previously deselected package patchage.
Unpacking patchage (from .../patchage_0.2.3-2.1_i386.deb) ...
Selecting previously deselected package pitivi.
Unpacking pitivi (from .../pitivi_0.10.3-1_all.deb) ...
Selecting previously deselected package puredata.
Unpacking puredata (from .../puredata_0.40.2-2_i386.deb) ...
Selecting previously deselected package qamix.
Unpacking qamix (from .../qamix_0.0.7e-0ubuntu2_i386.deb) ...
Selecting previously deselected package qjackctl.
Unpacking qjackctl (from .../qjackctl_0.2.22-2ubuntu1_i386.deb) ...
Selecting previously deselected package qsampler.
Unpacking qsampler (from .../qsampler_0.1.2-0ubuntu2_i386.deb) ...
Selecting previously deselected package qsynth.
Unpacking qsynth (from .../qsynth_0.2.5-2ubuntu1_i386.deb) ...
Selecting previously deselected package rosegarden-data.
Unpacking rosegarden-data (from .../rosegarden-data_1%3a1.5.1-3ubuntu1_all.deb) ...
Selecting previously deselected package sndfile-programs.
Unpacking sndfile-programs (from .../sndfile-programs_1.0.17-4_i386.deb) ...
Selecting previously deselected package rosegarden.
Unpacking rosegarden (from .../rosegarden_1%3a1.5.1-3ubuntu1_i386.deb) ...
Selecting previously deselected package rosegarden4.
Unpacking rosegarden4 (from .../rosegarden4_1%3a1.5.1-3ubuntu1_all.deb) ...
Selecting previously deselected package scribus.
Unpacking scribus (from .../scribus_1.3.3.11.dfsg-1ubuntu3~gutsy1_i386.deb) ...
Selecting previously deselected package seq24.
Unpacking seq24 (from .../seq24_0.8.7-1ubuntu1_i386.deb) ...
Selecting previously deselected package shaketracker.
Unpacking shaketracker (from .../shaketracker_0.4.6-5build1_i386.deb) ...
Selecting previously deselected package sooperlooper.
Unpacking sooperlooper (from .../sooperlooper_1.0.8c-2ubuntu2_i386.deb) ...
Selecting previously deselected package stopmotion.
Unpacking stopmotion (from .../stopmotion_0.6.0-1_i386.deb) ...
Selecting previously deselected package swami.
Unpacking swami (from .../swami_0.9.4-1_i386.deb) ...
Selecting previously deselected package tap-plugins.
Unpacking tap-plugins (from .../tap-plugins_0.7.0-2_i386.deb) ...
Selecting previously deselected package tapiir.
Unpacking tapiir (from .../tapiir_0.7.1-9_i386.deb) ...
Selecting previously deselected package terminatorx.
Unpacking terminatorx (from .../terminatorx_3.82-7ubuntu2_i386.deb) ...
Selecting previously deselected package timemachine.
Unpacking timemachine (from .../timemachine_0.3.0-3ubuntu1_i386.deb) ...
Selecting previously deselected package timidity.
Unpacking timidity (from .../timidity_2.13.2-15ubuntu1_i386.deb) ...
Selecting previously deselected package tk707.
Unpacking tk707 (from .../tk707_0.7.21-9_i386.deb) ...
Selecting previously deselected package alsa-tools.
Unpacking alsa-tools (from .../alsa-tools_1.0.14-1ubuntu2_i386.deb) ...
Selecting previously deselected package alsa-tools-gui.
Unpacking alsa-tools-gui (from .../alsa-tools-gui_1.0.14-1ubuntu2_i386.deb) ...
Selecting previously deselected package beast.
Unpacking beast (from .../beast_0.6.6-9_i386.deb) ...
Selecting previously deselected package freebirth-data.
Unpacking freebirth-data (from .../freebirth-data_0.3.2-8_all.deb) ...
Selecting previously deselected package freebirth.
Unpacking freebirth (from .../freebirth_0.3.2-8_i386.deb) ...
Selecting previously deselected package gtick.
Unpacking gtick (from .../gtick_0.3.15-1_i386.deb) ...
Selecting previously deselected package vkeybd.
Unpacking vkeybd (from .../vkeybd_1%3a0.1.17b-1_i386.deb) ...
Selecting previously deselected package zynaddsubfx.
Unpacking zynaddsubfx (from .../zynaddsubfx_2.2.1-4_i386.deb) ...
Selecting previously deselected package ubuntustudio-audio.
Unpacking ubuntustudio-audio (from .../ubuntustudio-audio_0.11_i386.deb) ...
Selecting previously deselected package libclthreads2.
Unpacking libclthreads2 (from .../libclthreads2_2.2.1-2_i386.deb) ...
Selecting previously deselected package libclxclient3.
Unpacking libclxclient3 (from .../libclxclient3_3.3.2-1_i386.deb) ...
Selecting previously deselected package stops.
Unpacking stops (from .../archives/stops_0.3.0-1_all.deb) ...
Selecting previously deselected package aeolus.
Unpacking aeolus (from .../aeolus_0.6.6+2-4_i386.deb) ...
Selecting previously deselected package vcf.
Unpacking vcf (from .../vcf_0.0.5-5ubuntu1_i386.deb) ...
Selecting previously deselected package xsynth-dssi.
Unpacking xsynth-dssi (from .../xsynth-dssi_0.9.0-2ubuntu1_i386.deb) ...
Selecting previously deselected package ubuntustudio-audio-plugins.
Unpacking ubuntustudio-audio-plugins (from .../ubuntustudio-audio-plugins_0.11_i386.deb) ...
Selecting previously deselected package ubuntustudio-theme.
Unpacking ubuntustudio-theme (from .../ubuntustudio-theme_0.14_all.deb) ...
Selecting previously deselected package ubuntustudio-wallpapers.
Unpacking ubuntustudio-wallpapers (from .../ubuntustudio-wallpapers_0.14_all.deb) ...
Selecting previously deselected package ubuntustudio-gdm-theme.
Unpacking ubuntustudio-gdm-theme (from .../ubuntustudio-gdm-theme_0.14_all.deb) ...
Selecting previously deselected package ubuntustudio-icon-theme.
Unpacking ubuntustudio-icon-theme (from .../ubuntustudio-icon-theme_0.4_all.deb) ...
Selecting previously deselected package ubuntustudio-sounds.
Unpacking ubuntustudio-sounds (from .../ubuntustudio-sounds_0.5_all.deb) ...
Selecting previously deselected package ubuntustudio-look.
Unpacking ubuntustudio-look (from .../ubuntustudio-look_0.14_all.deb) ...
Selecting previously deselected package ubuntustudio-default-settings.
Unpacking ubuntustudio-default-settings (from .../ubuntustudio-default-settings_0.5_all.deb) ...
Adding `diversion of /etc/sound/events/gnome-2.soundlist to /etc/sound/events/gnome-2.soundlist.orig by ubuntustudio-default-settings'
Adding `diversion of /etc/sound/events/gtk-events-2.soundlist to /etc/sound/events/gtk-events-2.soundlist.orig by ubuntustudio-default-settings'
Selecting previously deselected package ubuntustudio-menu.
Unpacking ubuntustudio-menu (from .../ubuntustudio-menu_0.5_all.deb) ...
Adding `diversion of /etc/xdg/menus/applications.menu to /etc/xdg/menus/applications.menu.orig by ubuntustudio-menu'
Selecting previously deselected package ubuntustudio-screensaver.
Unpacking ubuntustudio-screensaver (from .../ubuntustudio-screensaver_0.2_all.deb) ...
Selecting previously deselected package usplash-theme-ubuntustudio.
Unpacking usplash-theme-ubuntustudio (from .../usplash-theme-ubuntustudio_0.15_i386.deb) ...
Selecting previously deselected package ubuntustudio-desktop.
Unpacking ubuntustudio-desktop (from .../ubuntustudio-desktop_0.11_i386.deb) ...
Selecting previously deselected package libdv-bin.
Unpacking libdv-bin (from .../libdv-bin_1.0.0-1ubuntu1_i386.deb) ...
Selecting previously deselected package libsynfig0.
Unpacking libsynfig0 (from .../libsynfig0_0.61.06-2_i386.deb) ...
Selecting previously deselected package libsynfigapp0.
Unpacking libsynfigapp0 (from .../libsynfigapp0_0.61.06-1_i386.deb) ...
Selecting previously deselected package synfigstudio.
Unpacking synfigstudio (from .../synfigstudio_0.61.06-1_i386.deb) ...
Selecting previously deselected package wacom-tools.
Unpacking wacom-tools (from .../wacom-tools_1%3a0.7.7.7-0ubuntu2_i386.deb) ...
Selecting previously deselected package yafray.
Unpacking yafray (from .../yafray_0.0.9-2_i386.deb) ...
Selecting previously deselected package ubuntustudio-graphics.
Unpacking ubuntustudio-graphics (from .../ubuntustudio-graphics_0.11_i386.deb) ...
Selecting previously deselected package dvgrab.
Unpacking dvgrab (from .../archives/dvgrab_3.0-1_i386.deb) ...
Selecting previously deselected package kino.
Unpacking kino (from .../kino_1.1.0-3ubuntu2_i386.deb) ...
Selecting previously deselected package ubuntustudio-video.
Unpacking ubuntustudio-video (from .../ubuntustudio-video_0.11_i386.deb) ...
Setting up libbinio1c2 (1.4-6) ...

Setting up ladcca2 (0.4.0-6) ...

Setting up libjack0.100.0-0 (0.103.0-6ubuntu1) ...
Setting up libfluidsynth1 (1.0.7a-1) ...

Setting up libprojectm1-data (1.01-3~gutsy1) ...
Setting up libprojectm1 (1.01-3~gutsy1) ...

Setting up libresid-builder0c2a (2.1.1-5) ...

Setting up libsidplay2 (2.1.1-5) ...

Setting up audacious-plugins-extra (1.4.4-1ubuntu1~gutsy1) ...
Setting up texinfo (4.8.dfsg.1-6) ...
Running mktexlsr. This may take some time. ... done.

Setting up lilypond-data (2.10.25-0ubuntu1) ...
 Running /usr/bin/mktexlsr /usr/share/texmf...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Done.

 GNU LilyPond configuration completed.
 Please read /usr/share/doc/lilypond/README.Debian to get started.

Setting up linux-image-2.6.22-14-rt (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-rt
Running postinst hook script /sbin/update-grub.
Your /etc/kernel-img.conf needs to be updated. Read grub's NEWS.Debian[1]
file and follow its instructions.

 1. /usr/share/doc/grub/NEWS.Debian.gz


Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22-14-386
Found kernel: /boot/vmlinuz-2.6.22-14-rt
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/vmlinuz-2.6.20-16-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


Setting up linux-ubuntu-modules-2.6.22-14-rt (2.6.22-14.37) ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-rt

Setting up libfltk1.1 (1.1.7-4ubuntu1) ...

Setting up aconnectgui (0.9.0rc2-1-9) ...

Setting up libgconfmm-2.6-1c2 (2.20.0-0ubuntu1) ...

Setting up libglademm-2.4-1c2a (2.6.5-0ubuntu1) ...

Setting up agave (0.4.3-1) ...

Setting up liblo0 (0.23-2.1build1) ...

Setting up liblrdf0 (0.4.0-1build1) ...

Setting up python-twisted-bin (2.5.0-2build1) ...
Setting up python-zopeinterface (3.3.1-3build2) ...

Setting up python-twisted-core (2.5.0-2build1) ...

Setting up python-twisted-conch (1:0.8.0-1) ...

Setting up python-twisted-mail (0.4.0-1) ...

Setting up python-twisted-web (0.7.0-1) ...

Setting up python-twisted-lore (0.3.0-1) ...

Setting up python-twisted-names (0.4.0-1) ...

Setting up python-twisted-news (0.3.0-1) ...

Setting up python-twisted-runner (0.2.0-2) ...

Setting up python-twisted-words (0.5.0-1.1) ...

Setting up python-twisted (2.5.0-2build1) ...

Setting up ardour (1:2.1-1~gutsy1) ...

Setting up libgdiplus (1.2.4-2ubuntu1) ...
Setting up autopano-sift (2.4-0ubuntu6) ...
Setting up bitscope (1.1-6ubuntu2) ...

Setting up blender (2.45-1ubuntu2~gutsy1) ...

Setting up blop (0.2.8-5) ...
Setting up bristol (0.9.1-13) ...
Setting up caps (0.3.0-3) ...
Setting up libcinepaint0 (0.22-1-0ubuntu1) ...

Setting up cinepaint-data (0.22-1-0ubuntu1) ...
Setting up cinepaint (0.22-1-0ubuntu1) ...

Setting up cmt (1.15-3.1) ...

Setting up creox (0.2.2rc2-3ubuntu3) ...

Setting up csound (1:4.23f13-1.1) ...
Setting up denemo (0.7.5-4ubuntu3) ...

Setting up dssi-example-plugins (0.9.1-2build1) ...
Setting up dssi-host-jack (0.9.1-2build1) ...
Setting up dssi-utils (0.9.1-2build1) ...
Setting up ffmpeg2theora (0.19-1) ...
Setting up fftw3 (3.1.2-2ubuntu2) ...

Setting up fil-plugins (0.1.0-2) ...
Setting up fluidsynth (1.0.7a-1) ...

Setting up fluidsynth-dssi (0.9.1-3ubuntu1) ...
Setting up libuninameslist0 (0.0.20060907-2) ...

Setting up fontforge (0.0.20070607-3) ...

Setting up freepats (20060219-1) ...
Setting up libsigc++-1.2-5c2 (1.2.7-2) ...

Setting up freqtweak (0.7.0~cvs20070510-0ubuntu1) ...

Setting up libmpeg3-1 (1.5.4-5) ...

Setting up gimp-gap (2.2.2-1~gutsy1) ...
Setting up libexiv2-0 (0.15-1ubuntu2) ...

Setting up gimp-ufraw (0.11-2ubuntu3) ...
Setting up gnome-raw-thumbnailer (2.0.1-0ubuntu5) ...

Setting up gnome-specimen (0.2-0ubuntu1) ...

Setting up gtk2-engines-murrine (0.53.1-0ubuntu2) ...
Setting up guile-1.8-libs (1.8.1+1-5) ...

Setting up guile-1.8 (1.8.1+1-5) ...

Setting up hexter (0.6.1-2ubuntu1) ...

Setting up libboost-thread1.34.1 (1.34.1-2ubuntu1.1) ...

Setting up libpano12-0 (2.8.4-0build1) ...

Setting up hugin-data (0.7~beta4-0ubuntu3.1) ...
Setting up hugin-bin (0.7~beta4-0ubuntu3.1) ...

Setting up hugin-tools (0.7~beta4-0ubuntu3.1) ...
Setting up libpano12-bin (2.8.4-0build1) ...
Setting up libplot2c2 (2.5-2) ...

Setting up enblend (3.0.dfsg.1-0ubuntu3) ...
Setting up hugin (0.7~beta4-0ubuntu3.1) ...
Setting up hydrogen (0.9.3-4ubuntu2) ...

Setting up inkscape (0.45.1-1ubuntu5) ...

Setting up swh-plugins (0.4.15-0.1) ...

Setting up jack-rack (1.4.4-3ubuntu1) ...

Setting up jack-tools (0.0.2-4.1) ...
Setting up jackbeat (0.6.1-1ubuntu1) ...

Setting up jackeq (0.4.1-1ubuntu2) ...

Setting up jamin (0.95.0-4) ...

Setting up jdelay (1.0-0ubuntu1) ...
Setting up khelpcenter (4:3.5.8-0ubuntu2.2) ...

Setting up ladspa-sdk (1.1-6) ...

Setting up libclalsadrv1 (1.2.2-1ubuntu2) ...

Setting up libgig6 (3.1.1-0.1) ...

Setting up libgnomecanvasmm-2.6-1c2a (2.20.0-0ubuntu1) ...

Setting up libsigc++0c2 (1.0.4-9.1ubuntu2) ...
Setting up libgtkmm1.2-0c2a (1.2.10-8ubuntu2) ...

Setting up liblash2 (0.5.3-1) ...

Setting up liblscp (0.3.1-1) ...

Setting up libmxml1 (2.2-2) ...

Setting up libportaudio2 (19+svn20070125-1ubuntu2) ...

Setting up libqt4-core (4.3.2-0ubuntu3.2) ...

Setting up libqt4-gui (4.3.2-0ubuntu3.2) ...

Setting up libxml++2.6c2a (2.20.0-0ubuntu1) ...

Setting up lilypond (2.10.25-0ubuntu1) ...
Setting up linux-image-rt (2.6.22.14.21) ...
Setting up linux-restricted-modules-2.6.22-14-rt (2.6.22.4-14.10) ...

Setting up linux-restricted-modules-rt (2.6.22.14.21) ...
Setting up linux-rt (2.6.22.14.21) ...
Setting up mcp-plugins (0.3.0-4) ...
Setting up meterbridge (0.9.2-6ubuntu2) ...

Setting up mixxx-data (1.5.2svn~20070807dfsg-0ubuntu1) ...
Setting up mixxx (1.5.2svn~20070807dfsg-0ubuntu1) ...

Setting up mpg321 (0.2.10.3) ...

Setting up muse (0.8.1a-5) ...

Setting up nautilus-image-converter (0.0.9-0ubuntu1) ...
Setting up omins (0.2.0-5) ...
Setting up patchage (0.2.3-2.1) ...

Setting up pitivi (0.10.3-1) ...

Setting up puredata (0.40.2-2) ...

Setting up qamix (0.0.7e-0ubuntu2) ...

Setting up qjackctl (0.2.22-2ubuntu1) ...

Setting up qsampler (0.1.2-0ubuntu2) ...

Setting up qsynth (0.2.5-2ubuntu1) ...

Setting up rosegarden-data (1:1.5.1-3ubuntu1) ...
Setting up sndfile-programs (1.0.17-4) ...
Setting up rosegarden (1:1.5.1-3ubuntu1) ...

Setting up rosegarden4 (1:1.5.1-3ubuntu1) ...
Setting up scribus (1.3.3.11.dfsg-1ubuntu3~gutsy1) ...

Setting up seq24 (0.8.7-1ubuntu1) ...

Setting up shaketracker (0.4.6-5build1) ...

Setting up sooperlooper (1.0.8c-2ubuntu2) ...

Setting up stopmotion (0.6.0-1) ...

Setting up swami (0.9.4-1) ...
Setting up tap-plugins (0.7.0-2) ...

Setting up tapiir (0.7.1-9) ...

Setting up terminatorx (3.82-7ubuntu2) ...

Setting up timemachine (0.3.0-3ubuntu1) ...

Setting up timidity (2.13.2-15ubuntu1) ...
 * Starting timidity                                                                                                                             
 * Starting TiMidity++ ALSA midi emulation...                                                                                                   
 ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix.device'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
                                                                                                                                          [fail]
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
Setting up tk707 (0.7.21-9) ...

Setting up alsa-tools (1.0.14-1ubuntu2) ...
Setting up alsa-tools-gui (1.0.14-1ubuntu2) ...

Setting up beast (0.6.6-9) ...

Setting up freebirth-data (0.3.2-8) ...
Setting up freebirth (0.3.2-8) ...

Setting up gtick (0.3.15-1) ...

Setting up vkeybd (1:0.1.17b-1) ...

Setting up zynaddsubfx (2.2.1-4) ...

dpkg: dependency problems prevent configuration of ubuntustudio-audio:
 ubuntustudio-audio depends on timidity; however:
  Package timidity is not configured yet.
dpkg: error processing ubuntustudio-audio (--configure):
 dependency problems - leaving unconfigured
Setting up libclthreads2 (2.2.1-2) ...

Setting up libclxclient3 (3.3.2-1) ...

Setting up stops (0.3.0-1) ...
Setting up aeolus (0.6.6+2-4) ...

Setting up vcf (0.0.5-5ubuntu1) ...
Setting up xsynth-dssi (0.9.0-2ubuntu1) ...
Setting up ubuntustudio-audio-plugins (0.11) ...
Setting up ubuntustudio-theme (0.14) ...
Setting up ubuntustudio-wallpapers (0.14) ...
Setting up ubuntustudio-gdm-theme (0.14) ...

Setting up ubuntustudio-icon-theme (0.4) ...

Setting up ubuntustudio-sounds (0.5) ...
Setting up ubuntustudio-look (0.14) ...

Setting up ubuntustudio-default-settings (0.5) ...

Setting up ubuntustudio-menu (0.5) ...

Setting up ubuntustudio-screensaver (0.2) ...
Setting up usplash-theme-ubuntustudio (0.15) ...
update-initramfs: deferring update (trigger activated)

Setting up ubuntustudio-desktop (0.11) ...
Setting up libdv-bin (1.0.0-1ubuntu1) ...
Setting up libsynfig0 (0.61.06-2) ...

Setting up libsynfigapp0 (0.61.06-1) ...

Setting up synfigstudio (0.61.06-1) ...

Setting up wacom-tools (1:0.7.7.7-0ubuntu2) ...

Setting up yafray (0.0.9-2) ...
Setting up ubuntustudio-graphics (0.11) ...
Setting up dvgrab (3.0-1) ...
Setting up kino (1.1.0-3ubuntu2) ...

Setting up ubuntustudio-video (0.11) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-rt
Errors were encountered while processing:
 timidity
 ubuntustudio-audio
E: Sub-process /usr/bin/dpkg returned an error code (1)
david@lancer:~$ su
Password: 
root@lancer:/media/data/home/david# apt-get update && apt-get dist-upgrade && apt-get dist-upgrade
Get:1 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_US                                                                          
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_US                                                                        
Get:2 http://archive.ubuntu.com gutsy-security Release.gpg [191B]                                                                               
Ign http://archive.ubuntu.com gutsy-security/main Translation-en_US                                                                             
Ign http://archive.ubuntu.com gutsy-security/restricted Translation-en_US                                                                       
Ign http://archive.ubuntu.com gutsy-security/universe Translation-en_US                                                                         
Ign http://archive.ubuntu.com gutsy-security/multiverse Translation-en_US                                                                       
Hit http://archive.ubuntu.com gutsy-updates Release                                                                                             
Get:3 http://security.ubuntu.com gutsy-security Release.gpg [191B]                                                                              
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US                                                                            
Get:4 http://us.archive.ubuntu.com gutsy Release.gpg [191B]                                                                                     
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US                                                                                   
Hit http://archive.ubuntu.com gutsy-security Release                                                                                            
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US                                                                      
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US                                                                        
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US                                                                      
Hit http://security.ubuntu.com gutsy-security Release                                                                                           
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US                                                               
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US                                           
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US                                         
Get:5 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]                                                               
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US                                                             
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US                                                       
Hit http://archive.ubuntu.com gutsy-updates/universe Packages                                                                     
Hit http://archive.ubuntu.com gutsy-updates/multiverse Packages                                                                   
Get:6 http://archive.canonical.com gutsy Release.gpg [191B]                                                                       
Ign http://archive.canonical.com gutsy/partner Translation-en_US                                            
Hit http://security.ubuntu.com gutsy-security/main Packages                                                 
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US                                   
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US                                 
Get:7 http://us.archive.ubuntu.com gutsy-backports Release.gpg [191B]                                       
Ign http://us.archive.ubuntu.com gutsy-backports/main Translation-en_US                                     
Hit http://archive.ubuntu.com gutsy-security/main Packages                                                                        
Hit http://archive.ubuntu.com gutsy-security/restricted Packages                                                                  
Hit http://archive.ubuntu.com gutsy-security/universe Packages                                                                    
Get:8 http://archive.canonical.com gutsy Release [6998B]                                                                          
Ign http://us.archive.ubuntu.com gutsy-backports/restricted Translation-en_US                                                          
Ign http://us.archive.ubuntu.com gutsy-backports/universe Translation-en_US                                                                     
Hit http://security.ubuntu.com gutsy-security/restricted Packages                                                                               
Hit http://security.ubuntu.com gutsy-security/main Sources                                                                                      
Hit http://security.ubuntu.com gutsy-security/restricted Sources                                                                                
Ign http://us.archive.ubuntu.com gutsy-backports/multiverse Translation-en_US                                                                   
Hit http://us.archive.ubuntu.com gutsy Release                                                                                                  
Hit http://us.archive.ubuntu.com gutsy-updates Release                                                                                          
Hit http://archive.ubuntu.com gutsy-security/multiverse Packages                                                                                
Hit http://us.archive.ubuntu.com gutsy-backports Release                                                                                        
Hit http://security.ubuntu.com gutsy-security/universe Packages                                                                 
Hit http://security.ubuntu.com gutsy-security/universe Sources                                  
Hit http://security.ubuntu.com gutsy-security/multiverse Packages                               
Hit http://security.ubuntu.com gutsy-security/multiverse Sources                                
Get:9 http://packages.medibuntu.org feisty Release.gpg [189B]                                   
Ign http://packages.medibuntu.org feisty/free Translation-en_US           
Hit http://us.archive.ubuntu.com gutsy/main Packages                      
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Ign http://packages.medibuntu.org feisty/non-free Translation-en_US
Hit http://packages.medibuntu.org feisty Release
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources        
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources    
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages     
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources      
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages   
Hit http://archive.canonical.com gutsy/partner Packages              
Ign http://packages.medibuntu.org feisty/free Packages               
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-backports/main Packages       
Hit http://us.archive.ubuntu.com gutsy-backports/restricted Packages 
Hit http://us.archive.ubuntu.com gutsy-backports/universe Packages   
Hit http://us.archive.ubuntu.com gutsy-backports/multiverse Packages 
Get:10 http://archive.canonical.com gutsy/partner Sources [1341B]    
Ign http://packages.medibuntu.org feisty/non-free Packages           
Ign http://packages.medibuntu.org feisty/free Sources
Ign http://packages.medibuntu.org feisty/non-free Sources
Hit http://us.archive.ubuntu.com gutsy-backports/main Sources       
Hit http://us.archive.ubuntu.com gutsy-backports/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-backports/universe Sources
Hit http://us.archive.ubuntu.com gutsy-backports/multiverse Sources
Hit http://packages.medibuntu.org feisty/free Packages
Hit http://packages.medibuntu.org feisty/non-free Packages
Hit http://packages.medibuntu.org feisty/free Sources
Hit http://packages.medibuntu.org feisty/non-free Sources
Fetched 8537B in 2s (3891B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up timidity (2.13.2-15ubuntu1) ...
 * Starting timidity                                                                                                                             
 * Starting TiMidity++ ALSA midi emulation...                                                                                             [ OK ] 

Setting up ubuntustudio-audio (0.11) ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@lancer:/media/data/home/david# 

```

---

### Post by Raptor Ramjet on 2008-04-05
Thanks for that.  However I had to perform a slight variation of your actions as "su" didn't work for me (If I remember correctly I thought  you have to actually set a root password to be able to use su ?).

Anyway to switch to root I did:

> 
sudo -i


I then tried getting my installation up to date by using:

> 
apt-get update && apt-get dist-upgrade && apt-get dist-upgrade


However this again failed but it gave me the brainwave of manually removing the timidity package which I did by using:

> 
sudo apt-get remove timidity


When I ran this I was quite happy to see that it also removed the ubuntustudio-audio package so as soon as it was finished I decided to try installing the ubuntustudio-audio package first.

> 
apt-get install ubuntustudio-audio


This had the desired effect of also installing timidity so now everything seems to work fine (only time will tell...)

For further detail the relevant parts of my session were:

> 
.... start of code not shown...
Errors were encountered while processing:
 timidity
 timidity-interfaces-extra
 ubuntustudio-audio
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@olga:~# sudo apt-get remove timidity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  timidity timidity-interfaces-extra ubuntustudio-audio
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
3 not fully installed or removed.
^[[ANeed to get 0B of archives.
After unpacking 2089kB disk space will be freed.
Do you want to continue [Y/n]? y
Abort.
root@oldknacker:~# sudo apt-get remove timidity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  timidity timidity-interfaces-extra ubuntustudio-audio
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 2089kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 133010 files and directories currently installed.)
Removing ubuntustudio-audio ...
Removing timidity-interfaces-extra ...
Removing timidity ...
 * Stopping TiMidity++ ALSA midi emulation...                            [ OK ] 
root@oldknacker:~# sudo apt-get install ubuntustudio-audio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  timidity
Suggested packages:
  pmidi
The following NEW packages will be installed
  timidity ubuntustudio-audio
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/559kB of archives.
After unpacking 1782kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously deselected package timidity.
(Reading database ... 132948 files and directories currently installed.)
Unpacking timidity (from .../timidity_2.13.2-15ubuntu1_i386.deb) ...
Selecting previously deselected package ubuntustudio-audio.
Unpacking ubuntustudio-audio (from .../ubuntustudio-audio_0.11_i386.deb) ...
Setting up timidity (2.13.2-15ubuntu1) ...
 * Starting timidity                                                             * Starting TiMidity++ ALSA midi emulation...                            [ OK ] 

Setting up ubuntustudio-audio (0.11) ...
root@oldknacker:~# 


Once again cheers for pointing me in the right direction and I hope this is of use to someone else.

---

### Post by davidshere on 2008-04-05
yes, upon installation you can't log into the root account... this is because the root account has no password.  I've always disabled that right away in all my ubuntu installations.  There are a number of different ways, this was my way:

```
david@lancer:~$ sudo sulogin
[sudo] password for david:[current user password]
root@lancer:~# passwd
Enter new UNIX password: [password you want for root]
Retype new UNIX password: [password you want for root]
passwd: password updated successfully
root@lancer:~# exit
david@lancer:~$ su
Password: [password you want for root]
root@lancer:/media/data/home/david# 
```

I'm sure this procedure is documented elsewhere.

As for the ubuntu studio problem, we may not have had the same problem, but I'm glad my idea helped you.  I've pretty much done nothing with ubuntu studio since then, so I actually really can't tell you if what I did actually worked; only that the installation went through with no errors. 

I was hoping that installing Ubuntu studio would help me find some good free video editing software, specifically that would help me convert and edit my Quicktime MOVs from my Nikon digital camera into Mpegs or Avis. Either I didn't look hard enough or it's not there.  But that's another thread.

---

