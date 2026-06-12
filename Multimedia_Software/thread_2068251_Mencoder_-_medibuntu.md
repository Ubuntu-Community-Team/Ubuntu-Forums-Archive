---
title: "Mencoder - medibuntu"
date: 2012-10-08
forum: Multimedia Software
---

### Post by jmore9 on 2012-10-08
Hello 

Anyone got any ideas on how i can get mencoder to install on 12.10 ?

Software center says it is broken - Gdebi says it needs libavcodec that is older than the one already installed.

What would forceing it to install from command line to system stabiliation ?

Thanks in advance for any help.

---

### Post by oldos2er on 2012-10-08
Can you post the output from ```
sudo apt-get update && sudo apt-get install mencoder
``` ?

---

### Post by jmore9 on 2012-10-08
sudo apt-get install mencoder
[sudo] password for jeffm: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 mencoder : Depends: libx264-120 but it is not installable
E: Unable to correct problems, you have held broken packages.

Version installed is libx264-123 , it is complaining about not heving versionlibx264-120 .

---

### Post by jmore9 on 2012-10-08
Software Center gives the following errors trying to install:

The following packages have unmet dependencies:

mencoder: Depends: libavcodec-extra-53 (>= 4:0.8-1~) but 6:0.8.3.6ubuntu1+medibuntu1 is to be installed
          Depends: libavformat-extra-53 (>= 4:0.8-1~) but 6:0.8.3.6ubuntu1+medibuntu1 is to be installed
          Depends: libavutil-extra-51 (>= 4:0.8-1~) but 6:0.8.3.6ubuntu1+medibuntu1 is to be installed
          Depends: libpostproc-extra-52 (>= 4:0.8-1~) but 6:0.8.3.6ubuntu1+medibuntu1 is to be installed
          Depends: libswscale-extra-2 (>= 4:0.8-1~) but 6:0.8.3.6ubuntu1+medibuntu1 is to be installed
          Depends: libx264-120 but it is not going to be installed

---

### Post by oldos2er on 2012-10-09
Did you run 'sudo apt-get update' first? Can you post the output?

---

### Post by jmore9 on 2012-10-09
sudo apt-get update
[sudo] password for jeffm: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports InRelease                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease                      
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal InRelease                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease                                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal InRelease                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-proposed InRelease                    
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release.gpg [933 B]                 
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release.gpg                   
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg [72 B]                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release.gpg                 
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release                        
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-proposed Release.gpg [933 B]        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                   
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release [49.6 kB]                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal/free Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages                        
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-proposed Release [49.6 kB]          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources               
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Sources [872 kB]               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en            
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en_US             
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Sources [5,642 B]        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US                    
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en                
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Sources [5,539 kB]         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal/non-free Sources 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal/free i386 Packages                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal/non-free i386 Packages 
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Sources [166 kB]         
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main i386 Packages [1,143 kB]      
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted i386 Packages [8,334 B] 
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe i386 Packages [5,321 kB] 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal/free Translation-en_US               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal/free Translation-en  
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse i386 Packages [132 kB]  
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en [661 kB]       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal/non-free Translation-en_US           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal/non-free Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en             
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en [3,662 kB] 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en     
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-proposed/restricted i386 Packages [14 B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-proposed/main i386 Packages [37.8 kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-proposed/multiverse i386 Packages [14 B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-proposed/universe i386 Packages [4,708 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-proposed/main Translation-en [13.7 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-proposed/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-proposed/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-proposed/universe Translation-en      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en_US                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-proposed/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-proposed/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-proposed/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-proposed/universe Translation-en_US   
Fetched 17.7 MB in 29s (590 kB/s)                                              
Reading package lists... Done

---

### Post by oldos2er on 2012-10-09
Odd. I don't have the medibuntu repository enabled, and mencoder installed fine, so I suspect your problem is the lib files in medibuntu conflicting with the ones in the default repositories.

---

### Post by budgie9 on 2012-10-11
I too am getting the same message 

The following packages have unmet dependencies:
  mencoder: Depends: mplayer but it is not going to be installed
E: Broken packages
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

I need to re-install Devede which was working but since the latest upgrade no longer works. Apt removed Mplayer, Mencoder and devede.

---

