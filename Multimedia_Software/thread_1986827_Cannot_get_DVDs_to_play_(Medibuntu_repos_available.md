---
title: "Cannot get DVDs to play (Medibuntu repos available)"
date: 2012-05-25
forum: Multimedia Software
---

### Post by mantisdolphin on 2012-05-25
Based on many Ubuntu multimedia help guide suggestions (notably [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)), I have run many commands in terminal to get the Medibuntu and non-free stuff working in this old celeron box (it's a DVD player and game box for a four year old).  This is something I've done before when using Xubuntu 9.04 on this box, which then played DVDs no problem.  Maybe I could revert to that but it's unsupported. From what I can make out of the terminal reports, something is locked, but I'm stumped.

I manually added medibuntu lines to the sources file.
```
gksudo gedit /etc/apt/sources.list
```

```
deb http://packages.medibuntu.org/ karmic free non-free
deb-src http://packages.medibuntu.org/ karmic free non-free
```

Here are some readouts from the terminal.  Could someone please let me know if you see anything that's causing the machine to not play DVDs?  They get identified correctly in the file manager but MPlayer and VLC cannot bring up sound and audio.  Any suggestions for other data gathering commands I could run and report here would also be much appreciated.  Thanks in advance for time and help!  

Running Cinnamon in 
3.2.0-24-generic GNU/Linux
Distributor ID:	Ubuntu
Release:	12.04
Codename:	precise

```
SC2@SC2-Dimension-2400:~$ du -sh /media/
du: cannot read directory `/media/SIMPSONS_WS': Permission denied
4.4G	/media/
```

```
SC2@SC2-Dimension-2400:~$ uname -a
Linux SC2-Dimension-2400 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:52 UTC 2012 i686 i686 i386 GNU/Linux
```


```
SC2@SC2-Dimension-2400:~$ sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
[sudo] password for SC2: 
--2012-05-25 11:00:29--  http://www.medibuntu.org/sources.list.d/precise.list
Resolving www.medibuntu.org (www.medibuntu.org)... 88.191.127.22
Connecting to www.medibuntu.org (www.medibuntu.org)|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 284 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 284         --.-K/s   in 0s      

2012-05-25 11:00:30 (6.47 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [284/284]

Ign http://extras.ubuntu.com precise InRelease
Hit http://packages.medibuntu.org precise InRelease
Ign http://security.ubuntu.com precise-security InRelease
Ign http://archive.canonical.com precise InRelease
Hit http://extras.ubuntu.com precise Release.gpg
Ign http://ppa.launchpad.net precise InRelease
Ign http://ppa.launchpad.net precise InRelease
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Hit http://archive.canonical.com precise Release.gpg
Hit http://extras.ubuntu.com precise Release
Hit http://ppa.launchpad.net precise Release.gpg
Get:2 http://security.ubuntu.com precise-security Release [49.6 kB]
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://archive.canonical.com precise Release
Hit http://extras.ubuntu.com precise/main Sources
Hit http://packages.medibuntu.org precise/free i386 Packages
Hit http://extras.ubuntu.com precise/main i386 Packages
Ign http://extras.ubuntu.com precise/main TranslationIndex
Hit http://archive.canonical.com precise/partner Sources
Hit http://ppa.launchpad.net precise Release
Hit http://archive.canonical.com precise/partner i386 Packages
Ign http://archive.canonical.com precise/partner TranslationIndex
Get:3 http://security.ubuntu.com precise-security/main Sources [12.6 kB]
Hit http://packages.medibuntu.org precise/non-free i386 Packages
Hit http://ppa.launchpad.net precise Release
Get:4 http://security.ubuntu.com precise-security/restricted Sources [14 B]
Get:5 http://security.ubuntu.com precise-security/universe Sources [4,522 B]
Get:6 http://security.ubuntu.com precise-security/multiverse Sources [696 B]
Get:7 http://security.ubuntu.com precise-security/main i386 Packages [43.9 kB]
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://packages.medibuntu.org precise/free TranslationIndex
Get:8 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:9 http://security.ubuntu.com precise-security/universe i386 Packages [10.3 kB]
Get:10 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,393 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Ign http://packages.medibuntu.org precise/non-free TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en_US
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://extras.ubuntu.com precise/main Translation-en
Ign http://archive.canonical.com precise/partner Translation-en_US
Ign http://archive.canonical.com precise/partner Translation-en
Ign http://us.archive.ubuntu.com precise InRelease
Ign http://us.archive.ubuntu.com precise-updates InRelease
Ign http://us.archive.ubuntu.com precise-backports InRelease
Get:11 http://us.archive.ubuntu.com precise Release.gpg [198 B]
Get:12 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]
Get:13 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]
Get:14 http://us.archive.ubuntu.com precise Release [49.6 kB]
Ign http://ppa.launchpad.net precise/main Translation-en_US
Get:15 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]
Get:16 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]
Ign http://ppa.launchpad.net precise/main Translation-en
Get:17 http://us.archive.ubuntu.com precise/main Sources [934 kB]
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://packages.medibuntu.org precise/free Translation-en_US
Ign http://packages.medibuntu.org precise/free Translation-en
Get:18 http://us.archive.ubuntu.com precise/restricted Sources [5,470 B]
Get:19 http://us.archive.ubuntu.com precise/universe Sources [5,019 kB]
Ign http://packages.medibuntu.org precise/non-free Translation-en_US
Ign http://packages.medibuntu.org precise/non-free Translation-en
Get:20 http://us.archive.ubuntu.com precise/multiverse Sources [155 kB]
Get:21 http://us.archive.ubuntu.com precise/main i386 Packages [1,274 kB]
Get:22 http://us.archive.ubuntu.com precise/restricted i386 Packages [8,431 B]
Get:23 http://us.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]
Get:24 http://us.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]
Hit http://us.archive.ubuntu.com precise/main TranslationIndex
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex
Get:25 http://us.archive.ubuntu.com precise-updates/main Sources [45.5 kB]
Get:26 http://us.archive.ubuntu.com precise-updates/restricted Sources [1,379 B]
Get:27 http://us.archive.ubuntu.com precise-updates/universe Sources [13.4 kB]
Get:28 http://us.archive.ubuntu.com precise-updates/multiverse Sources [696 B]
Get:29 http://us.archive.ubuntu.com precise-updates/main i386 Packages [118 kB]
Get:30 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [2,439 B]
Get:31 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [36.0 kB]
Get:32 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [1,393 B]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex
Get:33 http://us.archive.ubuntu.com precise-backports/main Sources [700 B]
Get:34 http://us.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:35 http://us.archive.ubuntu.com precise-backports/universe Sources [3,490 B]
Get:36 http://us.archive.ubuntu.com precise-backports/multiverse Sources [14 B]
Get:37 http://us.archive.ubuntu.com precise-backports/main i386 Packages [559 B]
Get:38 http://us.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:39 http://us.archive.ubuntu.com precise-backports/universe i386 Packages [2,653 B]
Get:40 http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages [14 B]
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise/main Translation-en
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise/restricted Translation-en
Hit http://us.archive.ubuntu.com precise/universe Translation-en
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Fetched 12.8 MB in 1min 52s (114 kB/s)
Reading package lists...
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists...
Building dependency tree...
Reading state information...
medibuntu-keyring is already the newest version.
The following packages were automatically installed and are no longer required:
  libxfcegui4-4 libx264-116 libregexp-java libaiksaurusgtk-1.2-0c2a
  libaiksaurus-1.2-0c2a libaccess-bridge-java-jni libaccess-bridge-java
  libabiword-2.8 libpolkit-gtk-1-0 libmusicbrainz4c2a libaiksaurus-1.2-data
  libwv-1.2-3 libept1 openoffice.org-common libvpx0 libaudiofile0 libiso9660-7
  libattica0 libmcs1 libmatroska4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 61 not upgraded.
