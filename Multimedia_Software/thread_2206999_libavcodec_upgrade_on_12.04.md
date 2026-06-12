---
title: "libavcodec upgrade? on 12.04"
date: 2014-02-21
forum: Multimedia Software
---

### Post by sdowney717 on 2014-02-21
Anyway to do this, go from 53 to 54 version which is in trusty?

[https://launchpad.net/ubuntu/trusty/i386/libavcodec-extra-54](https://launchpad.net/ubuntu/trusty/i386/libavcodec-extra-54)

---

### Post by monkeybrain20122 on 2014-02-21
[https://launchpad.net/~samrog131/+archive/ppa](https://launchpad.net/~samrog131/+archive/ppa)

See this for how to set it to be the default ffmpeg
[http://askubuntu.com/questions/361299/ffmpeg2-on-ubuntu-12-10-quantal-server](http://askubuntu.com/questions/361299/ffmpeg2-on-ubuntu-12-10-quantal-server)

---

### Post by sdowney717 on 2014-02-21
I dont think it works for 12.04?
```
scott@scott-P5QC:~$ sudo add-apt-repository ppa:samrog131/ppa
You are about to add the following PPA to your system:
 Misc (small)  apps...

.
.
I have been checking/testing these and dropping them to here to be available. BUT:

! Check the OFFICIAL repositories first !

.

# These are totally UNOFFICIAL packages: Kubuntu does not provide these packages so they are not a supported piece of software. 

# Only guarantee: No harm intended - These packages (amd64 version) were working at here, they may or may not work there or in the future.  

# Packages are build against:
Precise - KDE 4.8 / Qt 4.8.1
Quantal - KDE 4.9 / Qt 4.8.3
.
Raring EOL announcement: https://lists.ubuntu.com/archives/ubuntu-announce/2014-January/000179.html
.
Saucy - KDE 4.11 / Qt 4.8.4
Trusty - KDE 4.12+13 / Qt 4.8.5

!! You could download single packages - and install them !!

1) Click "View package details"
2) Click the application (source column) that you want to download.
3) Download the amd64/i386 .deb package.
.

Old packages: https://launchpad.net/~samrog131/+archive/dump
New packages (before any testing):  https://launchpad.net/~samrog131/+archive/build-queue
 More info: https://launchpad.net/~samrog131/+archive/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpp6BSL0/secring.gpg' created
gpg: keyring `/tmp/tmpp6BSL0/pubring.gpg' created
gpg: requesting key 2B7E03A7 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpp6BSL0/trustdb.gpg: trustdb created
gpg: key 2B7E03A7: public key "Launchpad PPA for Sam Rog" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
scott@scott-P5QC:~$ sudo apt-get update
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Get:2 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Hit http://us.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://us.archive.ubuntu.com precise Release                               
Hit http://us.archive.ubuntu.com precise-updates Release                       
Hit http://dl.google.com stable Release.gpg                                    
Get:3 http://security.ubuntu.com precise-security/main Sources [97.7 kB]       
Hit http://us.archive.ubuntu.com precise-backports Release                     
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://dl.google.com stable Release.gpg                                    
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://dl.google.com stable Release.gpg                                    
Hit http://repo.wuala.com stable Release.gpg                                   
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Hit http://us.archive.ubuntu.com precise-updates/main Sources                  
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources            
Hit http://us.archive.ubuntu.com precise-updates/universe Sources              
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources            
Hit http://us.archive.ubuntu.com precise-updates/main amd64 Packages           
Hit http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages     
Hit http://us.archive.ubuntu.com precise-updates/universe amd64 Packages       
Hit http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages            
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages      
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages        
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Get:4 http://security.ubuntu.com precise-security/restricted Sources [2,494 B] 
Get:5 http://security.ubuntu.com precise-security/universe Sources [30.9 kB]   
Get:6 http://security.ubuntu.com precise-security/multiverse Sources [1,782 B] 
Get:7 http://security.ubuntu.com precise-security/main amd64 Packages [363 kB] 
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com precise-backports/main Sources                
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://us.archive.ubuntu.com precise-backports/universe Sources            
Hit http://dl.google.com stable Release                                        
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages         
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages   
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages     
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages   
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
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://dl.google.com stable Release                                        
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Hit http://repo.wuala.com stable Release                                       
Get:8 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]
Get:9 http://security.ubuntu.com precise-security/universe amd64 Packages [90.9 kB]
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Get:10 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,443 B]
Get:11 http://security.ubuntu.com precise-security/main i386 Packages [387 kB] 
Hit http://dl.google.com stable Release                                        
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Get:12 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:13 http://security.ubuntu.com precise-security/universe i386 Packages [95.4 kB]
Hit http://dl.google.com stable/main amd64 Packages                            
Get:14 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,641 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://repo.wuala.com stable/main amd64 Packages                           
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://repo.wuala.com stable/main i386 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages               
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://ppa.launchpad.net precise/main Sources                     
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Ign http://repo.wuala.com stable/main TranslationIndex                         
Hit http://ppa.launchpad.net precise/main i386 Packages               
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://ppa.launchpad.net precise/main Sources                     
Hit http://ppa.launchpad.net precise/main amd64 Packages              
Hit http://ppa.launchpad.net precise/main i386 Packages               
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://ppa.launchpad.net precise/main Sources                     
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Ign http://extras.ubuntu.com precise/main Translation-en_US           
Hit http://ppa.launchpad.net precise/main Sources                     
Hit http://ppa.launchpad.net precise/main amd64 Packages              
Hit http://ppa.launchpad.net precise/main i386 Packages               
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://ppa.launchpad.net precise/main Sources                     
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://ppa.launchpad.net precise/main Sources                     
Ign http://extras.ubuntu.com precise/main Translation-en              
Hit http://ppa.launchpad.net precise/main amd64 Packages              
Hit http://ppa.launchpad.net precise/main i386 Packages               
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages               
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://ppa.launchpad.net precise/main Sources                     
Hit http://ppa.launchpad.net precise/main amd64 Packages              
Hit http://ppa.launchpad.net precise/main i386 Packages               
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://ppa.launchpad.net precise/main Sources                     
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Ign http://dl.google.com stable/main Translation-en_US
Ign http://repo.wuala.com stable/main Translation-en_US               
Ign http://dl.google.com stable/main Translation-en                   
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://dl.google.com stable/main Translation-en_US
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main amd64 Packages              
Hit http://ppa.launchpad.net precise/main i386 Packages               
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://ppa.launchpad.net precise/main Sources                     
Ign http://dl.google.com stable/main Translation-en                   
Ign http://repo.wuala.com stable/main Translation-en                  
Ign http://dl.google.com stable/main Translation-en_US
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Ign http://dl.google.com stable/main Translation-en
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Fetched 1,133 kB in 8s (140 kB/s)                                              
Reading package lists... Done
scott@scott-P5QC:~$ sudo apt-cache show ffmpeg-real
N: Unable to locate package ffmpeg-real
E: No packages found
scott@scott-P5QC:~$ 

```

---

### Post by monkeybrain20122 on 2014-02-21
Yeah you're right. It doesn't have ffmpeg package for 12.04 (things like this is the main reason I don't use LTS for more than a 1.5 year:))  I suppose you can always use fakeoutdoorsman's guide to compile ffmpeg yourself.

---

### Post by sdowney717 on 2014-02-21
I am going to upgrade to beta 14.04

That will give me a newer file.
I dual boot this PC
When I play wtv files on VLC in win7 , they are smooth.
Played in 12.04, half the frames are dropped.:(
The VLC forum suggested my OS is too old, so will find out.

My vid card is 8400 gs 256mb.
I have wondered about upgrading but it is a software issue, so I wait and see if they can make it work like it should work.

---

### Post by monkeybrain20122 on 2014-02-21
> **sdowney717 said:**
> I am going to upgrade to beta 14.04

That will give me a newer file.
I dual boot this PC
When I play wtv files on VLC in win7 , they are smooth.
Played in 12.04, half the frames are dropped.:(
The VLC forum suggested my OS is too old, so will find out.

My vid card is 8400 gs 256mb.
I have wondered about upgrading but it is a software issue, so I wait and see if they can make it work like it should work.

You have a Nvidia card, right? VLC uses vdpau since 2.1.1 but I don't think it is enabled with any Ubuntu build including trusty's and videolan's ppa as it needs libavcodecs >=54 and I don't think even Trusty has that. But the samrog ppa would work in Trusty and you can compile vlc with vdpau support. I did that in Saucy and it definitely works, even though mplayer/mplayer2 is still a lot better.

---

### Post by sdowney717 on 2014-02-21
Can mplayer play wtv files?

WMC creates recorded tv files with extension wtv. AFAIK, only VLC can play them.

Trusty has version 54

my thread over there
[https://forum.videolan.org/viewtopic.php?f=13&t=117635](https://forum.videolan.org/viewtopic.php?f=13&t=117635)

---

### Post by SeijiSensei on 2014-02-21
Apparently [mplayer]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2011-October/083467.html") can play wtv files.

My advice is to install SMPlayer from the repositories then go to Options > Preferences > Video and select vdpau as the output driver from the drop-down box.  See how that works for you.

Oh, you'll need to install the proprietary NVIDIA driver if you haven't already.  Use "sudo apt-get nvidia-current" or the "Additional Drivers" application in the program menu.

---

### Post by monkeybrain20122 on 2014-02-21
> **sdowney717 said:**
> Can mplayer play wtv files?

WMC creates recorded tv files with extension wtv. AFAIK, only VLC can play them.

Trusty has version 54

my thread over there
[https://forum.videolan.org/viewtopic.php?f=13&t=117635](https://forum.videolan.org/viewtopic.php?f=13&t=117635)

Hey dude, if you want to upload a clip  to test, make a smaller one. It is ridiculous to have to spend 1hr + to download 8 G just to see if mediaplayer works. Not everyone is as keen on the Olympics as yourself.:)

---

### Post by sdowney717 on 2014-02-21
> **SeijiSensei said:**
> Apparently [mplayer]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2011-October/083467.html") can play wtv files.

My advice is to install SMPlayer from the repositories then go to Options > Preferences > Video and select vdpau as the output driver from the drop-down box.  See how that works for you.

Oh, you'll need to install the proprietary NVIDIA driver if you haven't already.  Use "sudo apt-get nvidia-current" or the "Additional Drivers" application in the program menu.

Hi, thanks for that, smplayer plays them perfectly and smooth. No dropped frames.

I tried vpdau and it does not play, so switched back to xv.
vpdau causes the player to oddly loop for a microsecond then it just quits playing.
I have nvidia driver 331 working.

under video, gl also works well.

---

### Post by monkeybrain20122 on 2014-02-21
Hi, I just did the ridiculous thing and downloaded your 8 G video and tested it on mplayer, mlayer2 and vlc, all play smoothly. My Nvidia machine has a broken screen and is now sitting in the repair store. This is a borrowed refurb Dell latitude E5510 which costs $300 CND if purchased. Intel(R) Core(TM) i5 CPU M 460 @ 2.53GHz, 4 G of ram and video driver is the infamous i915. Not bad but hardly top of the line. :) Ubuntu 13.10 booting out of an external hard drive.

Edited: Only totem threw an error message and quitted (could not determine mime type of stream)

---

### Post by mc4man on 2014-02-21
> **monkeybrain20122 said:**
> Hi, I just did the ridiculous thing and downloaded your 8 G video and tested it on mplayer, mlayer2 and vlc, all play smoothly. My Nvidia machine has a broken screen and is now sitting in the repair store. This is a borrowed refurb Dell latitude E5510 which costs $300 CND if purchased. Intel(R) Core(TM) i5 CPU M 460 @ 2.53GHz, 4 G of ram and video driver is the infamous i915. Hardly top of the line. :) Ubuntu 13.10 booting out of an external hard drive.
Same here (missed that event so thanks,) then tried on my old 8400m laptop. The vid is mpeg2 & despite large size isn't that demanding so played back fine in both mplayer (not repo version) & vlc repo version (2.0.8 I believe), only used about 34% cpu on core2duo

Probably not advantage to vdpau for mpeg2 on an 8400, though you need to specify -vc as well as -vo for mplayer, noting the 12.04 mplayer repo build is quite old
(-vc ffmpeg12vdpau

---

### Post by sdowney717 on 2014-02-22
My PC where VLC is dropping frames is an ASUS p5qc with a 6600 core2duo cpu, 8gb ddr2 1066, and a pcie 8400gs nvidia.

Maybe there is hope upgrading the OS would make vlc work.
Happy that mplayer is so good on this.

I am also pleased that huge upload worked. I took me maybe an hour to upload.
Biggest file I ever uploaded to google drive.

---

### Post by mc4man on 2014-02-22
while 14.04 should be superior to 12.04 in all areas you should be abe to play that vid fine in 12.04 on that hardware.
If inclined try setting vlc back to it's default config

```
vlc --reset-config
```

---

### Post by sdowney717 on 2014-02-22
> **mc4man said:**
> while 14.04 should be superior to 12.04 in all areas you should be abe to play that vid fine in 12.04 on that hardware.
If inclined try setting vlc back to it's default config

```
vlc --reset-config
```

You fixed it!
Working smooth again.
I have upgraded to 14.04, that did not fix vlc, so I just tried your idea.

Wonder what setting was so wrong.

---

### Post by mc4man on 2014-02-22
> **sdowney717 said:**
> You fixed it!
Working smooth again.
I have upgraded to 14.04, that did not fix vlc, so I just tried your idea.

Wonder what setting was so wrong.
It may have been set to a poor (for your hardware),  video out (vout) setting. for your hardware just leave on vlc's default which for your hw will  I believe will be xv 
(vlc-2.1.2 will auto pick best vout, to see either run from terminal with a -vv option or start a vid in vlc then go - 
Tools > Messages> Modules tree

---

