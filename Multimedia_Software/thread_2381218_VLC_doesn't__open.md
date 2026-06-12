---
title: "VLC doesn't  open"
date: 2017-12-28
forum: Multimedia Software
---

### Post by WDYSUN on 2017-12-28
Dear Members

there is something strange with VLC. I am under Ubuntu 14.04 LTS and VLC is installed from 

[https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)

It always worked but now double clicking on file nothing happens. The same happens if I try to open from cli. 

I looked at several posts around but none of them seem consistent with the kind of errors I get 

```

vlc come_on_over.wav
VLC media player 2.2.5.1 Umbrella (revision 2.2.5.1~ppa)
[0000000001a648e8] core audio output error: no suitable audio output module
[0000000001a651e8] core interface error: no suitable interface module
[0000000001a33048] core libvlc error: interface "hotkeys,none" initialization failed
[0000000001a651e8] core interface error: no suitable interface module
[0000000001a33048] core libvlc error: interface "globalhotkeys,none" initialization failed
[0000000001a651e8] core interface error: no suitable interface module
[0000000001a33048] core libvlc error: interface "dbus,none" initialization failed
[0000000001a33048] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0000000001a651e8] core interface error: no suitable interface module
[0000000001a33048] core libvlc error: interface "default" initialization failed
[0000000001a61d38] core playlist error: could not export playlist

```




```

pietro@oak cvlc --reset-config
VLC media player 2.2.5.1 Umbrella (revision 2.2.5.1~ppa)
[00000000014bbe38] core audio output error: no suitable audio output module
[00000000014bbf78] core interface error: no suitable interface module
[000000000148a048] core libvlc error: interface "hotkeys,none" initialization failed
[00000000014bbf78] core interface error: no suitable interface module
[000000000148a048] core libvlc error: interface "globalhotkeys,none" initialization failed
[00000000014bbf78] core interface error: no suitable interface module
[000000000148a048] core libvlc error: interface "dbus,none" initialization failed
[00000000014bbf78] core interface error: no suitable interface module
[000000000148a048] core libvlc error: interface "default" initialization failed
[00000000014b9138] core playlist error: could not export playlist

```

Of course both audio and video works with other softwares.

I am getting crazy, I purged and reinstalled vlc and related packages 100 times, but nothing change!

Best
Pietro

---

### Post by ajgreeny on 2017-12-28
Open it from terminal with command **vlc** and show us the output which may give some clues.

---

### Post by WDYSUN on 2017-12-28
> **ajgreeny said:**
> Open it from terminal with command **vlc** and show us the output which may give some clues.

Hello,

calling vlc from the cli does not open the gui, this is what happens

```

pietro@oak:~$ vlc
VLC media player 2.2.5.1 Umbrella (revision 2.2.5.1~ppa)
[0000000000f9dc38] core audio output error: no suitable audio output module
[0000000000f9dd78] core interface error: no suitable interface module
[0000000000f6c048] core libvlc error: interface "hotkeys,none" initialization failed
[0000000000f9dd78] core interface error: no suitable interface module
[0000000000f6c048] core libvlc error: interface "globalhotkeys,none" initialization failed
[0000000000f9dd78] core interface error: no suitable interface module
[0000000000f6c048] core libvlc error: interface "dbus,none" initialization failed
[0000000000f6c048] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0000000000f9dd78] core interface error: no suitable interface module
[0000000000f6c048] core libvlc error: interface "default" initialization failed
[0000000000f9af38] core playlist error: could not export playlist

``` 

Cheers
Pietro

---

### Post by ajgreeny on 2017-12-28
Try renaming ~/.config/vlc as a backup, eg ~/.config/vlcbackup, with vlc not running, then start vlc again.
Perhaps your vlc configuration has become corrupt

---

### Post by mc4man on 2017-12-28
The above advice is reasonably solid so try that but just go ahead & remove .config/vlc folder entirely.

If that fails to work then post output of this in a code box, will be fairly extensive
```
apt-cache policy vlc-*
```

What also may be of some value would be output of these 2 commands, note the 2nd one is just a simulation.
Again put in code box or just copy to a .txt file & attach
```
sudo apt-get update && sudo apt-get -s dist-upgrade
```

