---
title: "Updating claim I have No internet when I'm connected to the internet"
date: 2013-01-05
forum: Networking &amp; Wireless
---

### Post by Hyper Tails on 2013-01-05
Hey Guys, I have Windows 8 Pro and Ubuntu 12.10 installed on the same computer.

I have a wireless connection (using a D-link DWA-160), I want to update my system, download games, etc on Ubuntu as well. However, I constantly keep getting messages saying to check if I'm connected to the internet, which I am, and some apps don't fully download cause of the same reason.  also Youtube videos are nearly impossible to watch on Ubuntu. It works perfectly fine in Windows 8 and reasonably fast for the most part. I need help for my Ubuntu part of my computer.

Any help will be thanked.

---

### Post by ibjsb4 on 2013-01-05
```
sudo apt-get update
```

Get any errors?

---

### Post by Hyper Tails on 2013-01-06
```
liam@liam-Z68P-DS3:~$ sudo apt-get update
[sudo] password for liam: 
Ign http://ubuntu.mirrors.pair.com quantal InRelease
Ign http://dl.google.com stable InRelease                                      
Ign http://ppa.launchpad.net quantal InRelease                                 
Ign http://extras.ubuntu.com quantal InRelease                                 
Ign http://ubuntu.mirrors.pair.com quantal-updates InRelease                   
Hit http://repo.steampowered.com precise InRelease                             
Hit http://dl.google.com stable Release.gpg                                    
Get:1 http://packages.medibuntu.org quantal InRelease [7,099 B]                
Ign http://download.skype.com stable InRelease                                 
Hit http://dl.google.com stable Release                                        
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://extras.ubuntu.com quantal Release.gpg                               
Ign http://ubuntu.mirrors.pair.com quantal-backports InRelease                 
Ign http://packages.medibuntu.org quantal InRelease                            
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Ign http://ubuntu.mirrors.pair.com quantal-security InRelease                  
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://extras.ubuntu.com quantal Release                                   
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://ubuntu.mirrors.pair.com quantal Release.gpg                         
Ign http://download.skype.com stable Release.gpg                               
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://ubuntu.mirrors.pair.com quantal-updates Release.gpg                 
Hit http://extras.ubuntu.com quantal/main Sources                              
Hit http://ubuntu.mirrors.pair.com quantal-backports Release.gpg               
Ign http://packages.medibuntu.org quantal/free amd64 Packages/DiffIndex        
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://extras.ubuntu.com quantal/main amd64 Packages                       
Hit http://ubuntu.mirrors.pair.com quantal-security Release.gpg                
Hit http://ubuntu.mirrors.pair.com quantal Release                             
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://extras.ubuntu.com quantal/main i386 Packages                        
Hit http://ubuntu.mirrors.pair.com quantal-updates Release                     
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://ubuntu.mirrors.pair.com quantal-backports Release                   
Ign http://packages.medibuntu.org quantal/non-free amd64 Packages/DiffIndex    
Ign http://download.skype.com stable Release                                   
Hit http://ppa.launchpad.net quantal Release.gpg                               
Ign http://dl.google.com stable/main Translation-en_CA                         
Hit http://ppa.launchpad.net quantal Release.gpg                               
Ign http://dl.google.com stable/main Translation-en                            
Ign http://packages.medibuntu.org quantal/free i386 Packages/DiffIndex         
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://ppa.launchpad.net quantal Release.gpg                               
Ign http://packages.medibuntu.org quantal/non-free i386 Packages/DiffIndex     
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://ppa.launchpad.net quantal Release.gpg                               
Ign http://download.skype.com stable/non-free i386 Packages/DiffIndex          
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://ppa.launchpad.net quantal Release                                   
Ign http://extras.ubuntu.com quantal/main Translation-en_CA                    
Hit http://ppa.launchpad.net quantal Release                                   
Ign http://extras.ubuntu.com quantal/main Translation-en                       
Hit http://ppa.launchpad.net quantal Release                                   
Ign http://repo.steampowered.com precise/steam Translation-en_CA               
Hit http://ppa.launchpad.net quantal Release                                   
Ign http://repo.steampowered.com precise/steam Translation-en                  
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://download.skype.com stable/non-free i386 Packages                    
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://packages.medibuntu.org quantal/free amd64 Packages        
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Hit http://packages.medibuntu.org quantal/non-free amd64 Packages              
Hit http://ubuntu.mirrors.pair.com quantal-security Release                    
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://packages.medibuntu.org quantal/free i386 Packages         
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Hit http://packages.medibuntu.org quantal/non-free i386 Packages               
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Err http://download.skype.com stable/non-free amd64 Packages                   
  404  Not Found [IP: 81.52.130.153 80]
Hit http://ubuntu.mirrors.pair.com quantal/restricted Sources                  
Hit http://ubuntu.mirrors.pair.com quantal/main Sources                        
Hit http://ubuntu.mirrors.pair.com quantal/multiverse Sources                  
Hit http://ubuntu.mirrors.pair.com quantal/universe Sources          
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Ign http://download.skype.com stable/non-free Translation-en_CA                
Hit http://ubuntu.mirrors.pair.com quantal/main amd64 Packages       
Hit http://ppa.launchpad.net quantal/main i386 Packages              
Ign http://download.skype.com stable/non-free Translation-en         
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Ign http://packages.medibuntu.org quantal/free Translation-en_CA               
Hit http://ubuntu.mirrors.pair.com quantal/restricted amd64 Packages           
Hit http://ubuntu.mirrors.pair.com quantal/universe amd64 Packages             
Ign http://packages.medibuntu.org quantal/free Translation-en                  
Hit http://ubuntu.mirrors.pair.com quantal/multiverse amd64 Packages           
Hit http://ubuntu.mirrors.pair.com quantal/main i386 Packages                  
Ign http://packages.medibuntu.org quantal/non-free Translation-en_CA           
Ign http://packages.medibuntu.org quantal/non-free Translation-en              
Hit http://ubuntu.mirrors.pair.com quantal/restricted i386 Packages            
Hit http://ubuntu.mirrors.pair.com quantal/universe i386 Packages              
Hit http://ubuntu.mirrors.pair.com quantal/multiverse i386 Packages            
Hit http://ubuntu.mirrors.pair.com quantal/main Translation-en_CA              
Hit http://ubuntu.mirrors.pair.com quantal/main Translation-en                 
Hit http://ubuntu.mirrors.pair.com quantal/multiverse Translation-en           
Hit http://ubuntu.mirrors.pair.com quantal/restricted Translation-en           
Hit http://ubuntu.mirrors.pair.com quantal/universe Translation-en_CA          
Hit http://ubuntu.mirrors.pair.com quantal/universe Translation-en             
Hit http://ubuntu.mirrors.pair.com quantal-updates/restricted Sources          
Hit http://ubuntu.mirrors.pair.com quantal-updates/main Sources                
Hit http://ubuntu.mirrors.pair.com quantal-updates/multiverse Sources
Hit http://ubuntu.mirrors.pair.com quantal-updates/universe Sources
Ign http://ppa.launchpad.net quantal/main Translation-en_CA
Hit http://ubuntu.mirrors.pair.com quantal-updates/main amd64 Packages
Ign http://ppa.launchpad.net quantal/main Translation-en
Hit http://ubuntu.mirrors.pair.com quantal-updates/restricted amd64 Packages
Ign http://ppa.launchpad.net quantal/main Translation-en_CA
Hit http://ubuntu.mirrors.pair.com quantal-updates/universe amd64 Packages
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_CA
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_CA
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_CA
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_CA
Ign http://ppa.launchpad.net quantal/main Translation-en
Hit http://ubuntu.mirrors.pair.com quantal-updates/multiverse amd64 Packages
Ign http://ppa.launchpad.net quantal/main Translation-en_CA
Hit http://ubuntu.mirrors.pair.com quantal-updates/main i386 Packages
Ign http://ppa.launchpad.net quantal/main Translation-en
Hit http://ubuntu.mirrors.pair.com quantal-updates/restricted i386 Packages
Hit http://ubuntu.mirrors.pair.com quantal-updates/universe i386 Packages
Hit http://ubuntu.mirrors.pair.com quantal-updates/multiverse i386 Packages
Hit http://ubuntu.mirrors.pair.com quantal-updates/main Translation-en
Hit http://ubuntu.mirrors.pair.com quantal-updates/multiverse Translation-en
Hit http://ubuntu.mirrors.pair.com quantal-updates/restricted Translation-en
Hit http://ubuntu.mirrors.pair.com quantal-updates/universe Translation-en
Hit http://ubuntu.mirrors.pair.com quantal-backports/main Sources
Hit http://ubuntu.mirrors.pair.com quantal-backports/restricted Sources
Hit http://ubuntu.mirrors.pair.com quantal-backports/universe Sources
Hit http://ubuntu.mirrors.pair.com quantal-backports/multiverse Sources
Hit http://ubuntu.mirrors.pair.com quantal-backports/main amd64 Packages
Hit http://ubuntu.mirrors.pair.com quantal-backports/restricted amd64 Packages
Hit http://ubuntu.mirrors.pair.com quantal-backports/universe amd64 Packages
Hit http://ubuntu.mirrors.pair.com quantal-backports/multiverse amd64 Packages
Hit http://ubuntu.mirrors.pair.com quantal-backports/main i386 Packages
Hit http://ubuntu.mirrors.pair.com quantal-backports/restricted i386 Packages
Hit http://ubuntu.mirrors.pair.com quantal-backports/universe i386 Packages
Hit http://ubuntu.mirrors.pair.com quantal-backports/multiverse i386 Packages
Hit http://ubuntu.mirrors.pair.com quantal-backports/main Translation-en
Hit http://ubuntu.mirrors.pair.com quantal-backports/multiverse Translation-en
Hit http://ubuntu.mirrors.pair.com quantal-backports/restricted Translation-en
Hit http://ubuntu.mirrors.pair.com quantal-backports/universe Translation-en
Hit http://ubuntu.mirrors.pair.com quantal-security/restricted Sources
Hit http://ubuntu.mirrors.pair.com quantal-security/main Sources
Hit http://ubuntu.mirrors.pair.com quantal-security/multiverse Sources
Hit http://ubuntu.mirrors.pair.com quantal-security/universe Sources
Hit http://ubuntu.mirrors.pair.com quantal-security/main amd64 Packages
Hit http://ubuntu.mirrors.pair.com quantal-security/restricted amd64 Packages
Hit http://ubuntu.mirrors.pair.com quantal-security/universe amd64 Packages
Hit http://ubuntu.mirrors.pair.com quantal-security/multiverse amd64 Packages
Hit http://ubuntu.mirrors.pair.com quantal-security/main i386 Packages
Hit http://ubuntu.mirrors.pair.com quantal-security/restricted i386 Packages
Hit http://ubuntu.mirrors.pair.com quantal-security/universe i386 Packages
Hit http://ubuntu.mirrors.pair.com quantal-security/multiverse i386 Packages
Hit http://ubuntu.mirrors.pair.com quantal-security/main Translation-en
Hit http://ubuntu.mirrors.pair.com quantal-security/multiverse Translation-en
Hit http://ubuntu.mirrors.pair.com quantal-security/restricted Translation-en
Hit http://ubuntu.mirrors.pair.com quantal-security/universe Translation-en
Ign http://ubuntu.mirrors.pair.com quantal/multiverse Translation-en_CA
Ign http://ubuntu.mirrors.pair.com quantal/restricted Translation-en_CA
Ign http://ubuntu.mirrors.pair.com quantal-updates/main Translation-en_CA
Ign http://ubuntu.mirrors.pair.com quantal-updates/multiverse Translation-en_CA
Ign http://ubuntu.mirrors.pair.com quantal-updates/restricted Translation-en_CA
Ign http://ubuntu.mirrors.pair.com quantal-updates/universe Translation-en_CA
Ign http://ubuntu.mirrors.pair.com quantal-backports/main Translation-en_CA
Ign http://ubuntu.mirrors.pair.com quantal-backports/multiverse Translation-en_CA
Ign http://ubuntu.mirrors.pair.com quantal-backports/restricted Translation-en_CA
Ign http://ubuntu.mirrors.pair.com quantal-backports/universe Translation-en_CA
Ign http://ubuntu.mirrors.pair.com quantal-security/main Translation-en_CA
Ign http://ubuntu.mirrors.pair.com quantal-security/multiverse Translation-en_CA
Ign http://ubuntu.mirrors.pair.com quantal-security/restricted Translation-en_CA
Ign http://ubuntu.mirrors.pair.com quantal-security/universe Translation-en_CA
Fetched 7,099 B in 25s (274 B/s)
W: GPG error: http://packages.medibuntu.org quantal InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages  404  Not Found [IP: 81.52.130.153 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Here is my output.

---

### Post by ibjsb4 on 2013-01-06
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783 

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+NO_PUBKEY&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+NO_PUBKEY&as_qdr=all&sa=Google+Search&lang=en)

W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages)  404  Not Found [IP: 81.52.130.153 80]

This url is either down or no longer in service

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

