---
title: "VLC- restricted areas- decrytption"
date: 2014-03-04
forum: Multimedia Software
---

### Post by christon74 on 2014-03-04
Good afternoon every ubunter:)
it seems 'libdvdcss2' is now obsolete or has been replaced by something else (W32?)
I have tried to download them codecs but here is the answer I get:
sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: **_Unable to locate package w32codecs_**

it is not the first time trying to download something using a terminal windows ends with 'unable to locate....'

If you have any hint or suggestion, they are highly welcome.
Thanks in advance for all help and trouble.
Chris

---

### Post by christon74 on 2014-03-04
More details about not being able to play some (not DVDs)
root@hp1:/home/christophe# sudo apt-get update
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise Release.gpg
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-updates Release.gpg                   
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-updates Release                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-backports Release                     
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise/main Sources                          
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise/universe Sources                      
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise/universe TranslationIndex             
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-updates/main Sources                  
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-updates/restricted Sources            
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-updates/universe Sources              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-updates/multiverse Sources            
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-updates/main i386 Packages            
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-updates/restricted i386 Packages      
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-updates/universe i386 Packages        
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-updates/multiverse i386 Packages      
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-backports/main Sources                
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-backports/restricted Sources          
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-backports/multiverse Sources          
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-backports/main i386 Packages          
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-backports/restricted i386 Packages    
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-backports/universe i386 Packages      
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-backports/multiverse i386 Packages    
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise/main Translation-en_GB                
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise/multiverse Translation-en_GB          
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise/restricted Translation-en_GB          
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise/universe Translation-en_GB            
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-updates/main Translation-en_GB        
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-updates/multiverse Translation-en_GB  
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-updates/restricted Translation-en_GB  
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-updates/universe Translation-en_GB    
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) precise-backports/universe Translation-en     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_GB                    
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [98.1 kB]       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B] 
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [30.9 kB]   
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,782 B] 
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [388 kB]  
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [95.5 kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,641 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
100% [Connecting to antesis.freecontrib.org (213.251.190.135)]                 
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release.gpg         
  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (110: Connection timed out)
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release             
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free TranslationIndex
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free TranslationIndex
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
  Unable to connect to antesis.freecontrib.org:http:
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
  Unable to connect to antesis.freecontrib.org:http:
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free i386 Packages
  Unable to connect to antesis.freecontrib.org:http:
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free i386 Packages
  Unable to connect to antesis.freecontrib.org:http:
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Translation-en_GB
  Unable to connect to antesis.freecontrib.org:http:
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Translation-en
  Unable to connect to antesis.freecontrib.org:http:
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Translation-en_GB
  Unable to connect to antesis.freecontrib.org:http:
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Translation-en
  Unable to connect to antesis.freecontrib.org:http:
Fetched 674 kB in 1min 3s (10.7 kB/s)
W: Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (110: Connection timed out)

W: Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/source/Sources](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/source/Sources)  Unable to connect to antesis.freecontrib.org:http:

W: Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/source/Sources](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/source/Sources)  Unable to connect to antesis.freecontrib.org:http:

W: Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-i386/Packages](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-i386/Packages)  Unable to connect to antesis.freecontrib.org:http:

W: Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages)  Unable to connect to antesis.freecontrib.org:http:

W: Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/i18n/Translation-en_GB](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/i18n/Translation-en_GB)  Unable to connect to antesis.freecontrib.org:http:

W: Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/i18n/Translation-en](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/i18n/Translation-en)  Unable to connect to antesis.freecontrib.org:http:

W: Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/i18n/Translation-en_GB](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/i18n/Translation-en_GB)  Unable to connect to antesis.freecontrib.org:http:

W: Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/i18n/Translation-en](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/i18n/Translation-en)  Unable to connect to antesis.freecontrib.org:http:

E: Some index files failed to download. They have been ignored, or old ones used instead.

AND:
sudo apt-get install libdvdcss2 w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libdvdcss2' has no installation candidate
E: Unable to locate package w32codecs
root@hp1:/home/christophe#

---

### Post by christon74 on 2014-03-04
Ha! Solved. I have found the information I needed. Just as a reminder, if any of you gets stuck the same way or has any difficulty playing encrypted DVDs, here are the instructions you should follow:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