---

### Post by WDYSUN on 2017-12-29
> **mc4man said:**
> The above advice is reasonably solid so try that but just go ahead & remove .config/vlc folder entirely.


done, still the same.


> **mc4man said:**
> 
If that fails to work then post output of this in a code box, will be fairly extensive
```
apt-cache policy vlc-*[CODE]


here the out output

[CODE]
pietro@oak:~$ apt-cache policy vlc-*
libvlc-dev:
  Installed: (none)
  Candidate: 2.2.5.1~ppa
  Version table:
     2.2.5.1~ppa 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
     2.1.6-0ubuntu14.04.4 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-security/universe amd64 Packages
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-updates/universe amd64 Packages
     2.1.2-2build2 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty/universe amd64 Packages
python-vlc:
  Installed: (none)
  Candidate: (none)
  Version table:
vlc-plugin-notify:
  Installed: 2.2.5.1~ppa
  Candidate: 2.2.5.1~ppa
  Version table:
 *** 2.2.5.1~ppa 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     2.1.6-0ubuntu14.04.4 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-security/universe amd64 Packages
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-updates/universe amd64 Packages
     2.1.2-2build2 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty/universe amd64 Packages
libvlc0-dev:
  Installed: (none)
  Candidate: (none)
  Version table:
vlc-plugin-fluidsynth:
  Installed: 2.2.8-1ubuntu3~14.04.york0
  Candidate: 2.2.8-1ubuntu3~14.04.york0
  Version table:
 *** 2.2.8-1ubuntu3~14.04.york0 0
        100 /var/lib/dpkg/status
     2.2.5.1~ppa 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
     2.1.6-0ubuntu14.04.4 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-security/universe amd64 Packages
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-updates/universe amd64 Packages
     2.1.2-2build2 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty/universe amd64 Packages
libvlccore7:
  Installed: (none)
  Candidate: 2.1.6-0ubuntu14.04.4
  Version table:
     2.1.6-0ubuntu14.04.4 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-security/universe amd64 Packages
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-updates/universe amd64 Packages
     2.1.6-0ubuntu14.04.1 0
        100 /var/lib/dpkg/status
     2.1.5+ppa1 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
     2.1.2-2build2 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty/universe amd64 Packages
libvlccore8:
  Installed: 2.2.8-1ubuntu3~14.04.york0
  Candidate: 2.2.8-1ubuntu3~14.04.york0
  Version table:
 *** 2.2.8-1ubuntu3~14.04.york0 0
        100 /var/lib/dpkg/status
     2.2.5.1~ppa 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
vlc-nox:
  Installed: 2.2.5.1~ppa
  Candidate: 2.2.5.1~ppa
  Version table:
 *** 2.2.5.1~ppa 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     2.1.6-0ubuntu14.04.4 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-security/universe amd64 Packages
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-updates/universe amd64 Packages
     2.1.2-2build2 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty/universe amd64 Packages
browser-plugin-vlc:
  Installed: (none)
  Candidate: 2.0.6-2
  Version table:
     2.0.6-2 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty/universe amd64 Packages
vlc-plugin-samba:
  Installed: 2.2.5.1~ppa
  Candidate: 2.2.5.1~ppa
  Version table:
 *** 2.2.5.1~ppa 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
vlc-plugin-zvbi:
  Installed: 2.2.5.1~ppa
  Candidate: 2.2.5.1~ppa
  Version table:
 *** 2.2.5.1~ppa 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     2.1.6-0ubuntu14.04.4 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-security/universe amd64 Packages
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-updates/universe amd64 Packages
     2.1.2-2build2 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty/universe amd64 Packages
vlc-plugin-jack:
  Installed: 2.2.5.1~ppa
  Candidate: 2.2.5.1~ppa
  Version table:
 *** 2.2.5.1~ppa 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     2.1.6-0ubuntu14.04.4 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-security/universe amd64 Packages
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-updates/universe amd64 Packages
     2.1.2-2build2 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty/universe amd64 Packages
vlc-plugin-sdl:
  Installed: 2.2.5.1~ppa
  Candidate: 2.2.5.1~ppa
  Version table:
 *** 2.2.5.1~ppa 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     2.1.6-0ubuntu14.04.4 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-security/universe amd64 Packages
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-updates/universe amd64 Packages
     2.1.2-2build2 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty/universe amd64 Packages
vlc-data:
  Installed: 2.2.5.1~ppa
  Candidate: 2.2.5.1~ppa
  Version table:
 *** 2.2.5.1~ppa 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     2.1.6-0ubuntu14.04.4 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-security/universe amd64 Packages
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-updates/universe amd64 Packages
     2.1.5+ppa1 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
     2.1.2-2build2 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty/universe amd64 Packages
vlc-bin:
  Installed: (none)
  Candidate: (none)
  Version table:
libvlccore-dev:
  Installed: (none)
  Candidate: 2.2.5.1~ppa
  Version table:
     2.2.5.1~ppa 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
     2.1.6-0ubuntu14.04.4 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-security/universe amd64 Packages
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-updates/universe amd64 Packages
     2.1.2-2build2 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty/universe amd64 Packages
vlc-plugin-libde265:
  Installed: 0.1.7-1ppa1~trusty1.1
  Candidate: 0.1.7-1ppa1~trusty1.1
  Version table:
 *** 0.1.7-1ppa1~trusty1.1 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     0.1.7-1ppa1~trusty1 0
        500 http://ppa.launchpad.net/strukturag/libde265/ubuntu/ trusty/main amd64 Packages
phonon4qt5-backend-vlc:
  Installed: (none)
  Candidate: 0.7.80-0ubuntu2
  Version table:
     0.7.80-0ubuntu2 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
     0.7.80-0ubuntu1~ubuntu14.04 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-updates/universe amd64 Packages
     0.7.1-1ubuntu3 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty/universe amd64 Packages
phonon-backend-vlc:
  Installed: (none)
  Candidate: 0.7.80-0ubuntu2
  Version table:
     0.7.80-0ubuntu2 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
     0.7.80-0ubuntu1~ubuntu14.04 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-updates/universe amd64 Packages
     0.7.1-1ubuntu3 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty/universe amd64 Packages
vlc-plugin-vlsub:
  Installed: 0.9.10-1
  Candidate: 0.9.10-1
  Version table:
 *** 0.9.10-1 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status
vlc-plugin-libde265-dbg:
  Installed: 0.1.7-1ppa1~trusty1.1
  Candidate: 0.1.7-1ppa1~trusty1.1
  Version table:
 *** 0.1.7-1ppa1~trusty1.1 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     0.1.7-1ppa1~trusty1 0
        500 http://ppa.launchpad.net/strukturag/libde265/ubuntu/ trusty/main amd64 Packages
phonon-backend-vlc-dbg:
  Installed: (none)
  Candidate: 0.7.80-0ubuntu2
  Version table:
     0.7.80-0ubuntu2 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
     0.7.80-0ubuntu1~ubuntu14.04 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-updates/universe amd64 Packages
     0.7.1-1ubuntu3 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty/universe amd64 Packages
mozilla-plugin-vlc:
  Installed: (none)
  Candidate: (none)
  Version table:
vlc-plugin-svg:
  Installed: 2.2.5.1~ppa
  Candidate: 2.2.5.1~ppa
  Version table:
 *** 2.2.5.1~ppa 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     2.1.6-0ubuntu14.04.4 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-security/universe amd64 Packages
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-updates/universe amd64 Packages
     2.1.2-2build2 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty/universe amd64 Packages
vlc:
  Installed: 2.2.5.1~ppa
  Candidate: 2.2.5.1~ppa
  Version table:
 *** 2.2.5.1~ppa 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     2.1.6-0ubuntu14.04.4 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-security/universe amd64 Packages
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-updates/universe amd64 Packages
     2.1.2-2build2 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty/universe amd64 Packages
libvlc5:
  Installed: 2.2.5.1~ppa
  Candidate: 2.2.5.1~ppa
  Version table:
 *** 2.2.5.1~ppa 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     2.1.6-0ubuntu14.04.4 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-security/universe amd64 Packages
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-updates/universe amd64 Packages
     2.1.2-2build2 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty/universe amd64 Packages
remuco-vlc:
  Installed: (none)
  Candidate: 0.9.6-2
  Version table:
     0.9.6-2 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty/universe amd64 Packages
vlc-dbg:
  Installed: (none)
  Candidate: 2.2.5.1~ppa
  Version table:
     2.2.5.1~ppa 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
     2.1.6-0ubuntu14.04.4 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-security/universe amd64 Packages
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-updates/universe amd64 Packages
     2.1.2-2build2 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty/universe amd64 Packages
vlc-plugin-pulse:
  Installed: 2.2.5.1~ppa
  Candidate: 2.2.5.1~ppa
  Version table:
 *** 2.2.5.1~ppa 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     2.1.6-0ubuntu14.04.4 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-security/universe amd64 Packages
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty-updates/universe amd64 Packages
     2.1.2-2build2 0
        500 http://ubuntu.mirror.garr.it/mirrors/ubuntu-archive/ trusty/universe amd64 Packages

```


