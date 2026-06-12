---
title: "Mic Problems Thinkpad Edge E530"
date: 2013-02-07
forum: Multimedia Software
---

### Post by Smilo on 2013-02-07
My mic was working great until I decided to uninstsalled pulseaudio volume control because it wasnt working properly. However when I reinstalled it my mic was very quite. I am an avid Skype user so I need my mic to work properly on a daily basis. I have checked the input settings and have even put them above 100% but it is still barely audible.

OS: Ubuntu 12.04 LTS
Computer: Lenovo Thinkpad Edge E530
sound card: HDA Intel PCH

What should I do to fix it! :confused:
(if there is any infomation that i have missed out, and will aid in the fixing proccess, please tell me.)

Thanks in advance

---

### Post by xc3RnbFO8P on 2013-02-07
From [https://help.ubuntu.com/community/SoundTroubleshootingProcedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
Copy and paste into terminal:
> sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`

---

### Post by Smilo on 2013-02-07
> **Ringi said:**
> From [https://help.ubuntu.com/community/SoundTroubleshootingProcedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
Copy and paste into terminal:
Could you explain what this does? (i am only a kid and have had a bad experience with entering code from forums into terminal before)

Thanks

---

### Post by xc3RnbFO8P on 2013-02-07
> **Smilo said:**
> Could you explain what this does? (i am only a kid and have had a bad experience with entering code from forums into terminal before)

Thanks

Then dont!

I tested it on my computer to see if there was some problems,
there were none, sound works.
this is from terminal:
```
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://dk.archive.ubuntu.com lucid-backports/multiverse i386 Packages      
Ign http://dk.archive.ubuntu.com lucid-backports/main TranslationIndex         
Ign http://dk.archive.ubuntu.com lucid-backports/multiverse TranslationIndex   
Ign http://dk.archive.ubuntu.com lucid-backports/restricted TranslationIndex   
Ign http://dk.archive.ubuntu.com lucid-backports/universe TranslationIndex     
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://ppa.launchpad.net precise Release                                   
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Get:6 http://ftp.uni-kl.de precise-updates Release [49.6 kB]                   
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://ppa.launchpad.net gutsy Release                                     
Ign http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Ign http://dl.google.com stable/main TranslationIndex                          
Get:7 http://ppa.launchpad.net precise Release [11.9 kB]                       
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://ppa.launchpad.net gutsy/main TranslationIndex                       
Ign http://dk.archive.ubuntu.com lucid-backports/main Translation-en_US        
Ign http://dk.archive.ubuntu.com lucid-backports/main Translation-en           
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://dk.archive.ubuntu.com lucid-backports/multiverse Translation-en_US  
Ign http://dk.archive.ubuntu.com lucid-backports/multiverse Translation-en     
Ign http://dk.archive.ubuntu.com lucid-backports/restricted Translation-en_US  
Ign http://dk.archive.ubuntu.com lucid-backports/restricted Translation-en     
Ign http://dk.archive.ubuntu.com lucid-backports/universe Translation-en_US    
Ign http://dk.archive.ubuntu.com lucid-backports/universe Translation-en       
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Get:8 http://ftp.uni-kl.de precise-security Release [49.6 kB]                  
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:9 http://ppa.launchpad.net precise/main Sources [2,633 B]                  
Get:10 http://ppa.launchpad.net precise/main amd64 Packages [6,373 B]          
Get:11 http://ppa.launchpad.net precise/main i386 Packages [6,523 B]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:12 http://ftp.uni-kl.de precise-backports Release [49.6 kB]                
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://ftp.uni-kl.de precise/main Sources                                  
Hit http://ftp.uni-kl.de precise/restricted Sources                            
Hit http://ftp.uni-kl.de precise/universe Sources                              
Hit http://ftp.uni-kl.de precise/multiverse Sources                            
Hit http://ftp.uni-kl.de precise/main amd64 Packages                           
Hit http://ftp.uni-kl.de precise/restricted amd64 Packages                     
Hit http://ftp.uni-kl.de precise/universe amd64 Packages                       
Hit http://ftp.uni-kl.de precise/multiverse amd64 Packages                     
Hit http://ftp.uni-kl.de precise/main i386 Packages                            
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://dl.google.com stable/main Translation-en                            
Hit http://ftp.uni-kl.de precise/restricted i386 Packages             
Hit http://ftp.uni-kl.de precise/universe i386 Packages
Hit http://ftp.uni-kl.de precise/multiverse i386 Packages
Hit http://ftp.uni-kl.de precise/main TranslationIndex
Hit http://ftp.uni-kl.de precise/multiverse TranslationIndex
Hit http://ftp.uni-kl.de precise/restricted TranslationIndex
Hit http://ftp.uni-kl.de precise/universe TranslationIndex
Get:13 http://ftp.uni-kl.de precise-updates/main Sources [366 kB]
Err http://ppa.launchpad.net gutsy/main amd64 Packages  
  404  Not Found
Err http://ppa.launchpad.net gutsy/main i386 Packages   
  404  Not Found
Err http://ppa.launchpad.net precise/main Sources
  404  Not Found
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net gutsy/main Translation-en_US
Ign http://ppa.launchpad.net gutsy/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Get:14 http://ftp.uni-kl.de precise-updates/restricted Sources [5,135 B]
Get:15 http://ftp.uni-kl.de precise-updates/universe Sources [78.2 kB]
Get:16 http://ftp.uni-kl.de precise-updates/multiverse Sources [4,737 B]
Get:17 http://ftp.uni-kl.de precise-updates/main amd64 Packages [574 kB]
Get:18 http://ftp.uni-kl.de precise-updates/restricted amd64 Packages [9,565 B]
Get:19 http://ftp.uni-kl.de precise-updates/universe amd64 Packages [179 kB]
Get:20 http://ftp.uni-kl.de precise-updates/multiverse amd64 Packages [9,425 B]
Get:21 http://ftp.uni-kl.de precise-updates/main i386 Packages [583 kB]
Get:22 http://ftp.uni-kl.de precise-updates/restricted i386 Packages [9,503 B]
Get:23 http://ftp.uni-kl.de precise-updates/universe i386 Packages [181 kB]
Get:24 http://ftp.uni-kl.de precise-updates/multiverse i386 Packages [10.4 kB]
Get:25 http://ftp.uni-kl.de precise-updates/main TranslationIndex [3,564 B]
Get:26 http://ftp.uni-kl.de precise-updates/multiverse TranslationIndex [2,605 B]
Get:27 http://ftp.uni-kl.de precise-updates/restricted TranslationIndex [2,461 B]
Get:28 http://ftp.uni-kl.de precise-updates/universe TranslationIndex [2,850 B]
Get:29 http://ftp.uni-kl.de precise-security/main Sources [63.1 kB]    
Get:30 http://ftp.uni-kl.de precise-security/restricted Sources [1,950 B]
Get:31 http://ftp.uni-kl.de precise-security/universe Sources [20.6 kB]
Get:32 http://ftp.uni-kl.de precise-security/multiverse Sources [1,379 B]
Get:33 http://ftp.uni-kl.de precise-security/main amd64 Packages [225 kB]
Get:34 http://ftp.uni-kl.de precise-security/restricted amd64 Packages [3,969 B]
Get:35 http://ftp.uni-kl.de precise-security/universe amd64 Packages [65.4 kB]
Get:36 http://ftp.uni-kl.de precise-security/multiverse amd64 Packages [2,184 B]
Get:37 http://ftp.uni-kl.de precise-security/main i386 Packages [233 kB]
Get:38 http://ftp.uni-kl.de precise-security/restricted i386 Packages [3,968 B]
Get:39 http://ftp.uni-kl.de precise-security/universe i386 Packages [66.9 kB]
Get:40 http://ftp.uni-kl.de precise-security/multiverse i386 Packages [2,366 B]
Get:41 http://ftp.uni-kl.de precise-security/main TranslationIndex [74 B]
Get:42 http://ftp.uni-kl.de precise-security/multiverse TranslationIndex [71 B]
Get:43 http://ftp.uni-kl.de precise-security/restricted TranslationIndex [71 B]
Get:44 http://ftp.uni-kl.de precise-security/universe TranslationIndex [73 B]
Get:45 http://ftp.uni-kl.de precise-backports/main Sources [2,422 B]
Get:46 http://ftp.uni-kl.de precise-backports/universe Sources [21.8 kB]
Get:47 http://ftp.uni-kl.de precise-backports/multiverse Sources [2,669 B]
Get:48 http://ftp.uni-kl.de precise-backports/restricted Sources [14 B]
Get:49 http://ftp.uni-kl.de precise-backports/main amd64 Packages [1,945 B]
Get:50 http://ftp.uni-kl.de precise-backports/multiverse amd64 Packages [2,489 B]
Get:51 http://ftp.uni-kl.de precise-backports/universe amd64 Packages [22.3 kB]
Get:52 http://ftp.uni-kl.de precise-backports/restricted amd64 Packages [14 B]
Get:53 http://ftp.uni-kl.de precise-backports/main i386 Packages [1,941 B]
Get:54 http://ftp.uni-kl.de precise-backports/multiverse i386 Packages [2,504 B]
Get:55 http://ftp.uni-kl.de precise-backports/universe i386 Packages [22.4 kB]
Get:56 http://ftp.uni-kl.de precise-backports/restricted i386 Packages [14 B]
Hit http://ftp.uni-kl.de precise-backports/main TranslationIndex
Hit http://ftp.uni-kl.de precise-backports/multiverse TranslationIndex
Hit http://ftp.uni-kl.de precise-backports/restricted TranslationIndex
Hit http://ftp.uni-kl.de precise-backports/universe TranslationIndex
Hit http://ftp.uni-kl.de precise/main Translation-en
Hit http://ftp.uni-kl.de precise/multiverse Translation-en
Hit http://ftp.uni-kl.de precise/restricted Translation-en
Hit http://ftp.uni-kl.de precise/universe Translation-en
Hit http://ftp.uni-kl.de precise-updates/main Translation-en
Hit http://ftp.uni-kl.de precise-updates/multiverse Translation-en
Hit http://ftp.uni-kl.de precise-updates/restricted Translation-en
Get:57 http://ftp.uni-kl.de precise-updates/universe Translation-en [107 kB]
Hit http://ftp.uni-kl.de precise-security/main Translation-en
Hit http://ftp.uni-kl.de precise-security/multiverse Translation-en
Hit http://ftp.uni-kl.de precise-security/restricted Translation-en
Get:58 http://ftp.uni-kl.de precise-security/universe Translation-en [40.4 kB]
Hit http://ftp.uni-kl.de precise-backports/main Translation-en          
Hit http://ftp.uni-kl.de precise-backports/multiverse Translation-en
Hit http://ftp.uni-kl.de precise-backports/restricted Translation-en
Hit http://ftp.uni-kl.de precise-backports/universe Translation-en
Fetched 3,116 kB in 5s (613 kB/s) 
W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/gutsy/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/gutsy/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/precise/main/source/Sources  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  gnome-settings-daemon libpulse-mainloop-glib0 libpulse-mainloop-glib0:i386
  libpulse0 libpulse0:i386 libpulsedsp libpulsedsp:i386 libunity-core-5.0-5
  pulseaudio pulseaudio-module-bluetooth pulseaudio-module-gconf
  pulseaudio-module-x11 pulseaudio-utils unity unity-common unity-greeter
  unity-services
17 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,964 kB of archives.
After this operation, 1,461 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ftp.uni-kl.de/pub/linux/ubuntu/ precise-updates/main gnome-settings-daemon amd64 3.4.2-0ubuntu0.6.2 [482 kB]
Get:2 http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/ precise/main libpulse0 amd64 1:2.0-0ubuntu1~precise2 [330 kB]
Get:3 http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/ precise/main libpulse0 i386 1:2.0-0ubuntu1~precise2 [319 kB]
Get:4 http://ftp.uni-kl.de/pub/linux/ubuntu/ precise-updates/main unity-greeter amd64 0.2.9-0ubuntu1 [87.1 kB]
Get:5 http://ftp.uni-kl.de/pub/linux/ubuntu/ precise-updates/main unity amd64 5.18.0-0ubuntu2 [1,286 kB]
Get:6 http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/ precise/main libpulse-mainloop-glib0 i386 1:2.0-0ubuntu1~precise2 [59.8 kB]
Get:7 http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/ precise/main libpulse-mainloop-glib0 amd64 1:2.0-0ubuntu1~precise2 [59.8 kB]
Get:8 http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/ precise/main libpulsedsp i386 1:2.0-0ubuntu1~precise2 [70.9 kB]
Get:9 http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/ precise/main libpulsedsp amd64 1:2.0-0ubuntu1~precise2 [70.9 kB]
Get:10 http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/ precise/main pulseaudio-utils amd64 1:2.0-0ubuntu1~precise2 [109 kB]
Get:11 http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/ precise/main pulseaudio amd64 1:2.0-0ubuntu1~precise2 [1,417 kB]
Get:12 http://ftp.uni-kl.de/pub/linux/ubuntu/ precise-updates/main unity-common all 5.18.0-0ubuntu2 [146 kB]
Get:13 http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/ precise/main pulseaudio-module-gconf amd64 1:2.0-0ubuntu1~precise2 [60.5 kB]
Get:14 http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/ precise/main pulseaudio-module-x11 amd64 1:2.0-0ubuntu1~precise2 [65.5 kB]Could you explain what this does? (i am only a kid and have had a bad experience with entering code from forums into terminal before)
Get:15 http://ftp.uni-kl.de/pub/linux/ubuntu/ precise-updates/main libunity-core-5.0-5 amd64 5.18.0-0ubuntu2 [235 kB]
Get:16 http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/ precise/main pulseaudio-module-bluetooth amd64 1:2.0-0ubuntu1~precise2 [131 kB]
Get:17 http://ftp.uni-kl.de/pub/linux/ubuntu/ precise-updates/main unity-services amd64 5.18.0-0ubuntu2 [35.0 kB]
Fetched 4,964 kB in 4s (1,005 kB/s)   
(Reading database ... 312441 files and directories currently installed.)
Preparing to replace libpulse0 1:1.1-0ubuntu15.2 (using .../libpulse0_1%3a2.0-0ubuntu1~precise2_amd64.deb) ...
De-configuring libpulse0:i386 ...
Unpacking replacement libpulse0 ...
Preparing to replace libpulse0:i386 1:1.1-0ubuntu15.2 (using .../libpulse0_1%3a2.0-0ubuntu1~precise2_i386.deb) ...
Unpacking replacement libpulse0:i386 ...
Setting up libpulse0 (1:2.0-0ubuntu1~precise2) ...
Setting up libpulse0:i386 (1:2.0-0ubuntu1~precise2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 312444 files and directories currently installed.)
Preparing to replace libpulse-mainloop-glib0:i386 1:1.1-0ubuntu15.2 (using .../libpulse-mainloop-glib0_1%3a2.0-0ubuntu1~precise2_i386.deb) ...
De-configuring libpulse-mainloop-glib0 ...
Unpacking replacement libpulse-mainloop-glib0:i386 ...
Preparing to replace libpulse-mainloop-glib0 1:1.1-0ubuntu15.2 (using .../libpulse-mainloop-glib0_1%3a2.0-0ubuntu1~precise2_amd64.deb) ...
Unpacking replacement libpulse-mainloop-glib0 ...
Setting up libpulse-mainloop-glib0:i386 (1:2.0-0ubuntu1~precise2) ...
Setting up libpulse-mainloop-glib0 (1:2.0-0ubuntu1~precise2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 312445 files and directories currently installed.)
Preparing to replace libpulsedsp:i386 1:1.1-0ubuntu15.2 (using .../libpulsedsp_1%3a2.0-0ubuntu1~precise2_i386.deb) ...
De-configuring libpulsedsp ...
Unpacking replacement libpulsedsp:i386 ...
Preparing to replace libpulsedsp 1:1.1-0ubuntu15.2 (using .../libpulsedsp_1%3a2.0-0ubuntu1~precise2_amd64.deb) ...
Unpacking replacement libpulsedsp ...
Setting up libpulsedsp:i386 (1:2.0-0ubuntu1~precise2) ...
Setting up libpulsedsp (1:2.0-0ubuntu1~precise2) ...
(Reading database ... 312446 files and directories currently installed.)
Preparing to replace gnome-settings-daemon 3.4.2-0ubuntu0.6.1 (using .../gnome-settings-daemon_3.4.2-0ubuntu0.6.2_amd64.deb) ...
Unpacking replacement gnome-settings-daemon ...
Preparing to replace unity-greeter 0.2.8-0ubuntu1.4 (using .../unity-greeter_0.2.9-0ubuntu1_amd64.deb) ...
Unpacking replacement unity-greeter ...
Preparing to replace unity 5.18.0-0ubuntu1 (using .../unity_5.18.0-0ubuntu2_amd64.deb) ...
Unpacking replacement unity ...
Preparing to replace unity-common 5.18.0-0ubuntu1 (using .../unity-common_5.18.0-0ubuntu2_all.deb) ...
Unpacking replacement unity-common ...
Preparing to replace libunity-core-5.0-5 5.18.0-0ubuntu1 (using .../libunity-core-5.0-5_5.18.0-0ubuntu2_amd64.deb) ...
Unpacking replacement libunity-core-5.0-5 ...
Preparing to replace unity-services 5.18.0-0ubuntu1 (using .../unity-services_5.18.0-0ubuntu2_amd64.deb) ...
Unpacking replacement unity-services ...
Preparing to replace pulseaudio-utils 1:1.1-0ubuntu15.2 (using .../pulseaudio-utils_1%3a2.0-0ubuntu1~precise2_amd64.deb) ...
Unpacking replacement pulseaudio-utils ...
Preparing to replace pulseaudio 1:1.1-0ubuntu15.2 (using .../pulseaudio_1%3a2.0-0ubuntu1~precise2_amd64.deb) ...
Unpacking replacement pulseaudio ...
Preparing to replace pulseaudio-module-gconf 1:1.1-0ubuntu15.2 (using .../pulseaudio-module-gconf_1%3a2.0-0ubuntu1~precise2_amd64.deb) ...
Unpacking replacement pulseaudio-module-gconf ...
Preparing to replace pulseaudio-module-x11 1:1.1-0ubuntu15.2 (using .../pulseaudio-module-x11_1%3a2.0-0ubuntu1~precise2_amd64.deb) ...
Unpacking replacement pulseaudio-module-x11 ...
Preparing to replace pulseaudio-module-bluetooth 1:1.1-0ubuntu15.2 (using .../pulseaudio-module-bluetooth_1%3a2.0-0ubuntu1~precise2_amd64.deb) ...
Unpacking replacement pulseaudio-module-bluetooth ...
Processing triggers for gconf2 ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0 ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up gnome-settings-daemon (3.4.2-0ubuntu0.6.2) ...
Setting up unity-greeter (0.2.9-0ubuntu1) ...
Setting up unity-services (5.18.0-0ubuntu2) ...
Setting up libunity-core-5.0-5 (5.18.0-0ubuntu2) ...
Setting up unity-common (5.18.0-0ubuntu2) ...
Setting up unity (5.18.0-0ubuntu2) ...
Setting up pulseaudio-utils (1:2.0-0ubuntu1~precise2) ...
Setting up pulseaudio (1:2.0-0ubuntu1~precise2) ...
Installing new version of config file /etc/xdg/autostart/pulseaudio-kde.desktop ...
Installing new version of config file /etc/pulse/daemon.conf ...
Installing new version of config file /etc/pulse/default.pa ...
pulseaudio stop/pre-start, process 4856
Setting up pulseaudio-module-gconf (1:2.0-0ubuntu1~precise2) ...
Setting up pulseaudio-module-x11 (1:2.0-0ubuntu1~precise2) ...
Setting up pulseaudio-module-bluetooth (1:2.0-0ubuntu1~precise2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
W: Duplicate sources.list entry http://ftp.uni-kl.de/pub/linux/ubuntu/ precise/multiverse amd64 Packages (/var/lib/apt/lists/ftp.uni-kl.de_pub_linux_ubuntu_dists_precise_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry http://ftp.uni-kl.de/pub/linux/ubuntu/ precise/multiverse i386 Packages (/var/lib/apt/lists/ftp.uni-kl.de_pub_linux_ubuntu_dists_precise_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://ftp.uni-kl.de/pub/linux/ubuntu/ precise-backports/universe amd64 Packages (/var/lib/apt/lists/ftp.uni-kl.de_pub_linux_ubuntu_dists_precise-backports_universe_binary-amd64_Packages)
W: Duplicate sources.list entry http://ftp.uni-kl.de/pub/linux/ubuntu/ precise-backports/universe i386 Packages (/var/lib/apt/lists/ftp.uni-kl.de_pub_linux_ubuntu_dists_precise-backports_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-base is already the newest version.
alsa-utils is already the newest version.
linux-sound-base is already the newest version.
libasound2 is already the newest version.
linux-image-3.2.0-37-generic is already the newest version.
ubuntu-desktop is already the newest version.
Suggested packages:
  uswsusp gnome-mag gok
The following NEW packages will be installed:
  gdm pavucontrol
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,878 kB of archives.
After this operation, 8,017 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ftp.uni-kl.de/pub/linux/ubuntu/ precise/universe gdm amd64 3.0.4-0ubuntu15 [1,733 kB]
Get:2 http://ftp.uni-kl.de/pub/linux/ubuntu/ precise/universe pavucontrol amd64 0.99.2-1build1 [145 kB]
Fetched 1,878 kB in 4s (409 kB/s)
Preconfiguring packages ...
Selecting previously unselected package gdm.
(Reading database ... 312492 files and directories currently installed.)
Unpacking gdm (from .../gdm_3.0.4-0ubuntu15_amd64.deb) ...
Selecting previously unselected package pavucontrol.
Unpacking pavucontrol (from .../pavucontrol_0.99.2-1build1_amd64.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gconf2 ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up gdm (3.0.4-0ubuntu15) ...
Adding group `gdm' (GID 126) ...
Done.
Warning: The home dir /var/lib/gdm you specified already exists.
Adding system user `gdm' (UID 115) ...
Adding new user `gdm' (UID 115) with group `gdm' ...
The home directory `/var/lib/gdm' already exists.  Not copying from `/etc/skel'.
adduser: Warning: The home directory `/var/lib/gdm' does not belong to the user you are currently creating.
usermod: no changes
usermod: no changes
usermod: no changes
Setting up pavucontrol (0.99.2-1build1) ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 8 reinstalled, 0 to remove and 0 not upgraded.
Need to get 2,134 kB/42.4 MB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://ftp.uni-kl.de/pub/linux/ubuntu/ precise/main alsa-utils amd64 1.0.25-1ubuntu5 [1,118 kB]
Get:2 http://ftp.uni-kl.de/pub/linux/ubuntu/ precise-updates/main libasound2 amd64 1.0.25-1ubuntu10.1 [428 kB]
Get:3 http://ftp.uni-kl.de/pub/linux/ubuntu/ precise-updates/main libasound2 i386 1.0.25-1ubuntu10.1 [430 kB]
Get:4 http://ftp.uni-kl.de/pub/linux/ubuntu/ precise/main alsa-base all 1.0.25+dfsg-0ubuntu1 [143 kB]
Get:5 http://ftp.uni-kl.de/pub/linux/ubuntu/ precise/main linux-sound-base all 1.0.25+dfsg-0ubuntu1 [15.0 kB]
Fetched 2,134 kB in 4s (455 kB/s)      
Preconfiguring packages ...
(Reading database ... 312773 files and directories currently installed.)
Preparing to replace alsa-utils 1.0.25-1ubuntu5 (using .../alsa-utils_1.0.25-1ubuntu5_amd64.deb) ...
Unpacking replacement alsa-utils ...
Preparing to replace gdm 3.0.4-0ubuntu15 (using .../gdm_3.0.4-0ubuntu15_amd64.deb) ...Could you explain what this does? (i am only a kid and have had a bad experience with entering code from forums into terminal before)
Unpacking replacement gdm ...
Preparing to replace libasound2 1.0.25-1ubuntu10.1 (using .../libasound2_1.0.25-1ubuntu10.1_amd64.deb) ...
Unpacking replacement libasound2 ...
Preparing to replace libasound2:i386 1.0.25-1ubuntu10.1 (using .../libasound2_1.0.25-1ubuntu10.1_i386.deb) ...
Unpacking replacement libasound2:i386 ...
Preparing to replace linux-image-3.2.0-37-generic 3.2.0-37.58 (using .../linux-image-3.2.0-37-generic_3.2.0-37.58_amd64.deb) ...
Done.
Unpacking replacement linux-image-3.2.0-37-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-37-generic /boot/vmlinuz-3.2.0-37-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-37-generic /boot/vmlinuz-3.2.0-37-generic
Preparing to replace alsa-base 1.0.25+dfsg-0ubuntu1 (using .../alsa-base_1.0.25+dfsg-0ubuntu1_all.deb) ...
Unpacking replacement alsa-base ...
Preparing to replace linux-sound-base 1.0.25+dfsg-0ubuntu1 (using .../linux-sound-base_1.0.25+dfsg-0ubuntu1_all.deb) ...
Unpacking replacement linux-sound-base ...
Preparing to replace ubuntu-desktop 1.267.1 (using .../ubuntu-desktop_1.267.1_amd64.deb) ...
Unpacking replacement ubuntu-desktop ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gconf2 ...
Setting up linux-sound-base (1.0.25+dfsg-0ubuntu1) ...
Setting up libasound2 (1.0.25-1ubuntu10.1) ...
Setting up libasound2:i386 (1.0.25-1ubuntu10.1) ...
Setting up alsa-utils (1.0.25-1ubuntu5) ...
Setting up gdm (3.0.4-0ubuntu15) ...
Setting up linux-image-3.2.0-37-generic (3.2.0-37.58) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.2.0-37.58 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.2.0-37.58 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-37-generic /boot/vmlinuz-3.2.0-37-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-37-generic /boot/vmlinuz-3.2.0-37-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-37-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-37-generic /boot/vmlinuz-3.2.0-37-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-37-generic /boot/vmlinuz-3.2.0-37-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-37-generic /boot/vmlinuz-3.2.0-37-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
Found linux image: /boot/vmlinuz-3.2.0-36-generic
Found initrd image: /boot/initrd.img-3.2.0-36-generic
Found linux image: /boot/vmlinuz-3.2.0-35-generic
Found initrd image: /boot/initrd.img-3.2.0-35-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found linux image: /boot/vmlinuz-2.6.32-45-generic
Found initrd image: /boot/initrd.img-2.6.32-45-generic
Found linux image: /boot/vmlinuz-2.6.32-41-generic
Found initrd image: /boot/initrd.img-2.6.32-41-generic
Found linux image: /boot/vmlinuz-2.6.32-39-generic
Found initrd image: /boot/initrd.img-2.6.32-39-generic
Found linux image: /boot/vmlinuz-2.6.32-38-generic
Found initrd image: /boot/initrd.img-2.6.32-38-generic
Found linux image: /boot/vmlinuz-2.6.32-36-generic
Found initrd image: /boot/initrd.img-2.6.32-36-generic
Found linux image: /boot/vmlinuz-2.6.32-35-generic
Found initrd image: /boot/initrd.img-2.6.32-35-generic
Found linux image: /boot/vmlinuz-2.6.32-34-generic
Found initrd image: /boot/initrd.img-2.6.32-34-generic
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found linux image: /boot/vmlinuz-2.6.32-32-generic
Found initrd image: /boot/initrd.img-2.6.32-32-generic
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found linux image: /boot/vmlinuz-2.6.32-30-generic
Found initrd image: /boot/initrd.img-2.6.32-30-generic
Found linux image: /boot/vmlinuz-2.6.32-29-generic
Found initrd image: /boot/initrd.img-2.6.32-29-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 8 (loader) on /dev/sda1
done
Setting up alsa-base (1.0.25+dfsg-0ubuntu1) ...
Setting up ubuntu-desktop (1.267.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
rob@rob-MS-7502:~$ 

```

---