Ign http://ppa.launchpad.net precise InRelease
Ign http://ppa.launchpad.net precise InRelease
Hit http://packages.medibuntu.org precise InRelease
Ign http://extras.ubuntu.com precise InRelease
Ign http://archive.canonical.com precise InRelease
Hit http://ppa.launchpad.net precise Release.gpg
Ign http://security.ubuntu.com precise-security InRelease
Hit http://extras.ubuntu.com precise Release.gpg
Hit http://archive.canonical.com precise Release.gpg
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://security.ubuntu.com precise-security Release.gpg
Hit http://extras.ubuntu.com precise Release
Hit http://archive.canonical.com precise Release
Hit http://ppa.launchpad.net precise Release
Hit http://security.ubuntu.com precise-security Release
Hit http://packages.medibuntu.org precise/free i386 Packages
Hit http://extras.ubuntu.com precise/main Sources
Hit http://ppa.launchpad.net precise Release
Hit http://archive.canonical.com precise/partner Sources
Hit http://extras.ubuntu.com precise/main i386 Packages
Ign http://extras.ubuntu.com precise/main TranslationIndex
Hit http://security.ubuntu.com precise-security/main Sources
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://archive.canonical.com precise/partner i386 Packages
Ign http://archive.canonical.com precise/partner TranslationIndex
Hit http://packages.medibuntu.org precise/non-free i386 Packages
Hit http://security.ubuntu.com precise-security/restricted Sources
Hit http://security.ubuntu.com precise-security/universe Sources
Hit http://security.ubuntu.com precise-security/multiverse Sources
Hit http://security.ubuntu.com precise-security/main i386 Packages
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Ign http://packages.medibuntu.org precise/free TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Ign http://packages.medibuntu.org precise/non-free TranslationIndex
Hit http://security.ubuntu.com precise-security/universe Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en_US
Ign http://extras.ubuntu.com precise/main Translation-en
Ign http://archive.canonical.com precise/partner Translation-en_US
Ign http://archive.canonical.com precise/partner Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://us.archive.ubuntu.com precise InRelease
Ign http://us.archive.ubuntu.com precise-updates InRelease
Ign http://us.archive.ubuntu.com precise-backports InRelease
Hit http://us.archive.ubuntu.com precise Release.gpg
Hit http://us.archive.ubuntu.com precise-updates Release.gpg
Hit http://us.archive.ubuntu.com precise-backports Release.gpg
Hit http://us.archive.ubuntu.com precise Release
Hit http://us.archive.ubuntu.com precise-updates Release
Hit http://us.archive.ubuntu.com precise-backports Release
Hit http://us.archive.ubuntu.com precise/main Sources
Hit http://us.archive.ubuntu.com precise/restricted Sources
Hit http://us.archive.ubuntu.com precise/universe Sources
Hit http://us.archive.ubuntu.com precise/multiverse Sources
Hit http://us.archive.ubuntu.com precise/main i386 Packages
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise/universe i386 Packages
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise/main TranslationIndex
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/main Sources
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources
Hit http://us.archive.ubuntu.com precise-updates/universe Sources
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/main Sources
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources
Hit http://us.archive.ubuntu.com precise-backports/universe Sources
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise/main Translation-en
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise/restricted Translation-en
Hit http://us.archive.ubuntu.com precise/universe Translation-en
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Ign http://packages.medibuntu.org precise/free Translation-en_US
Ign http://packages.medibuntu.org precise/free Translation-en
Ign http://packages.medibuntu.org precise/non-free Translation-en_US
Ign http://packages.medibuntu.org precise/non-free Translation-en
Reading package lists...
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
SC2@SC2-Dimension-2400:~$ apt-get update 
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
SC2@SC2-Dimension-2400:~$ sudo apt-get update 
Ign http://security.ubuntu.com precise-security InRelease
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://archive.canonical.com precise InRelease                             
Hit http://security.ubuntu.com precise-security Release.gpg                    
Ign http://extras.ubuntu.com precise InRelease                                 
Hit http://packages.medibuntu.org precise InRelease                            
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://archive.canonical.com precise Release.gpg                           
Ign http://us.archive.ubuntu.com precise InRelease                             
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Ign http://us.archive.ubuntu.com precise-backports InRelease                   
Hit http://security.ubuntu.com precise-security Release                        
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://archive.canonical.com precise Release                               
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Hit http://us.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://extras.ubuntu.com precise Release                                   
Hit http://security.ubuntu.com precise-security/main Sources                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://us.archive.ubuntu.com precise Release                               
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://packages.medibuntu.org precise/free i386 Packages                   
Hit http://security.ubuntu.com precise-security/restricted Sources             
Hit http://security.ubuntu.com precise-security/universe Sources               
Hit http://security.ubuntu.com precise-security/multiverse Sources             
Hit http://security.ubuntu.com precise-security/main i386 Packages             
Hit http://security.ubuntu.com precise-security/restricted i386 Packages       
Hit http://security.ubuntu.com precise-security/universe i386 Packages         
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages       
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://ppa.launchpad.net precise Release                                   
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://us.archive.ubuntu.com precise-updates Release                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://us.archive.ubuntu.com precise-backports Release                     
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://packages.medibuntu.org precise/non-free i386 Packages               
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Hit http://us.archive.ubuntu.com precise-updates/main Sources                  
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources            
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://us.archive.ubuntu.com precise-updates/universe Sources              
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources            
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages            
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages      
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages        
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Ign http://packages.medibuntu.org precise/free TranslationIndex                
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com precise-backports/main Sources                
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://us.archive.ubuntu.com precise-backports/universe Sources            
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages    
Ign http://packages.medibuntu.org precise/non-free TranslationIndex            
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://extras.ubuntu.com precise/main Translation-en             
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://packages.medibuntu.org precise/free Translation-en_US               
Ign http://packages.medibuntu.org precise/free Translation-en
Ign http://packages.medibuntu.org precise/non-free Translation-en_US
Ign http://packages.medibuntu.org precise/non-free Translation-en
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
SC2@SC2-Dimension-2400:~$ gksudo gedit /etc/apt/sources.list
SC2@SC2-Dimension-2400:~$ wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
OK
Ign http://archive.canonical.com precise InRelease                             
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://archive.canonical.com precise Release.gpg                           
Ign http://security.ubuntu.com precise-security InRelease                      
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:1 http://packages.medibuntu.org karmic InRelease [9,481 B]                 
Hit http://archive.canonical.com precise Release                               
Ign http://extras.ubuntu.com precise InRelease                                 
Get:2 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:3 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Get:4 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise Release                                   
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://ppa.launchpad.net precise Release                                   
Hit http://packages.medibuntu.org precise InRelease                            
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:5 http://security.ubuntu.com precise-security/main Sources [12.6 kB]       
Get:6 http://packages.medibuntu.org karmic/free Sources [3,259 B]              
Get:7 http://security.ubuntu.com precise-security/restricted Sources [14 B]    
Get:8 http://security.ubuntu.com precise-security/universe Sources [4,522 B]   
Get:9 http://security.ubuntu.com precise-security/multiverse Sources [696 B]   
Get:10 http://security.ubuntu.com precise-security/main i386 Packages [43.9 kB]
Get:11 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:12 http://security.ubuntu.com precise-security/universe i386 Packages [10.3 kB]
Get:13 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,393 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Get:14 http://packages.medibuntu.org karmic/non-free Sources [5,543 B]         
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Get:15 http://packages.medibuntu.org karmic/free i386 Packages [3,271 B]       
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Get:16 http://packages.medibuntu.org karmic/non-free i386 Packages [7,277 B]   
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://packages.medibuntu.org karmic/free TranslationIndex                 
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://packages.medibuntu.org karmic/non-free TranslationIndex             
Hit http://packages.medibuntu.org precise/free i386 Packages                   
Hit http://packages.medibuntu.org precise/non-free i386 Packages               
Ign http://us.archive.ubuntu.com precise InRelease                             
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Ign http://us.archive.ubuntu.com precise-backports InRelease                   
Ign http://packages.medibuntu.org precise/free TranslationIndex                
Get:17 http://us.archive.ubuntu.com precise Release.gpg [198 B]                
Get:18 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]        
Ign http://packages.medibuntu.org precise/non-free TranslationIndex            
Get:19 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]      
Get:20 http://us.archive.ubuntu.com precise Release [49.6 kB]                  
Get:21 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]          
Get:22 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]        
Get:23 http://us.archive.ubuntu.com precise/main Sources [934 kB]              
Get:24 http://us.archive.ubuntu.com precise/restricted Sources [5,470 B]       
Get:25 http://us.archive.ubuntu.com precise/universe Sources [5,019 kB]        
Ign http://packages.medibuntu.org karmic/free Translation-en_US                
Ign http://packages.medibuntu.org karmic/free Translation-en                   
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US            
Ign http://packages.medibuntu.org karmic/non-free Translation-en               
Ign http://packages.medibuntu.org precise/free Translation-en_US               
Ign http://packages.medibuntu.org precise/free Translation-en                  
Ign http://packages.medibuntu.org precise/non-free Translation-en_US           
Ign http://packages.medibuntu.org precise/non-free Translation-en              
Get:26 http://us.archive.ubuntu.com precise/multiverse Sources [155 kB]        
Get:27 http://us.archive.ubuntu.com precise/main i386 Packages [1,274 kB]      
Get:28 http://us.archive.ubuntu.com precise/restricted i386 Packages [8,431 B] 
Get:29 http://us.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]  
Get:30 http://us.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]  
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:31 http://us.archive.ubuntu.com precise-updates/main Sources [45.5 kB]     
Get:32 http://us.archive.ubuntu.com precise-updates/restricted Sources [1,379 B]
Get:33 http://us.archive.ubuntu.com precise-updates/universe Sources [13.4 kB] 
Get:34 http://us.archive.ubuntu.com precise-updates/multiverse Sources [696 B] 
Get:35 http://us.archive.ubuntu.com precise-updates/main i386 Packages [118 kB]
Get:36 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [2,439 B]
Get:37 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [36.0 kB]
Get:38 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [1,393 B]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Get:39 http://us.archive.ubuntu.com precise-backports/main Sources [700 B]     
Get:40 http://us.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:41 http://us.archive.ubuntu.com precise-backports/universe Sources [3,490 B]
Get:42 http://us.archive.ubuntu.com precise-backports/multiverse Sources [14 B]
Get:43 http://us.archive.ubuntu.com precise-backports/main i386 Packages [559 B]
Get:44 http://us.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:45 http://us.archive.ubuntu.com precise-backports/universe i386 Packages [2,653 B]
Get:46 http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages [14 B]
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 12.8 MB in 1min 38s (130 kB/s)                                         
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
SC2@SC2-Dimension-2400:~$ sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin
[sudo] password for SC2: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
SC2@SC2-Dimension-2400:~$ sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package kaffeine-mozilla
E: Unable to locate package mozilla-helix-player
E: Unable to locate package mozilla-mplayer
SC2@SC2-Dimension-2400:~$ 

```

---

### Post by CharlesA on 2012-05-25
Don't use old repos.

Did you install the ubuntu-restricted-extras ?

---

