---
title: "HTPC for local files !!!"
date: 2011-07-02
forum: Multimedia Software
---

### Post by linuxyogi on 2011-07-02
Hi,

I use this PC mainly to watch music videos & movies. All these are locally stored. I rarely 

stream coz my network speed is not that great. I was wondering, how about installing a 

HTPC app for the purpose ? I know it doesnt really make sense unless the PC has a TV Tuner 

but I feel like having a good looking interface to browse through. vdpau is a must coz 90% 

of my videos are HD . I tried  installing XBMC but they don't have a ppa for Natty.  


Please suggest one for me.

---

### Post by toliman on 2011-07-12
it's not part of the standard multiverse/universe package, but the team-xbmc build works OK if you follow the regular install steps

```

sudo apt-get install python-software-properties pkg-config
sudo add-apt-repository ppa:team-xbmc
sudo apt-get update
sudo apt-get install xbmc xbmc-standalone
sudo apt-get update

```

there are 4 kinds of XBMC builds, stable, unstable, user-patched and SVN. if you want to use anything more advanced, use the XBMC forums to find out more details. 

if you're using a regular install of ubuntu, you will need to install updated video drivers or it will run at about 4 fps just in the menus. if you're already able to play videos smoothly using xine, totem, VLC or ffmpeg, etc. it shouldn't be a concern. 

once you're installed, you can add in updated skins and plugins at a later time, also via the forums, some of the built-in plugins are a bit shabby, but they can work really well with the more advanced features of XBMC once you figure them all out. 

if you want to create an auto-boot straight into XBMC, you can add 

```

# xbmc-standalone
description "Autostart XBMC"

start on (filesystem and stopped udevtrigger)
stop on runlevel [06]

task
console output
emits starting-x

script
su xbmc -c "startx /etc/X11/Xsession /usr/bin/xbmc-standalone"
end script

```

to the file, /etc/init/xbmc.conf , if all the machine will do is play video and music files.

---

### Post by linuxyogi on 2011-07-12
@ toliman

Added the XBMC PPA

```
$ sudo add-apt-repository ppa:team-xbmc
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 189701DA570C56B9488EF60A6D975C4791E7EE5E
gpg: requesting key 91E7EE5E from hkp server keyserver.ubuntu.com
gpg: key 91E7EE5E: "Launchpad PPA for XBMC for Linux" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```Then did 

