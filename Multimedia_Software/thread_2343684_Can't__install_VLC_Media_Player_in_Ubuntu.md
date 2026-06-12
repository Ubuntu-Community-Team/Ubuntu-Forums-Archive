---
title: "Can't  install VLC Media Player in Ubuntu"
date: 2016-11-18
forum: Multimedia Software
---

### Post by shaolinwarrior on 2016-11-18
Hii In my Ubuntu 14.04 LTS vlc player can't be installed. Actually I'm new to Ubuntu so don't know much about it. 
I tried using Software Center but the following error was encountered.

Error was 

The following packages have unmet dependencies:

vlc: Depends: vlc-nox (= 2.1.6-0ubuntu14.04.2) but 2.1.6-0ubuntu14.04.2 is to be installed
     Depends: libc6 (>= 2.15) but 2.19-0ubuntu6.9 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.5.2-1ubuntu2.5 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.9.3-0ubuntu4 is to be installed
     Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 is to be installed
     Depends: libqtgui4 (>= 4:4.8.0) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 is to be installed
     Depends: libstdc++6 (>= 4.6) but 4.8.4-2ubuntu1~14.04.3 is to be installed
     Depends: zlib1g (>= 1:1.2.3.3) but 1:1.2.8.dfsg-1ubuntu1 is to be installed


I tried to install vlc-nox from software center nut returns anotrher error regarding libc6 library. 
I checked libc6 and found that it was alredy installed. 
  I have no idea . Can anyone help me.?

Thanks.

---

### Post by ajgreeny on 2016-11-18
Have you run sudo apt-get update first?
Do you have any packages from non-standard repositories, eg PPAs, installed that could have introduced dependency problems?

---

### Post by Autodave on 2016-11-19
I much prefer installing programs from synaptic package manager. From your software center, install "synaptic package manager". Then go into synaptic from the "system" entry. Now try to install VLC.

---

### Post by shaolinwarrior on 2016-11-20
> **ajgreeny said:**
> Have you run sudo apt-get update first?
Do you have any packages from non-standard repositories, eg PPAs, installed that could have introduced dependency problems?


Yeah . I have done that and I assume the software is up-to-date.This was the result after performing sudo apt-get update. You just check it and please let me know if anything is wrong.


```
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty InRelease                       
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates InRelease            
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-proposed InRelease                     
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty Release.gpg [933 B]                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/main Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/restricted Sources             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/universe i386 Packages         
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [4,289 B]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/multiverse i386 Packages       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/main Translation-en            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/universe Translation-en      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-proposed/universe i386 Packages        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-proposed/multiverse i386 Packages      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-proposed/restricted i386 Packages      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-proposed/main i386 Packages            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-proposed/main Translation-en           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-proposed/multiverse Translation-en     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-proposed/restricted Translation-en     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-proposed/universe Translation-en       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty Release                                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/main Sources                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/universe Translation-en                
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/universe Translation-en_US             
Fetched 5,222 B in 1min 11s (73 B/s)                                           
Reading package lists... Done
```
Once I tried to install vlc from a deb package.Now I suspect that. It was an official download from Debian site. 

Is there any way to remove such packages all at once because I cant precisely remember which were the packages I installed.

Is there something like System Restore in Windows OSs.?

I also tried sudo apt-get clean    sudo apt-get autoclean  commands. But no way.

By the way the sudo apt-get clean commands returns nothing , it just going to the command line initial position after hitting Enter key.

But sudo apt-get autoclean command shows the progress and notifies about the processes.

---

### Post by shaolinwarrior on 2016-11-20
> **Autodave said:**
> I much prefer installing programs from synaptic package manager. From your software center, install "synaptic package manager". Then go into synaptic from the "system" entry. Now try to install VLC.

Still no way. Got any other ideas.? 

I was already installed Synaptic and was trying to install vlc from that.
Once I was installed the official deb package of vlc from Debian site and it was installed properly . But it was before trying to install vlc from Software Centre and before the installation of Synaptic. I think that made the problems. I don’t precisely remember those packages I have installed. May be those libraries making the trouble. Is there any way to manually uninstall them all at once ?  or something like the System Restore .? 

I don’t know much about this OS.

---

### Post by Yellow Pasque on 2016-11-20
See if there are any vlc packages from your previous attempt:
```
dpkg -l | grep vlc
```

---

