---
title: "What is needed to convert 30 small clips into 1 clip?"
date: 2007-11-19
forum: Multimedia &amp; Video
---

### Post by lime4x4 on 2007-11-19
I have a bunch of small clips that i would like to convert into 1 clip?

---

### Post by ron999 on 2007-11-19
Hi
You could use Avidemux.

Start Avidemux.
File > Open... then select your first clip.
Then
File > Append... then select the second clip.
Then
File > Append... then select the third clip.
And so on.
Then finish by 
File > Save > Save Video 
:guitar:

---

### Post by lime4x4 on 2007-11-19
I can't install that. Here is the error i'm getting

The following packages have unmet dependencies:
  avidemux: Depends: libfaad2-0 (>= 2.0.0+cvs20040908+mp4v2+bmp) but it is not going to be installed
E: Broken packages

If i try to install that package it want's to remove about 17 other apps and packages. Some of those apps i use.

---

### Post by ron999 on 2007-11-19
Hi
I'm not sure what's wrong.
If you're using Ubuntu you should be able to install Avidemux using Synaptic Package Manager.
I don't think that Synaptic will uninstall anything that is needed by another app.
But it's up to you.

---

### Post by rsambuca on 2007-11-19
There could be a minor problem with your repositories.  Can you post the output of 

cat /etc/apt/sources.list

---

### Post by lime4x4 on 2007-11-19
john@john-feisty:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
# gOS Repositories
deb [http://packages.thinkgos.com/gos/](http://packages.thinkgos.com/gos/) painful main
deb-src [http://packages.thinkgos.com/gos/](http://packages.thinkgos.com/gos/) painful main
john@john-feisty:~$

---

### Post by rsambuca on 2007-11-19
Does it say anything when you  run

sudo apt-get update
sudo apt-get upgrade

---

### Post by lime4x4 on 2007-11-19
john@john-feisty:~$ sudo apt-get update
[sudo] password for john:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US         
Get:4 [http://packages.thinkgos.com](http://packages.thinkgos.com) painful Release.gpg [189B]                  
Ign [http://packages.thinkgos.com](http://packages.thinkgos.com) painful/main Translation-en_US                
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Get:6 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release [6998B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US       
Hit [http://packages.thinkgos.com](http://packages.thinkgos.com) painful Release                               
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US            
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Get:9 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                           
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US                     
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_US      
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release.gpg [191B]         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Translation-en_US        
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release [58.5kB]                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                                 
Ign [http://packages.thinkgos.com](http://packages.thinkgos.com) painful/main Packages                         
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release [58.5kB]             
Ign [http://packages.thinkgos.com](http://packages.thinkgos.com) painful/main Sources                          
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Hit [http://packages.thinkgos.com](http://packages.thinkgos.com) painful/main Packages                         
Hit [http://packages.thinkgos.com](http://packages.thinkgos.com) painful/main Sources                          
Get:14 [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages [717B]              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release                           
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release [58.5kB]               
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release [44.0kB]           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources                      
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages [20.1kB]      
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages [3202B]     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages               
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages [49.0kB]       
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Packages [4263B]    
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Packages [51.2kB]         
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages [4263B]  
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources [12.1kB]        
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources [937B]    
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Packages [5480B]      
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Packages [14B]  
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Packages [12.8kB] 
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Packages [2599B]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Sources [3235B]       
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Sources [14B]   
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Packages [3206B]    
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Packages [18.9kB]     
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Sources [4695B]   
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Sources [832B]  
Get:35 [http://www.virtualbox.org](http://www.virtualbox.org) gutsy Release.gpg [189B]                      
Ign [http://www.virtualbox.org](http://www.virtualbox.org) gutsy/non-free Translation-en_US
Hit [http://www.virtualbox.org](http://www.virtualbox.org) gutsy Release
Hit [http://www.virtualbox.org](http://www.virtualbox.org) gutsy/non-free Packages
Fetched 425kB in 45s (9302B/s)
Reading package lists... Done
john@john-feisty:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  ardour tzdata
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 7199kB of archives.
After unpacking 344kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main tzdata 2007i-0ubuntu0.7.10 [654kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe ardour 1:2.1-1~gutsy1 [6545kB]
Fetched 7199kB in 12s (593kB/s)                                                
Preconfiguring packages ...
(Reading database ... 284063 files and directories currently installed.)
Preparing to replace tzdata 2007h-0ubuntu0.7.10 (using .../tzdata_2007i-0ubuntu0.7.10_all.deb) ...
Unpacking replacement tzdata ...
Setting up tzdata (2007i-0ubuntu0.7.10) ...

User defined timezone, leaving /etc/localtime unchanged.
Local time is now:      Mon Nov 19 21:18:25 EST 2007.
Universal Time is now:  Tue Nov 20 02:18:25 UTC 2007.
Run 'dpkg-reconfigure tzdata' if you wish to change it.


(Reading database ... 284063 files and directories currently installed.)
Preparing to replace ardour 1:2.0.5-1ubuntu1 (using .../ardour_1%3a2.1-1~gutsy1_i386.deb) ...
Unpacking replacement ardour ...
Setting up ardour (1:2.1-1~gutsy1) ...
Installing new version of config file /etc/ardour2/ardour2_ui_dark.rc ...
Installing new version of config file /etc/ardour2/ardour2_ui_light.rc ...
Installing new version of config file /etc/ardour2/ardour2_ui_default.conf ...
Installing new version of config file /etc/ardour2/ardour.menus ...
Installing new version of config file /etc/ardour2/ardour.bindings ...

localepurge: Disk space freed in /usr/share/locale: 652K
john@john-feisty:~$ sudo apt-get install avidemux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avidemux: Depends: libfaad2-0 (>= 2.0.0+cvs20040908+mp4v2+bmp) but it is not going to be installed
E: Broken packages
john@john-feisty:~$

---