```
$ sudo apt-get update
Hit http://packages.medibuntu.org natty InRelease                             
Ign http://download.virtualbox.org natty InRelease                            
Ign http://linux.dropbox.com natty InRelease                                  
Ign http://extras.ubuntu.com natty InRelease                                  
Ign http://ppa.launchpad.net natty InRelease                                  
Ign http://ppa.launchpad.net natty InRelease                                  
Ign http://ppa.launchpad.net natty InRelease                                  
Hit http://download.virtualbox.org natty Release.gpg                          
Hit http://linux.dropbox.com natty Release.gpg                                
Hit http://packages.medibuntu.org natty/free i386 Packages                    
Get:1 http://extras.ubuntu.com natty Release.gpg [72 B]                       
Hit http://download.virtualbox.org natty Release                              
Hit http://download.virtualbox.org natty/contrib i386 Packages                
Hit http://linux.dropbox.com natty Release                                    
Hit http://extras.ubuntu.com natty Release                                    
Hit http://packages.medibuntu.org natty/non-free i386 Packages                
Ign http://download.virtualbox.org natty/contrib TranslationIndex             
Ign http://dl.google.com stable InRelease                                     
Hit http://linux.dropbox.com natty/main i386 Packages                         
Hit http://extras.ubuntu.com natty/main Sources                               
Ign http://packages.medibuntu.org natty/free TranslationIndex                 
Ign http://linux.dropbox.com natty/main TranslationIndex                      
Hit http://extras.ubuntu.com natty/main i386 Packages                         
Ign http://extras.ubuntu.com natty/main TranslationIndex                      
Ign http://packages.medibuntu.org natty/non-free TranslationIndex             
Get:2 http://dl.google.com stable Release.gpg [198 B]                         
Ign http://download.virtualbox.org natty/contrib Translation-en_US            
Ign http://download.virtualbox.org natty/contrib Translation-en               
Ign http://ppa.launchpad.net natty InRelease                                  
Hit http://ppa.launchpad.net natty Release.gpg                                
Hit http://ppa.launchpad.net natty Release.gpg                                
Ign http://ppa.launchpad.net natty Release.gpg                                
Hit http://ppa.launchpad.net natty Release.gpg                                
Ign http://archive.ubuntu.com natty InRelease                                 
Ign http://archive.ubuntu.com natty-updates InRelease                         
Ign http://archive.ubuntu.com natty-security InRelease                        
Hit http://ppa.launchpad.net natty Release                                    
Hit http://ppa.launchpad.net natty Release                                    
Hit http://archive.ubuntu.com natty Release.gpg                               
Get:3 http://dl.google.com stable Release [1,347 B]                           
Ign http://linux.dropbox.com natty/main Translation-en_US                     
Ign http://extras.ubuntu.com natty/main Translation-en_US                     
Ign http://ppa.launchpad.net natty Release                                    
Hit http://archive.ubuntu.com natty-updates Release.gpg                       
Ign http://linux.dropbox.com natty/main Translation-en                        
Ign http://extras.ubuntu.com natty/main Translation-en                        
Hit http://ppa.launchpad.net natty Release                                    
Hit http://ppa.launchpad.net natty/main Sources                               
Hit http://ppa.launchpad.net natty/main i386 Packages                         
Hit http://archive.ubuntu.com natty-security Release.gpg                      
Ign http://ppa.launchpad.net natty/main TranslationIndex                      
Hit http://ppa.launchpad.net natty/main Sources                               
Hit http://ppa.launchpad.net natty/main i386 Packages                         
Ign http://ppa.launchpad.net natty/main TranslationIndex                      
Hit http://archive.ubuntu.com natty Release                                   
Ign http://ppa.launchpad.net natty/main TranslationIndex                      
Hit http://ppa.launchpad.net natty/main Sources                      
Hit http://ppa.launchpad.net natty/main i386 Packages                
Ign http://ppa.launchpad.net natty/main TranslationIndex             
Hit http://archive.ubuntu.com natty-updates Release                           
Get:4 http://dl.google.com stable/main i386 Packages [767 B]                  
Hit http://archive.ubuntu.com natty-security Release                          
Hit http://archive.ubuntu.com natty/main Sources                              
Hit http://archive.ubuntu.com natty/restricted Sources                        
Hit http://archive.ubuntu.com natty/universe Sources                          
Hit http://archive.ubuntu.com natty/multiverse Sources                        
Hit http://archive.ubuntu.com natty/main i386 Packages                        
Hit http://archive.ubuntu.com natty/restricted i386 Packages                  
Hit http://archive.ubuntu.com natty/universe i386 Packages                    
Hit http://archive.ubuntu.com natty/multiverse i386 Packages                  
Ign http://archive.ubuntu.com natty/main TranslationIndex                     
Ign http://dl.google.com stable/main TranslationIndex                         
Ign http://archive.ubuntu.com natty/multiverse TranslationIndex               
Ign http://archive.ubuntu.com natty/restricted TranslationIndex               
Ign http://archive.ubuntu.com natty/universe TranslationIndex                 
Hit http://archive.ubuntu.com natty-updates/main Sources                      
Hit http://archive.ubuntu.com natty-updates/restricted Sources                
Hit http://archive.ubuntu.com natty-updates/universe Sources                  
Hit http://archive.ubuntu.com natty-updates/multiverse Sources                
Hit http://archive.ubuntu.com natty-updates/main i386 Packages                
Hit http://archive.ubuntu.com natty-updates/restricted i386 Packages 
Hit http://archive.ubuntu.com natty-updates/universe i386 Packages            
Hit http://archive.ubuntu.com natty-updates/multiverse i386 Packages          
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex    
Ign http://archive.ubuntu.com natty-updates/multiverse TranslationIndex       
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex       
Ign http://archive.ubuntu.com natty-updates/universe TranslationIndex
Hit http://archive.ubuntu.com natty-security/main Sources            
Hit http://archive.ubuntu.com natty-security/restricted Sources               
Hit http://archive.ubuntu.com natty-security/universe Sources                 
Hit http://archive.ubuntu.com natty-security/multiverse Sources               
Hit http://archive.ubuntu.com natty-security/main i386 Packages               
Hit http://archive.ubuntu.com natty-security/restricted i386 Packages         
Hit http://archive.ubuntu.com natty-security/universe i386 Packages           
Hit http://archive.ubuntu.com natty-security/multiverse i386 Packages         
Ign http://archive.ubuntu.com natty-security/main TranslationIndex            
Ign http://archive.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://archive.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://archive.ubuntu.com natty-security/universe TranslationIndex        
Err http://ppa.launchpad.net natty/main Sources                               
  404  Not Found
Err http://ppa.launchpad.net natty/main i386 Packages                         
  404  Not Found
Ign http://ppa.launchpad.net natty/main Translation-en_US                     
Ign http://ppa.launchpad.net natty/main Translation-en                        
Ign http://ppa.launchpad.net natty/main Translation-en_US            
Ign http://ppa.launchpad.net natty/main Translation-en                        
Ign http://ppa.launchpad.net natty/main Translation-en_US                     
Ign http://ppa.launchpad.net natty/main Translation-en                        
Ign http://packages.medibuntu.org natty/free Translation-en_US                
Ign http://ppa.launchpad.net natty/main Translation-en_US                     
Ign http://ppa.launchpad.net natty/main Translation-en                        
Ign http://packages.medibuntu.org natty/free Translation-en                   
Ign http://packages.medibuntu.org natty/non-free Translation-en_US            
Ign http://packages.medibuntu.org natty/non-free Translation-en               
Ign http://archive.ubuntu.com natty/main Translation-en_US                    
Ign http://archive.ubuntu.com natty/main Translation-en
Ign http://archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty/multiverse Translation-en
Ign http://archive.ubuntu.com natty/restricted Translation-en_US
Ign http://archive.ubuntu.com natty/restricted Translation-en
Ign http://archive.ubuntu.com natty/universe Translation-en_US
Ign http://archive.ubuntu.com natty/universe Translation-en
Ign http://archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://archive.ubuntu.com natty-updates/main Translation-en
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com natty-updates/universe Translation-en
Ign http://archive.ubuntu.com natty-security/main Translation-en_US
Ign http://archive.ubuntu.com natty-security/main Translation-en
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en
Ign http://archive.ubuntu.com natty-security/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-security/restricted Translation-en
Ign http://archive.ubuntu.com natty-security/universe Translation-en_US
Ign http://archive.ubuntu.com natty-security/universe Translation-en
Ign http://dl.google.com stable/main Translation-en_US
Ign http://dl.google.com stable/main Translation-en
Fetched 2,384 B in 46s (51 B/s)
[B]W: Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
[/B]


```They have packages upto Maverick. I guess they dont have packages for Natty.

Actually, in absence of a XBMC PPA for Natty I installed Mythv. But unfortunately MythTV is not too good with video playlists. 

Its really not that important don't bother. 

Thanks.

---

### Post by linuxyogi on 2011-07-12
@toliman

Installed XBMC from the above PPA,  just changed the Distribution (in Synaptic) from Natty to Maverick.
:guitar:

---