> **mc4man said:**
> 
What also may be of some value would be output of these 2 commands, note the 2nd one is just a simulation.
Again put in code box or just copy to a .txt file & attach
```
sudo apt-get update && sudo apt-get -s dist-upgrade
```


here it is 

```

pietro@oak:~$ sudo apt-get update && sudo apt-get -s dist-upgrade
[sudo] password for pietro: 
Ign http://ubuntu.mirror.garr.it trusty InRelease
Ign http://archive.canonical.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://dl.google.com stable InRelease                                      
Get:1 http://ubuntu.mirror.garr.it trusty-security InRelease [65.9 kB]         
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://ppa.launchpad.net trusty InRelease                                  
Get:2 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Hit http://dl.google.com stable Release.gpg                                    
Hit http://repository.spotify.com stable InRelease                             
Hit http://archive.canonical.com trusty Release                                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://dl.google.com stable Release                                        
Hit http://repository.spotify.com stable/non-free amd64 Packages               
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://dl.google.com stable/main amd64 Packages                            
Get:3 https://desktop-download.mendeley.com stable InRelease                   
Ign https://desktop-download.mendeley.com stable InRelease                     
Get:4 http://ubuntu.mirror.garr.it trusty-updates InRelease [65.9 kB]          
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://repository.spotify.com stable/non-free i386 Packages                
Hit http://dl.google.com stable/main i386 Packages                             
Hit https://desktop-download.mendeley.com stable Release.gpg                   
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit https://desktop-download.mendeley.com stable Release                       
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit https://repo.skype.com stable InRelease                                    
Hit https://desktop-download.mendeley.com stable/main amd64 Packages           
Hit https://repo.skype.com stable/main amd64 Packages                          
Hit http://ubuntu.mirror.garr.it trusty Release.gpg                            
Hit https://desktop-download.mendeley.com stable/main i386 Packages            
Hit http://ppa.launchpad.net trusty InRelease                                  
Get:5 https://cloud.r-project.org trusty/ InRelease                            
Ign https://cloud.r-project.org trusty/ InRelease                              
Get:6 http://ubuntu.mirror.garr.it trusty-security/main Sources [147 kB]       
Get:7 https://repo.skype.com stable/main Translation-en_US                     
Get:8 https://desktop-download.mendeley.com stable/main Translation-en_US      
Get:9 https://desktop-download.mendeley.com stable/main Translation-en         
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:10 https://cloud.r-project.org trusty/ Release                             
Hit https://cloud.r-project.org trusty/ Packages                               
Get:11 https://desktop-download.mendeley.com stable/main Translation-en_US     
Get:12 https://desktop-download.mendeley.com stable/main Translation-en        
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://repository.spotify.com stable/non-free Translation-en_US            
Get:13 https://desktop-download.mendeley.com stable/main Translation-en_US     
Ign http://repository.spotify.com stable/non-free Translation-en               
Get:14 https://desktop-download.mendeley.com stable/main Translation-en        
Get:15 http://ubuntu.mirror.garr.it trusty-security/restricted Sources [4,931 B]
Hit http://ppa.launchpad.net trusty InRelease                                  
Get:16 https://desktop-download.mendeley.com stable/main Translation-en_US     
Get:17 http://ubuntu.mirror.garr.it trusty-security/universe Sources [67.2 kB] 
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Get:18 https://desktop-download.mendeley.com stable/main Translation-en        
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:19 https://cloud.r-project.org trusty/ Translation-en_US                   
Get:20 https://desktop-download.mendeley.com stable/main Translation-en_US     
Ign https://desktop-download.mendeley.com stable/main Translation-en_US        
Ign http://dl.google.com stable/main Translation-en_US                         
Get:21 https://desktop-download.mendeley.com stable/main Translation-en        
Ign https://desktop-download.mendeley.com stable/main Translation-en           
Get:22 http://ubuntu.mirror.garr.it trusty-security/multiverse Sources [3,182 B]
Ign http://dl.google.com stable/main Translation-en                            
Ign http://ppa.launchpad.net trusty InRelease                         
Get:23 http://ubuntu.mirror.garr.it trusty-security/main amd64 Packages [698 kB]
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign https://repo.skype.com stable/main Translation-en_US                       
Ign https://repo.skype.com stable/main Translation-en                          
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main Sources                               
Ign https://cloud.r-project.org trusty/ Translation-en_US                      
Ign https://cloud.r-project.org trusty/ Translation-en                         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:24 http://ubuntu.mirror.garr.it trusty-security/restricted amd64 Packages [14.1 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:25 http://ubuntu.mirror.garr.it trusty-security/universe amd64 Packages [199 kB]
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:26 http://ubuntu.mirror.garr.it trusty-security/multiverse amd64 Packages [4,800 B]
Get:27 http://ubuntu.mirror.garr.it trusty-security/main i386 Packages [641 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:28 http://ubuntu.mirror.garr.it trusty-security/restricted i386 Packages [13.9 kB]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:29 http://ubuntu.mirror.garr.it trusty-security/universe i386 Packages [195 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:30 http://ubuntu.mirror.garr.it trusty-security/multiverse i386 Packages [4,958 B]
Get:31 http://ubuntu.mirror.garr.it trusty-security/main Translation-en [375 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                    
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:32 http://ubuntu.mirror.garr.it trusty-security/multiverse Translation-en [2,564 B]
Get:33 http://ubuntu.mirror.garr.it trusty-security/restricted Translation-en [3,542 B]
Hit http://ppa.launchpad.net trusty/main i386 Packages                        
Get:34 http://ubuntu.mirror.garr.it trusty-security/universe Translation-en [113 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:35 http://ubuntu.mirror.garr.it trusty-updates/main Sources [409 kB]       
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:36 http://ubuntu.mirror.garr.it trusty-updates/restricted Sources [6,322 B]
Get:37 http://ubuntu.mirror.garr.it trusty-updates/universe Sources [195 kB]   
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty Release                                    
Get:38 http://ubuntu.mirror.garr.it trusty-updates/multiverse Sources [7,781 B]
Get:39 http://ubuntu.mirror.garr.it trusty-updates/main amd64 Packages [1,045 kB]
Hit http://ppa.launchpad.net trusty Release                                
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:40 http://ubuntu.mirror.garr.it trusty-updates/restricted amd64 Packages [17.2 kB]
Get:41 http://ubuntu.mirror.garr.it trusty-updates/universe amd64 Packages [437 kB]
Get:42 http://ubuntu.mirror.garr.it trusty-updates/multiverse amd64 Packages [14.9 kB]
Get:43 http://ubuntu.mirror.garr.it trusty-updates/main i386 Packages [985 kB] 
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Get:44 http://ubuntu.mirror.garr.it trusty-updates/restricted i386 Packages [17.0 kB]
Get:45 http://ubuntu.mirror.garr.it trusty-updates/universe i386 Packages [435 kB]
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Get:46 http://ubuntu.mirror.garr.it trusty-updates/multiverse i386 Packages [15.3 kB]
Get:47 http://ubuntu.mirror.garr.it trusty-updates/main Translation-en [516 kB]
Get:48 http://ubuntu.mirror.garr.it trusty-updates/multiverse Translation-en [7,760 B]
Get:49 http://ubuntu.mirror.garr.it trusty-updates/restricted Translation-en [4,031 B]
Get:50 http://ubuntu.mirror.garr.it trusty-updates/universe Translation-en [236 kB]
Hit http://ubuntu.mirror.garr.it trusty Release                                
Hit http://ubuntu.mirror.garr.it trusty/main Sources                           
Hit http://ubuntu.mirror.garr.it trusty/restricted Sources                     
Hit http://ubuntu.mirror.garr.it trusty/universe Sources                       
Hit http://ubuntu.mirror.garr.it trusty/multiverse Sources                     
Hit http://ubuntu.mirror.garr.it trusty/main amd64 Packages                    
Hit http://ubuntu.mirror.garr.it trusty/restricted amd64 Packages              
Hit http://ubuntu.mirror.garr.it trusty/universe amd64 Packages                
Hit http://ubuntu.mirror.garr.it trusty/multiverse amd64 Packages              
Hit http://ubuntu.mirror.garr.it trusty/main i386 Packages                     
Hit http://ubuntu.mirror.garr.it trusty/restricted i386 Packages               
Hit http://ubuntu.mirror.garr.it trusty/universe i386 Packages                 
Hit http://ubuntu.mirror.garr.it trusty/multiverse i386 Packages               
Hit http://ubuntu.mirror.garr.it trusty/main Translation-en                    
Hit http://ubuntu.mirror.garr.it trusty/multiverse Translation-en              
Hit http://ubuntu.mirror.garr.it trusty/restricted Translation-en              
Hit http://ubuntu.mirror.garr.it trusty/universe Translation-en                
Ign http://ubuntu.mirror.garr.it trusty/main Translation-en_US                 
Ign http://ubuntu.mirror.garr.it trusty/multiverse Translation-en_US           
Ign http://ubuntu.mirror.garr.it trusty/restricted Translation-en_US           
Ign http://ubuntu.mirror.garr.it trusty/universe Translation-en_US             
Fetched 6,970 kB in 11s (622 kB/s)                                             
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  firefox firefox-locale-en firefox-locale-it
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Inst firefox [57.0.1+build2-0ubuntu0.14.04.1] (57.0.3+build1-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-security [amd64])
Inst firefox-locale-en [57.0.1+build2-0ubuntu0.14.04.1] (57.0.3+build1-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-security [amd64])
Inst firefox-locale-it [57.0.1+build2-0ubuntu0.14.04.1] (57.0.3+build1-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-security [amd64])
Conf firefox (57.0.3+build1-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-security [amd64])
Conf firefox-locale-en (57.0.3+build1-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-security [amd64])
Conf firefox-locale-it (57.0.3+build1-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-security [amd64])

```

Thanks 
Pietro

---

### Post by mc4man on 2017-12-29
Pretty simple, you have mixed vlc packages from 2 ppa's. If you wish to get vlc from a ppa then just use one. So start with - 
```
sudo apt-get purge vlc-*
```
Now if you want the 2.2.8 version then add back the york ppa to your sources, run sudo apt-get update then sudo apt-get install vlc.

If you want the 2.2.5 version from my ppa then after the purge just re-install vlc. Not sure if I'm inclined to provide 2.2.8 for 14.04, I have it for 16.04 so could do but honestly probably won't..

---

### Post by WDYSUN on 2017-12-30
> **mc4man said:**
> Pretty simple, you have mixed vlc packages from 2 ppa's. If you wish to get vlc from a ppa then just use one. So start with - 
```
sudo apt-get purge vlc-*
```
Now if you want the 2.2.8 version then add back the york ppa to your sources, run sudo apt-get update then sudo apt-get install vlc.

If you want the 2.2.5 version from my ppa then after the purge just re-install vlc. Not sure if I'm inclined to provide 2.2.8 for 14.04, I have it for 16.04 so could do but honestly probably won't..

Thanks a lot it worked! 2.2.9 works on my machine! For the moment there is no issue about it.

Happy new year
Pietro

---

