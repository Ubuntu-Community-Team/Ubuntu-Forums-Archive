---
title: "vlc problems"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by rab4567 on 2007-06-05
I'm trying to get vlc working so I tryed sudo apt-get and got 13premission denied. What do i do now I'm still new to all this.
example
rab@ubuntu:~$ sudo apt-get update
Password:
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Get:1 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg [189B]                   
Get:2 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US      
Get:3 [http://ftp.debian.org](http://ftp.debian.org) sarge Release.gpg [378B]                           
Ign [http://ftp.debian.org](http://ftp.debian.org) sarge/main Translation-en_US                         
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US      
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_US                 
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_US             
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
Hit [http://ftp.debian.org](http://ftp.debian.org) sarge Release                                        
Err [http://ftp.debian.org](http://ftp.debian.org) sarge Release                                        
  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US        
Get:5 [http://ftp.debian.org](http://ftp.debian.org) sarge Release [34.6kB]                             
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release                                
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release                                
  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty Release.gpg                              
Get:6 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release [7232B]                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages               
Get:7 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/main Translation-en_US                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                     
Ign [http://ftp.debian.org](http://ftp.debian.org) sarge Release                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages                 
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release                                
Ign [http://ftp.debian.org](http://ftp.debian.org) sarge/main Packages                          
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/main Translation-en_US
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages
Hit [http://ftp.debian.org](http://ftp.debian.org) sarge/main Packages  
Get:8 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/restricted Translation-en_US
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/restricted Translation-en_US
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources
Get:9 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/universe Translation-en_US
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/universe Translation-en_US
Get:10 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/multiverse Translation-en_US
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/multiverse Translation-en_US
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates Release.gpg
Get:11 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates/main Translation-en_US
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates/main Translation-en_US
Get:12 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates/restricted Translation-en_US
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates/restricted Translation-en_US
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security Release.gpg
Get:13 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/main Translation-en_US
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/main Translation-en_US
Get:14 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/restricted Translation-en_US
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/restricted Translation-en_US
Get:15 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/universe Translation-en_US
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/universe Translation-en_US
Get:16 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/multiverse Translation-en_US
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/multiverse Translation-en_US
Get:17 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty Release [57.2kB]
Get:18 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates Release [32.4kB]
Get:19 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security Release [50.9kB]             
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/restricted Sources                       
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/main Sources                             
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/main Packages                            
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/restricted Packages                      
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/multiverse Sources                       
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/universe Sources                         
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/universe Packages                        
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/multiverse Packages                      
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates/main Packages                    
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates/restricted Packages              
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates/main Sources                     
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates/restricted Sources               
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/main Packages                   
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/restricted Packages             
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/restricted Sources              
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/main Sources                    
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/multiverse Sources              
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/universe Sources                
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/universe Packages               
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/multiverse Packages             
Fetched 183kB in 9s (18.3kB/s)                                                 
Reading package lists... Done
W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
rab@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
rab@ubuntu:~$

---

### Post by NeoLithium on 2007-06-05
Well, I'm not sure about the debian key, so you might just want to search around for that or comment it out in your sources.list, but to add the Medibuntu Pubkey, open up a terminal window and type:
```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

```

Then just sudo, apt-get update.

---

### Post by rab4567 on 2007-06-05
Ok tried that thi is what i got


rab@ubuntu:~$ sudo apt-get update
Password:
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Get:1 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg [189B]                   
Get:2 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US      
Get:3 [http://ftp.debian.org](http://ftp.debian.org) sarge Release.gpg [378B]                           
Ign [http://ftp.debian.org](http://ftp.debian.org) sarge/main Translation-en_US                         
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US      
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_US                 
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_US             
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
Hit [http://ftp.debian.org](http://ftp.debian.org) sarge Release                                        
Err [http://ftp.debian.org](http://ftp.debian.org) sarge Release                                        
  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US        
Get:5 [http://ftp.debian.org](http://ftp.debian.org) sarge Release [34.6kB]                             
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release                                
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release                                
  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty Release.gpg                              
Get:6 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release [7232B]                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages               
Get:7 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/main Translation-en_US                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                     
Ign [http://ftp.debian.org](http://ftp.debian.org) sarge Release                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages                 
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release                                
Ign [http://ftp.debian.org](http://ftp.debian.org) sarge/main Packages                          
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/main Translation-en_US
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages
Hit [http://ftp.debian.org](http://ftp.debian.org) sarge/main Packages  
Get:8 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/restricted Translation-en_US
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/restricted Translation-en_US
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources
Get:9 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/universe Translation-en_US
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/universe Translation-en_US
Get:10 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/multiverse Translation-en_US
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/multiverse Translation-en_US
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates Release.gpg
Get:11 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates/main Translation-en_US
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates/main Translation-en_US
Get:12 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates/restricted Translation-en_US
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates/restricted Translation-en_US
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security Release.gpg
Get:13 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/main Translation-en_US
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/main Translation-en_US
Get:14 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/restricted Translation-en_US
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/restricted Translation-en_US
Get:15 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/universe Translation-en_US
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/universe Translation-en_US
Get:16 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/multiverse Translation-en_US
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/multiverse Translation-en_US
Get:17 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty Release [57.2kB]
Get:18 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates Release [32.4kB]
Get:19 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security Release [50.9kB]             
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/restricted Sources                       
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/main Sources                             
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/main Packages                            
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/restricted Packages                      
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/multiverse Sources                       
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/universe Sources                         
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/universe Packages                        
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/multiverse Packages                      
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates/main Packages                    
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates/restricted Packages              
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates/main Sources                     
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates/restricted Sources               
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/main Packages                   
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/restricted Packages             
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/restricted Sources              
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/main Sources                    
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/multiverse Sources              
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/universe Sources                
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/universe Packages               
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/multiverse Packages             
Fetched 183kB in 9s (18.3kB/s)                                                 
Reading package lists... Done
W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
rab@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
rab@ubuntu:~$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -
Password:
OK
rab@ubuntu:~$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -
OK
rab@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Get:1 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg [189B]                   
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US      
Get:3 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US      
Get:4 [http://ftp.debian.org](http://ftp.debian.org) sarge Release.gpg [378B]                           
Ign [http://ftp.debian.org](http://ftp.debian.org) sarge/main Translation-en_US                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US        
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty Release.gpg                              
Hit [http://ftp.debian.org](http://ftp.debian.org) sarge Release                                        
Err [http://ftp.debian.org](http://ftp.debian.org) sarge Release                                        
  
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages             
Get:5 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/main Translation-en_US               
Get:6 [http://ftp.debian.org](http://ftp.debian.org) sarge Release [34.6kB]                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages                 
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/main Translation-en_US                   
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_US                 
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_US
Get:7 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/restricted Translation-en_US
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release                                
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/restricted Translation-en_US             
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages        
Get:8 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/universe Translation-en_US
Ign [http://ftp.debian.org](http://ftp.debian.org) sarge Release                                        
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages               
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/universe Translation-en_US       
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources                   
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources
Ign [http://ftp.debian.org](http://ftp.debian.org) sarge/main Packages  
Get:9 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/multiverse Translation-en_US
Hit [http://ftp.debian.org](http://ftp.debian.org) sarge/main Packages    
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/multiverse Translation-en_US
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates Release.gpg
Get:10 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates/main Translation-en_US
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates/main Translation-en_US
Get:11 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates/restricted Translation-en_US
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates/restricted Translation-en_US
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security Release.gpg
Get:12 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/main Translation-en_US
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/main Translation-en_US
Get:13 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/restricted Translation-en_US
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/restricted Translation-en_US
Get:14 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/universe Translation-en_US
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/universe Translation-en_US
Get:15 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/multiverse Translation-en_US
Ign [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/multiverse Translation-en_US
Get:16 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty Release [57.2kB]
Get:17 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates Release [32.4kB]
Get:18 [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security Release [50.9kB]             
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/restricted Sources                       
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/main Sources                             
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/main Packages                            
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/restricted Packages                      
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/multiverse Sources                       
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/universe Sources                         
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/universe Packages                        
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty/multiverse Packages                      
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates/main Packages                    
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates/restricted Packages              
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates/main Sources                     
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-updates/restricted Sources               
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/main Packages                   
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/restricted Packages             
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/restricted Sources              
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/main Sources                    
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/multiverse Sources              
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/universe Sources                
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/universe Packages               
Hit [ftp://carroll.aset.psu.edu](ftp://carroll.aset.psu.edu) feisty-security/multiverse Packages             
Fetched 176kB in 9s (17.9kB/s)                                                 
Reading package lists... Done
W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: You may want to run apt-get update to correct these problems

---

### Post by tech9 on 2007-12-13
> **rab4567 said:**
> 
Reading package lists... Done
W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: You may want to run **apt-get update** to correct these problems

you may want to try what it suggests

sudo apt-get update

then 

sudo apt-get install vlc

---

### Post by rsambuca on 2007-12-13
Your repository sources list is really messed up.  If you keep it like it is, your system will become very unstable.  Open a terminal and post the output of:

```
cat /etc/apt/sources.list
```

---

